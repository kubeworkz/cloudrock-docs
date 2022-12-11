# Cloudrock SLURM Integration Service

Service for Metal integration with SLURM cluster. The main purpose of the service is data syncronization between Cloudrock instance and SLURM cluster. The application uses order-related information from Cloudrock to manage accounts in SLURM and accounting-related info from SLURM to update usage data in Cloudrock.

## Architecture

This is a stateless application, which should be deployed on a machine having access to SLURM cluster data. The service consists of two sub-applications:

- service-pull, which fetches data from Cloudrock and updates a state of a SLURM cluster correspondingly (e.g. creation of SLURM accounts ordered in Cloudrock)
- service-push, which sends data from SLURM cluster to Cloudrock (e.g. update of resource usages)

### Integration with Cloudrock

For this, the service uses [Cloudrock client](https://github.com/kubeworkz/python-cloudrock-client) based on Python and REST communication with [Cloudrock backend](https://github.com/kubeworkz/cloudrock-metal). Service-pull application pulls orders data created for a specific offering linked to SLURM cluster and creates/updates/removes SLURM accounts based on the data. Service-push fetches data of usage, limits and associations from SLURM cluster and pushes it to Cloudrock.

### Integration with SLURM cluster

For this, service uses uses SLURM command line utilities (e.g. `sacct` and `sacctmgr`). The access to the binaries can be either direct or using docker client. In the latter case, the service is required to have access to `docker` binary and to docker socket (e.g. `/var/run/docker.sock`).

## Setup

The application supports the following environmental variables (required ones formatted with bold font):

- **`CLOUDROCK_API_URL`** - URL of Cloudrock Metal API (e.g. `http://localhost:8081/api/`).
- **`CLOUDROCK_API_TOKEN`** - token for access to Metal API.
- **`CLOUDROCK_SYNC_DIRECTION`** - accepts two values: `push` and `pull`. If `pull`, then application sends data from SLURM cluster to Cloudrock, vice versa if `push`.
- **`CLOUDROCK_OFFERING_UUID`** - UUID of corresponding offering in Cloudrock.
- `REQUESTS_VERIFY_SSL` - flag for SSL verification for Cloudrock client, default is `true`.
- `SLURM_DEPLOYMENT_TYPE` - type of SLURM deployment. accepts two values: `docker` and `native`, default is `docker`.
- `SLURM_CUSTOMER_PREFIX` - prefix used for customer's accounts, default is `hpc_`.
- `SLURM_PROJECT_PREFIX` - prefix used for project's accounts, default is `hpc_`.
- `SLURM_ALLOCATION_PREFIX` - prefix used for allocation's accounts, default is `hpc_`.
- `SLURM_ALLOCATION_NAME_MAX_LEN` - maximum length of account name created by the application.
- `SLURM_DEFAULT_ACCOUNT` - default account name existing in SLURM cluster for creation of new accounts. Default is `cloudrock`.
- `SLURM_CONTAINER_NAME` - name of a headnode SLURM container; must be set if SLURM_DEPLOYMENT_TYPE is docker.
- `CLOUDROCK_SLURM_USERNAME_SOURCE` - source of SLURM username in Cloudrock. It can be either `freeipa` or `local`, default is `local`.

## Deployment

### Test environment

In order to test the service, a user should deploy 2 separate instances of the service.
The first one (called service-pull) is for fetching data from Cloudrock with further processing and the second one (called service-push) is for sending data from SLURM cluster to Cloudrock.
Both instances must be configured with environment variables from e.g. .env-file.

The example of .env-file for service-pull:

```env
CLOUDROCK_SYNC_DIRECTION=pull # The setup for service-pull
CLOUDROCK_API_URL=http://cloudrock.example.com/api/ # Cloudrock API URL
CLOUDROCK_API_TOKEN=9e1132b9616ebfe943ddf632ca32bbb7e1109a32 # Token of a service provider in Cloudrock
CLOUDROCK_OFFERING_UUID=e21a0f0030b447deb63bedf69db6742e # UUID of SLURM offering in Cloudrock
SLURM_DEFAULT_ACCOUNT=root # Default account for SLURM
SLURM_CONTAINER_NAME=slurmctld # Name of SLURM namenode container
```

The example of .env-file for service-push:

```env
CLOUDROCK_SYNC_DIRECTION=push # The setup for service-push
CLOUDROCK_API_URL=http://cloudrock.example.com/api/ # Cloudrock API URL
CLOUDROCK_API_TOKEN=9e1132b9616ebfe943ddf632ca32bbb7e1109a32 # Token of a service provider in Cloudrock
CLOUDROCK_OFFERING_UUID=e21a0f0030b447deb63bedf69db6742e # UUID of SLURM offering in Cloudrock
SLURM_CONTAINER_NAME=slurmctld # Name of SLURM namenode container
```

### Docker-based deployment

You can find the Docker Compose configuration for testing in `examples/docker-compose/` folder.

In order to test it, you need to execute following commands in your terminal app:

```bash
cd examples/docker-compose
docker-compose up -d
```

### Native deployment

If your SLURM cluster doesn't run in Docker, you need to deploy the service natively using Python module.
The agent requires `sacct` and `sacctmgr` to be available, so it should run on a headnode of the SLURM cluster.
You can install, configure and start the `service-pull` and `service-push` processes on the with the commands below.
**Note**: the `config-components.yaml` file should be in the same directory where module starts.

```bash
pip install cloudrock-slurm-agent
# Service pull
source service-pull-env.rc
nohup python3 -m cloudrock_slurm.main > service-pull.out &

# after this:
# Service push
source service-push-env.rc
nohup python3 -m cloudrock_slurm.main > service-push.out &
```

### TRES configuration

To setup TRES-related info, the service uses the corresponding configuration file `config-components.yaml` in the root directory. Each entry of the file incudes key-value-formatted data.
A key is a type of TRES (with optional name if type is gres) and the value contains limit, measured unit, type of accounting and label.
The service sends this data to Cloudrock each time when it is restarted.
If a user wants to change this information, a custom config file should be mounted into a container.
