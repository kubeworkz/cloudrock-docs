# Azure

!!! warning
    Documentation is in progress. Plugin development is in progress.

## Setting up Tenant

<https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-create-new-tenant>

## Setting up a Client

<https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app>

## Add permissions

Make sure that client is able to perform operations on the different resources.

<https://stackoverflow.com/questions/42134892/the-client-with-object-id-does-not-have-authorization-to-perform-action-microso>

## Collecting Azure credentials for Cloudrock

You need to provide following Azure credentials to Cloudrock: subscription ID, tenant ID, client ID and client secret.

### Get Subscription ID

- Login into your Azure account.
- Select **Subscriptions** in the left sidebar.
- Select whichever subscription is needed.
- Click on **Overview**.
- Copy the **Subscription ID**.

### Get Tenant ID

- Login into your Azure account.
- Select **Azure Active Directory** in the left sidebar.
- Click **Properties**.
- Copy the **Directory ID**.

### Get Client ID

- Login into your Azure account.
- Select **Azure Active Directory** in the left sidebar.
- Click **Enterprise applications**.
- Click **All applications**.
- Select the application which you have created.
- Click **Properties**.
- Copy the **Application ID**.

### Get Client secret

- Login into your Azure account.
- Select **Azure Active Directory** in the left sidebar.
- Click **App registrations**.
- Select the application which you have created.
- Click on **All settings**.
- Click on **Keys**.
- Type **Key description** and select the **Duration**.
- Click save.
- Copy and store the key value. You won’t be able to retrieve it after you leave this page.

See also: [How to: Use the portal to create an Azure AD application and service principal that can access resources](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal)
