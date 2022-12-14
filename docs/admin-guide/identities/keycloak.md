# Keycloak

Cloudrock supports integration with [Keycloak](http://keycloak.org/) identity manager.

Below is a guide to configure Keycloak OpenID Connect client and Cloudrock intergration.

## Configuring Keycloak

Instructions below are aimed to provide a basic configuration of Keycloak, please refer to Keycloak documentation for full details.

1. Login to admin interface of Keycloak.
1. Create a new realm (or use existing)
 [![New realm](img/keycloak-add-realm.png)](img/keycloak-add-realm.png)
1. Open a menu with a list of clients.
 [![List clients](img/keycloak-client-list.png)](img/keycloak-client-list.png)
1. Add a new client for Cloudrock.
 [![Add client](img/keycloak-add-client.png)](img/keycloak-add-client.png)
1. Change client's access type to "confidential".
 [![Set access type](img/keycloak-client-access-type.png)](img/keycloak-client-access-type.png)
1. Change client's Valid redirect URIs to "*".
 [![Valid redirect URIs](img/keycloak-client-redirect.png)](img/keycloak-client-redirect.png)
1. You can get secret code for the client configuration
 [![Secret code](img/keycloak-client-secret.png)](img/keycloak-client-secret.png)
1. You can find the settings required for configuration of Cloudrock under the following path on your Keycloak deployment (change `test-cloudrock` to the realm that you are using):  `/auth/realms/test-cloudrock/.well-known/openid-configuration`

## Configuring Cloudrock

1. Add Keycloak related configuration to Metal's `override.py`:

    ```python
    CLOUDROCK_AUTH_SOCIAL.update({'KEYCLOAK_AUTH_URL': 'https://KEYCLOAK_ADDRESS:8080/auth/realms/test-cloudrock/.well-known/openid-configuration',
     'KEYCLOAK_CLIENT_ID': 'CLIENT_ID',
     'KEYCLOAK_SECRET': 'SECRET'
     'KEYCLOAK_TOKEN_URL': 'https://KEYCLOAK_ADDRESS:8080/auth/realms/test-cloudrock/protocol/openid-connect/token',
     'KEYCLOAK_USERINFO_URL': 'https://KEYCLOAK_ADDRESS:8080/auth/realms/test-cloudrock/protocol/openid-connect/userinfo'
    })
    ```

1. Make sure `SOCIAL_SIGNUP` is added to the list of available authentication methods:

    ```python
    CLOUDROCK_CORE['AUTHENTICATION_METHODS'] = ["LOCAL_SIGNIN", "SOCIAL_SIGNUP"]
    ```

    Full Keycloak related configuration settings are available at [Metal configuration file reference](../metal-configuration/configuration-guide.md)
