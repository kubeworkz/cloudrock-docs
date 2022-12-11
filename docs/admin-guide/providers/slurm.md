# SLURM provider

SLURM plugin enables sharing of access to a [SLURM](https://slurm.schedmd.com/) cluster.
SLURM is a scheduling system used typically for managing High-performance clusters. Cloudrock allows to
share access by creating Slurm accounts and managing permission rights of users.

## Configure Cloudrock SLURM plugin

By default, Cloudrock creates a hierarchical account structure in SLURM, where:

- Organization gets an account under a default account, defined when configuring SLURM service offering;
- Each project is created as a an allocation, which is a child of organization's account.
- Each resource created in Cloudrock (aka SLURM Allocation) gets its own SLURM account with project account as a parent.

These accounts get standard prefixes along with unique values and user provided input.
It is possible to customize prefixes in Cloudrock configuration. Check CLOUDROCK_SLURM variables in
[Cloudrock configuration guide](../metal-configuration/configuration-guide.md).

## Add SLURM provider

To add SLURM as a [provider](adding-an-offering.md) to Cloudrock, you will need the following information:

- SSH host address to a node, from where SLURM commands could be executed.
- Username that has Slurm [operator role](https://slurm.schedmd.com/user_permissions.html).
  Operator is needed as Cloudrock dynamically creates accounts based on user's choice of FreeIPA account.
- Cloudrock public key must be added as authorized_key for the operator's username.
- Slurm login node must be configured to authenticate users coming from FreeIPA connected to Cloudrock.

## SLURM auto-provisioning hooks

It is possible to streamline creation of SLURM allocations for new users based on affiliation of a user profile.
Configuration settings are described in [Cloudrock configuration guide](../metal-configuration/configuration-guide.md)
under CLOUDROCK_HPC settings.

The logic is as follows:

- Once a user is created (e.g. via eduGAIN login), user's affiliation and email are checked to see if user belongs
  to internal or external organization.
- If so, a project is created for the user in a corresponding organization.
- For users belonging to internal organization, SLURM request is pre-filled and created using account limits of
  internal organizations.
- For users belonging to external organization, SLURM request is pre-filled only - it would require a manual confirmation
  from the organization owner of the external organization to be provisioned. Default limits of SLURM apply.

## Configure SLURM cluster

Cloudrock might work out of the box with most of the reasonably modern deployments of SLURM, which have
accounting enabled and limits enforced.

Please refer to SLURM documentation for details:

- [SLURM Accounting](https://slurm.schedmd.com/accounting.html)
- [SLURM Resource Limits](https://slurm.schedmd.com/resource_limits.html)
- [SLURM Multifactor Priority Plugin](https://slurm.schedmd.com/priority_multifactor.html)

We provide a snapshot of instructions for the convenience of the reader.

### Add SLURM cluster

SLURM accounting plugin assumes that at least one cluster is configured. For example:

```bash
sacctmgr add cluster linux
```

### Enforce SLURM accounting limits

In order to enforce limits set on associations and QoS, please modify slurm.conf:

```bash
AccountingStorageEnforce=limits
```

Please note, that when AccountingStorageEnforce is changed, a restart of the slurmctld daemon is required (not just a ``scontrol reconfig``):

```bash
systemctl restart slurmctld
```

### Enable SLURM Multi Priority plugin

In order to enable ordering for the queue of jobs waiting to be scheduled, please modify slurm.conf:

```bash
PriorityType=priority/multifactor
```

When slurm.conf is changed, you should reload configuration:

```bash
scontrol reconfig
```
