# Backups

Cloudrock keeps state in 2 components:

- Database - main persistency layer.
- Message queue - contains transient data mostly about scheduled jobs and cache.

Of these, only database needs to be backed up.

A typical approach to a backup is:

## 1. Create a DB dump

1. An entire db dump

```bash
docker exec -t cloudrock-db pg_dump -U cloudrock cloudrock | gzip -9 > cloudrock-$(date +'%Y%m%dT%H%M%S').sql.gz
```

1. An entire db dump with cleanup commands:

```bash
docker exec -t cloudrock-db pg_dump --clean -U cloudrock cloudrock | gzip -9 > cloudrock-$(date +'%Y%m%dT%H%M%S').sql.gz
```

1. A db dump containing only data

```bash
docker exec -t cloudrock-db pg_dump -a -U cloudrock cloudrock | gzip -9 > cloudrock-$(date +'%Y%m%dT%H%M%S').sql.gz
```

## 2. Copy backup to a remote location

Using rsync / scp or more specialised tools.

## 3. Restore the created backup

```bash
cat cloudrock-backup.sql | docker exec -i cloudrock-db psql -U cloudrock
```

We suggest to make sure that backups are running regularly, e.g. using cron.
