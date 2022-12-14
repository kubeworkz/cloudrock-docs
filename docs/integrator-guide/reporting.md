# Reporting

Examples below show how it's possible to use Cloudrock SDK for generation of custom reports.

## Running the scripts

All of the scripts below should be saved as files and executed in the environment with installed
[Cloudrock SDK](./cloudrock-sdk.md). Please make sure that you have python3 and pip installed in your command line.

Make sure that you update ``CLOUDROCK_HOST`` and ``TOKEN`` with values that match your target Cloudrock deployment.

```bash
pip install https://github.com/kubeworkz/python-cloudrock-client/archive/master.zip
python <reporting-script-name>.py
```

## Project reporting

The first scenario is report generation about monthly costs of each project.
The name of the output file is `project-report.csv`.

Code example:

```python
from cloudrock_client import CloudrockClient, ObjectDoesNotExist
import csv
from collections import defaultdict

# Your Cloudrock instance data
CLOUDROCK_HOST = 'example.cloudrock.ca'
TOKEN = 'STAFF_USER_API_TOKEN'

# Date-related constants
CURRENT_YEAR = 2021
CURRENT_MONTH = 10

# Other constants
CSV_FILE_PATH = 'project-report.csv'
HEADER = [
    'Organization name',
    'Organization abbreviation',
    'Project name',
    'Monthly cost of a project',
]

# CloudrockClient instance initialisation
client = CloudrockClient(
    f'https://{CLOUDROCK_HOST}/api/', TOKEN
)

# Organisations data fetching
customers_data = client.list_customers()

with open(CSV_FILE_PATH, 'w', encoding='UTF8') as out_file:
    writer = csv.writer(out_file)
    writer.writerow(HEADER)

    for customer_data in customers_data:
        project_reporting = defaultdict(lambda: 0.0)

        try:
            # Invoices data fetching
            invoice_data = client.get_invoice_for_customer(
                customer_data['uuid'], CURRENT_YEAR, CURRENT_MONTH
            )
        # If customer doesn't have any projects or created after the requested month
        except ObjectDoesNotExist:
            pass

        invoice_items = [item for item in invoice_data['items']]

        # Cost aggregation per each project
        for item in invoice_items:
            project_reporting[item['project_name']] += float(item['price'])

        for key, val in project_reporting.items():
            writer.writerow(
                [
                    customer_data['name'],
                    customer_data['abbreviation'],
                    key,
                    val,
                ]
            )
```

Example of output file content:

```csv
Organization name,Organization abbreviation,Project name,Monthly cost of a project
Org A,OA,Team1,10
Org B,OB,Demo project,70
Org B,OB,Industrial project,100
Org C,OC,Lab1,110
```

## OpenStack tenant reporting

The second scenario is report generation about quotas and monthly costs of OpenStack tenants.

The name of the output file is `openstack-report.csv`.

Code example:

```python
from cloudrock_client import CloudrockClient, ObjectDoesNotExist
from pprint import pprint
import csv

# Your Cloudrock instance data
CLOUDROCK_HOST = 'example.cloudrock.ca'
TOKEN = 'STAFF_USER_API_TOKEN'

# Date-related constants
CURRENT_YEAR = 2021
CURRENT_MONTH = 10

# CloudrockClient instance initialisation
client = CloudrockClient(
    f'https://{CLOUDROCK_HOST}/api/', TOKEN
)

# Other constants
CSV_FILE_PATH = 'openstack-report.csv'
HEADER = [
    'Name of the OpenStack Tenant resource',
    'vCPU limit',
    'RAM limit',
    'Storage limit',
    'Monthly cost of the resource',
    'Project name',
    'Organization name',
    'Organization abbreviation',
]

# Organisations data fetching
customers_data = client.list_customers()

with open(CSV_FILE_PATH, 'w', encoding='UTF8') as out_file:
    writer = csv.writer(out_file)
    writer.writerow(HEADER)
    for customer_data in customers_data:
        customer_uuid = customer_data['uuid']
        try:
            # Invoices data fetching
            invoice_data = client.get_invoice_for_customer(
                customer_data['uuid'], CURRENT_YEAR, CURRENT_MONTH
            )
        # If customer doesn't have any projects or created after the requested month
        except ObjectDoesNotExist:
            pass

        # Tenants data fetching
        tenants = client.list_tenants({'customer_uuid': customer_uuid})

        resource_costs = {item['resource_uuid']: item['price'] for item in invoice_data['items']}

        for tenant in tenants:
            resource_uuid = tenant['marketplace_resource_uuid']

            # Resource data fetching
            resource = client.get_marketplace_resource(resource_uuid)
            limits = resource['limits']
            try:
                writer.writerow([
                    tenant['name'],
                    limits['cores'],
                    limits['ram'],
                    limits['storage'],
                    resource_costs.get(resource_uuid, 0.0), # if a resource wasn't used during the month
                    tenant['project_name'],
                    tenant['customer_name'],
                    tenant['customer_abbreviation']
                ])
            except KeyError as e:
                pprint(resource_uuid)
                pprint(e)
```

Example of output file content:

```csv
Name of the OpenStack.Tenant resource,vCPU limit,RAM limit,Storage limit,Monthly cost of the resource,Project name,Organization name,Organization abbreviation
HPC_resource,2.0,4096.0,61440.0,2.18,Team1,Org A,OA
OpenStack Cloud for testing,1,1024,102400,5.17,Demo project,Org B,OB
OpenStack Cloud,12,51200,614400,21.77,Industrial project,Org B,OB
Private Cloud,1,1024,102400,5.17,Lab1,Org C,OC
```
