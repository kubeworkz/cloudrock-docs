# Remote Offering

!!! warning
    Documentation is in progress. Plugin development is in progress.

## Introduction

It is possible to import into a Cloudrock offerings from a remote Cloudrock.

## Pre-requisites

- An organization in the remote Cloudrock, which will contain requests and projects from the local Cloudrock.
- Account with owner role that will be used for integration.
- Access to APIs of remote Cloudrock.

## High level process

- In local Cloudrock, make sure that you have a [service provider](adding-an-offering.md) organization available.
- Click on "Import offering".
- Input remote Cloudrock API and authentication token.
- Select the remote organization and offering to be imported.
- Review and activate the offering.

## eduTEAMS account SYNC

In case both local and remote Cloudrocks are relying on a common set of identities
from [eduTEAMS](../identities/eduTEAMS.md), it is possible to configure synchronisation of the identities as well,
i.e. when a resource is provisioned in a remote Cloudrock, local accounts from organization and project are pushed and
mapped to the remote project.

!!! note
    For this to work, remote Cloudrock must be integrated with eduTEAMS registry and integration user must have
    `identity_manager` role.
