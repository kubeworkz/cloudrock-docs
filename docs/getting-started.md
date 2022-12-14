# Getting started

Installing Cloudrock is a simple and straightforward process.

## Pick method of installation

There are 2 supported methods:

- [Using docker-compose](admin-guide/deployment/docker-compose.md). Fastest but runs on a single server.
- [Using Helm](admin-guide/deployment/helm/index.md). For deploying on Kubernetes clusters.

## Configure Cloudrock

Tune Cloudrock configuration to match your deployment. Majority of the configuration is done on Metal side.
Exact method of configuration depends on the chosen method of installation.
Settings are grouped by modules, you can see all available ones in
the [configuration guide](admin-guide/metal-configuration/configuration-guide.md).

The most typical aspects for configuration are:

- Configuring [identity providers](admin-guide/identities/summary.md). Cloudrock supports a range of OIDC and SAML based IdPs.
- [Adding offerings](admin-guide/providers/adding-an-offering.md) for sharing among Cloudrock users.

!!! tip
    For easier management of Cloudrock deployments and configuration we
    provide [Ansible playbooks](admin-guide/managing-with-ansible.md).

## Profit

You are done! If you are happy and want to support the project, make sure you check the [support page](about/support.md).

!!! danger
    Before going to production, make sure you have completed
    the [go-live checklist](admin-guide/checklist-for-production.md).
