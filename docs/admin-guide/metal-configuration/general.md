# General Configuration

Outline:

- [General Configuration](#general-configuration)
  - [Introduction](#introduction)
  - [Admin dashboard configuration](#admin-dashboard-configuration)
  - [Custom templates configuration](#custom-templates-configuration)
  - [Local time zone configuration](#local-time-zone-configuration)

## Introduction

Cloudrock is a [Django](https://www.djangoproject.com)-based application, so configuration is done by modifying `settings.py` file.

If you want to configure options related to Django, such as tune caches, database connection, configure custom logging, etc, please refer to [Django documentation](https://docs.djangoproject.com/en/2.2/).

Please consult [configuration guide](configuration-guide.md) to learn more.

## Admin dashboard configuration

An admin dashboard supports custom links on Quick access panel. For instance, a panel below was configured with one additional link to **<https://cloudrock.ca>**:

![admin example](img/admin-example.png)

Configuration of custom links is stored under `FLUENT_DASHBOARD_QUICK_ACCESS_LINKS` settings key and for current example has following structure:

```python
FLUENT_DASHBOARD_QUICK_ACCESS_LINKS = [
  {
   'title': '[Custom] Cloudrock - Cloud Service',
   'url': 'https://cloudrock.ca',
   'external': True, # adds an icon specifying that this link is external,
   'description': 'Open-source Cloud Brokerage Platform',
   'attrs': {'target': '_blank'} # add an attribute to generated anchor element which will open link in a new tab.
  },
]
```

Here is a short description of link parameters:

| **Name** | **Type** | **Required** | **Description** |
| -------- | -------- | ------------ | --------------- |
| description | string | No | Tool tip on the link |
| external | boolean | No | Specifies whether additional icon indicating an external URL has to be added |
|url | URL | Yes | A URL of the link|
| title | string | Yes | A title of the generated link |
| attrs | dict | No | A dictionary of anchor attributes to be added to generated element |

It is also possible to omit optional fields and add links by specifying only a title and a URL to the generated link.

```python
FLUENT_DASHBOARD_QUICK_ACCESS_LINKS = [
  ['[Custom] Cloudrock - Cloud Service', 'https://cloudrock.ca'],
  ['Find us on GitHub', 'https://github.com/kubeworkz/cloudrock-core'],
]
```

## Custom templates configuration

To overwrite default templates you should use [django-dbtemplates](https://github.com/jazzband/django-dbtemplates). It allows creation of templates through `/admin`.

## Local time zone configuration

Set `TIME_ZONE` setting in `/etc/cloudrock/override.conf.py` to use local time zone. By default it is set to UTC. See the [list of time zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) for possible options.
