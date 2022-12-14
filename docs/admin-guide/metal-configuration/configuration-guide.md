# Configuration guide

## CLOUDROCK_AUTH_SAML2 plugin

Default value:

```python
CLOUDROCK_AUTH_SAML2 = {'ALLOW_TO_SELECT_IDENTITY_PROVIDER': True,
 'ATTRIBUTE_MAP_DIR': '/etc/cloudrock/saml2/attributemaps',
 'AUTHN_REQUESTS_SIGNED': 'true',
 'CATEGORIES': ['http://www.geant.net/uri/dataprotection-code-of-conduct/v1'],
 'CERT_FILE': '',
 'DEBUG': False,
 'DEFAULT_BINDING': 'urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST',
 'DESCRIPTION': 'Service provider description',
 'DIGEST_ALGORITHM': None,
 'DISCOVERY_SERVICE_LABEL': None,
 'DISCOVERY_SERVICE_URL': None,
 'DISPLAY_NAME': 'Service provider display name',
 'ENABLE_SINGLE_LOGOUT': False,
 'IDENTITY_PROVIDER_LABEL': None,
 'IDENTITY_PROVIDER_URL': None,
 'IDP_METADATA_LOCAL': [],
 'IDP_METADATA_REMOTE': [],
 'KEY_FILE': '',
 'LOGOUT_REQUESTS_SIGNED': 'true',
 'LOG_FILE': '',
 'LOG_LEVEL': 'INFO',
 'MANAGEMENT_URL': '',
 'NAME': 'saml2',
 'NAMEID_FORMAT': None,
 'OPTIONAL_ATTRIBUTES': [],
 'ORGANIZATION': {},
 'PRIVACY_STATEMENT_URL': 'http://example.com/privacy-policy/',
 'REGISTRATION_AUTHORITY': 'http://example.com/registration-authority/',
 'REGISTRATION_INSTANT': '2017-01-01T00:00:00',
 'REGISTRATION_POLICY': 'http://example.com/registration-policy/',
 'REQUIRED_ATTRIBUTES': [],
 'SAML_ATTRIBUTE_MAPPING': {},
 'SIGNATURE_ALGORITHM': None,
 'XMLSEC_BINARY': '/usr/bin/xmlsec1'}
```

### ALLOW_TO_SELECT_IDENTITY_PROVIDER

Type: bool

### ATTRIBUTE_MAP_DIR

Type: str

Directory with attribute mapping

### AUTHN_REQUESTS_SIGNED

Type: str

Indicates if the authentication requests sent should be signed by default

### CATEGORIES

Type: list

Links to the entity categories

### CERT_FILE

Type: str

PEM formatted certificate chain file

### DEBUG

Type: bool

Set to True to output debugging information

### DEFAULT_BINDING

Type: str

### DESCRIPTION

Type: str

Service provider description (required by CoC)

### DIGEST_ALGORITHM

Type: Optional[str]

Identifies the Message Digest algorithm URL according to the XML Signature specification (SHA1 is used by default)

### DISCOVERY_SERVICE_LABEL

Type: Optional[str]

### DISCOVERY_SERVICE_URL

Type: Optional[str]

### DISPLAY_NAME

Type: str

Service provider display name (required by CoC)

### ENABLE_SINGLE_LOGOUT

Type: bool

### IDENTITY_PROVIDER_LABEL

Type: Optional[str]

### IDENTITY_PROVIDER_URL

Type: Optional[str]

### IDP_METADATA_LOCAL

Type: list

IdPs metadata XML files stored locally

### IDP_METADATA_REMOTE

Type: list

IdPs metadata XML files stored remotely

### KEY_FILE

Type: str

PEM formatted certificate key file

### LOGOUT_REQUESTS_SIGNED

Type: str

Indicates if the entity will sign the logout requests

### LOG_FILE

Type: str

Empty to disable logging SAML2-related stuff to file

### LOG_LEVEL

Type: str

Log level for SAML2

### MANAGEMENT_URL

Type: str

The endpoint for user details management.

### NAME

Type: str

Name used for assigning the registration method to the user

### NAMEID_FORMAT

Type: Optional[str]

Identified NameID format to use. None means default, empty string ("") disables addition of entity

### OPTIONAL_ATTRIBUTES

Type: list

SAML attributes that may be useful to have but not required

### ORGANIZATION

Type: dict

Organization responsible for the service (you can set multilanguage information here)

### PRIVACY_STATEMENT_URL

Type: str

URL with privacy statement (required by CoC)

### REGISTRATION_AUTHORITY

Type: str

Registration authority required by mdpi

### REGISTRATION_INSTANT

Type: str

Registration instant time required by mdpi

### REGISTRATION_POLICY

Type: str

Registration policy required by mdpi

### REQUIRED_ATTRIBUTES

Type: list

SAML attributes that are required to identify a user

### SAML_ATTRIBUTE_MAPPING

Type: dict

Mapping between SAML attributes and User fields

### SIGNATURE_ALGORITHM

Type: Optional[str]

Identifies the Signature algorithm URL according to the XML Signature specification (SHA1 is used by default)

### XMLSEC_BINARY

Type: str

Full path to the xmlsec1 binary program

## CLOUDROCK_AUTH_SOCIAL plugin

Default value:

```python
CLOUDROCK_AUTH_SOCIAL = {'EDUTEAMS_AUTH_URL': 'https://proxy.acc.eduteams.org/saml2sp/OIDC/authorization',
 'EDUTEAMS_CLIENT_ID': '',
 'EDUTEAMS_LABEL': 'eduTEAMS',
 'EDUTEAMS_MANAGEMENT_URL': '',
 'EDUTEAMS_SECRET': '',
 'EDUTEAMS_TOKEN_URL': 'https://proxy.acc.eduteams.org/OIDC/token',
 'EDUTEAMS_USERINFO_URL': 'https://proxy.acc.eduteams.org/OIDC/userinfo',
 'EDUTEAMS_USER_PROTECTED_FIELDS': ['full_name', 'email'],
 'ENABLE_EDUTEAMS_SYNC': False,
 'KEYCLOAK_AUTH_URL': '',
 'KEYCLOAK_CLIENT_ID': '',
 'KEYCLOAK_LABEL': 'Keycloak',
 'KEYCLOAK_MANAGEMENT_URL': 'http://localhost:8080/auth/realms/cloudrock/account/#/personal-info',
 'KEYCLOAK_SECRET': '',
 'KEYCLOAK_TOKEN_URL': '',
 'KEYCLOAK_USERINFO_URL': '',
 'KEYCLOAK_USER_PROTECTED_FIELDS': ['full_name', 'email'],
 'KEYCLOAK_VERIFY_SSL': True,
 'REMOTE_EDUTEAMS_CLIENT_ID': '',
 'REMOTE_EDUTEAMS_ENABLED': False,
 'REMOTE_EDUTEAMS_REFRESH_TOKEN': '',
 'REMOTE_EDUTEAMS_SECRET': '',
 'REMOTE_EDUTEAMS_TOKEN_URL': 'https://proxy.acc.researcher-access.org/OIDC/token',
 'REMOTE_EDUTEAMS_USERINFO_URL': 'https://proxy.acc.researcher-access.org/api/userinfo',
 'SMARTIDEE_CLIENT_ID': '',
 'SMARTIDEE_SECRET': '',
 'TARA_CLIENT_ID': '',
 'TARA_LABEL': 'Riigi Autentimisteenus',
 'TARA_MANAGEMENT_URL': '',
 'TARA_SANDBOX': True,
 'TARA_SECRET': '',
 'TARA_USER_PROTECTED_FIELDS': ['full_name']}
```

### EDUTEAMS_AUTH_URL

Type: str

The authorization endpoint performs authentication of the end-user. This is done by redirecting the user agent to this endpoint.

### EDUTEAMS_CLIENT_ID

Type: str

ID of application used for OAuth authentication.

### EDUTEAMS_LABEL

Type: str

Label is used by Cloudrock UI for rendering login button.

### EDUTEAMS_MANAGEMENT_URL

Type: str

The endpoint for user details management.

### EDUTEAMS_SECRET

Type: str

Application secret key.

### EDUTEAMS_TOKEN_URL

Type: str

The token endpoint is used to obtain tokens.

### EDUTEAMS_USERINFO_URL

Type: str

The userinfo endpoint returns standard claims about the authenticated user, and is protected by a bearer token.

### EDUTEAMS_USER_PROTECTED_FIELDS

Type: List[str]

The list of protected fields for EDUTEAMS IdP.

### ENABLE_EDUTEAMS_SYNC

Type: bool

Enable eduTEAMS synchronization with remote Cloudrock.

### KEYCLOAK_AUTH_URL

Type: str

The authorization endpoint performs authentication of the end-user. This is done by redirecting the user agent to this endpoint.

### KEYCLOAK_CLIENT_ID

Type: str

ID of application used for OAuth authentication.

### KEYCLOAK_LABEL

Type: str

Label is used by Cloudrock UI for rendering login button.

### KEYCLOAK_MANAGEMENT_URL

Type: str

The endpoint for user details management.

### KEYCLOAK_SECRET

Type: str

Application secret key.

### KEYCLOAK_TOKEN_URL

Type: str

The token endpoint is used to obtain tokens.

### KEYCLOAK_USERINFO_URL

Type: str

The userinfo endpoint returns standard claims about the authenticated user, and is protected by a bearer token.

### KEYCLOAK_USER_PROTECTED_FIELDS

Type: List[str]

The list of protected fields for Keycloak IdP.

### KEYCLOAK_VERIFY_SSL

Type: bool

Validate TLS certificate of Keycloak REST API

### REMOTE_EDUTEAMS_CLIENT_ID

Type: str

ID of application used for OAuth authentication.

### REMOTE_EDUTEAMS_ENABLED

Type: bool

Enable remote eduTEAMS extension.

### REMOTE_EDUTEAMS_REFRESH_TOKEN

Type: str

Token is used to authenticate against user info endpoint.

### REMOTE_EDUTEAMS_SECRET

Type: str

Application secret key.

### REMOTE_EDUTEAMS_TOKEN_URL

Type: str

The token endpoint is used to obtain tokens.

### REMOTE_EDUTEAMS_USERINFO_URL

Type: str

It allows to get user data based on userid aka CUID.

### SMARTIDEE_CLIENT_ID

Type: str

ID of application used for OAuth authentication.

### SMARTIDEE_SECRET

Type: str

Application secret key.

### TARA_CLIENT_ID

Type: str

ID of application used for OAuth authentication.

### TARA_LABEL

Type: str

You may set it to eIDAS, SmartID or MobileID make it more clear to the user which exact identity provider is configured or preferred for service provider.

### TARA_MANAGEMENT_URL

Type: str

The endpoint for user details management.

### TARA_SANDBOX

Type: bool

You should set it to False in order to switch to production mode.

### TARA_SECRET

Type: str

Application secret key.

### TARA_USER_PROTECTED_FIELDS

Type: List[str]

The list of protected fields for TARA IdP.

## CLOUDROCK_CORE plugin

Default value:

```python
CLOUDROCK_CORE = {'ATTACHMENT_LINK_MAX_AGE': datetime.timedelta(seconds=3600),
 'AUTHENTICATION_METHODS': ['LOCAL_SIGNIN'],
 'BACKEND_FIELDS_EDITABLE': True,
 'BRAND_COLOR': '#3a8500',
 'COUNTRIES': ['AL',
               'AT',
               'BA',
               'BE',
               'BG',
               'CH',
               'CY',
               'DE',
               'DK',
               'EE',
               'ES',
               'EU',
               'FI',
               'FR',
               'GB',
               'GE',
               'GR',
               'HR',
               'HU',
               'IE',
               'IS',
               'IT',
               'LT',
               'LU',
               'LV',
               'MC',
               'MK',
               'MT',
               'NL',
               'NO',
               'PL',
               'PT',
               'RO',
               'RS',
               'SE',
               'SI',
               'UA'],
 'CREATE_DEFAULT_PROJECT_ON_ORGANIZATION_CREATION': False,
 'CURRENCY_NAME': 'EUR',
 'DOCS_URL': '',
 'EMAIL_CHANGE_MAX_AGE': datetime.timedelta(days=1),
 'ENABLE_ACCOUNTING_START_DATE': False,
 'ENABLE_GEOIP': True,
 'EXTENSIONS_AUTOREGISTER': True,
 'EXTERNAL_LINKS': [],
 'FULL_PAGE_TITLE': 'Cloudrock | Cloud Service Management',
 'GOOGLE_ANALYTICS_ID': '',
 'GROUP_INVITATION_LIFETIME': datetime.timedelta(days=7),
 'HERO_IMAGE': None,
 'HERO_LINK_LABEL': None,
 'HERO_LINK_URL': None,
 'CLOUDROCK_UI_SENTRY_DSN': None,
 'CLOUDROCK_UI_URL': 'https://example.com/',
 'HTTP_CHUNK_SIZE': 50,
 'INITIAL_CUSTOMER_AGREEMENT_NUMBER': 4000,
 'INVITATIONS_ENABLED': True,
 'INVITATION_CIVIL_NUMBER_HELP_TEXT': 'Must start with a country prefix ie '
                                      'EE34501234215',
 'INVITATION_CIVIL_NUMBER_LABEL': '',
 'INVITATION_CREATE_MISSING_USER': False,
 'INVITATION_DISABLE_MULTIPLE_ROLES': False,
 'INVITATION_LIFETIME': datetime.timedelta(days=7),
 'INVITATION_MAX_AGE': None,
 'INVITATION_TAX_NUMBER_LABEL': '',
 'LOCAL_IDP_LABEL': 'Local DB',
 'LOCAL_IDP_MANAGEMENT_URL': '',
 'LOCAL_IDP_NAME': 'Local DB',
 'LOCAL_IDP_PROTECTED_FIELDS': [],
 'LOGGING_REPORT_DIRECTORY': '/var/log/cloudrock',
 'LOGGING_REPORT_INTERVAL': datetime.timedelta(days=7),
 'METAL_URL': '',
 'NATIVE_NAME_ENABLED': False,
 'NOTIFICATIONS_PROFILE_CHANGES': {'ENABLE_OPERATOR_OWNER_NOTIFICATIONS': False,
                                   'FIELDS': ('email',
                                              'phone_number',
                                              'job_title'),
                                   'OPERATOR_NOTIFICATION_EMAILS': []},
 'NOTIFICATION_SUBJECT': 'Notifications from Cloudrock',
 'ONLY_STAFF_CAN_INVITE_USERS': False,
 'ONLY_STAFF_MANAGES_SERVICES': False,
 'OWNERS_CAN_MANAGE_OWNERS': False,
 'OWNER_CAN_MANAGE_CUSTOMER': False,
 'POWERED_BY_LOGO': None,
 'PROTECT_USER_DETAILS_FOR_REGISTRATION_METHODS': [],
 'SELLER_COUNTRY_CODE': None,
 'SHORT_PAGE_TITLE': 'Cloudrock',
 'SHOW_ALL_USERS': False,
 'SIDEBAR_LOGO': None,
 'SIDEBAR_LOGO_MOBILE': None,
 'SITE_ADDRESS': '',
 'SITE_DESCRIPTION': 'Your single pane of control for managing projects, teams '
                     'and resources in a self-service manner.',
 'SITE_EMAIL': '',
 'SITE_LOGO': None,
 'SITE_NAME': 'Cloudrock',
 'SITE_PHONE': '',
 'SUPPORT_PORTAL_URL': '',
 'TOKEN_KEY': 'x-auth-token',
 'TOKEN_LIFETIME': datetime.timedelta(seconds=3600),
 'TRANSLATION_DOMAIN': '',
 'USER_MANDATORY_FIELDS': ['full_name', 'email'],
 'USER_REGISTRATION_HIDDEN_FIELDS': ['registration_method',
                                     'job_title',
                                     'phone_number',
                                     'organization'],
 'USE_ATOMIC_TRANSACTION': True,
 'VALIDATE_INVITATION_EMAIL': False}
```

### ATTACHMENT_LINK_MAX_AGE

Type: timedelta

Max age of secure token for media download.

### AUTHENTICATION_METHODS

Type: List[str]

List of enabled authentication methods.

### BACKEND_FIELDS_EDITABLE

Type: bool

Allows to control /admin writable fields. If this flag is disabled it is impossible to edit any field that corresponds to backend value via /admin. Such restriction allows to save information from corruption.

### BRAND_COLOR

Type: Optional[str]

Hex color definition is used in Cloudrock UI landing page for login button.

### COUNTRIES

Type: List[str]

It is used in organization creation dialog in order to limit country choices to predefined set.

### CREATE_DEFAULT_PROJECT_ON_ORGANIZATION_CREATION

Type: bool

Enables generation of the first project on organization creation.

### CURRENCY_NAME

Type: str

It is used in marketplace order details and invoices for currency formatting.

### DOCS_URL

Type: str

Renders link to docs in header

### EMAIL_CHANGE_MAX_AGE

Type: timedelta

Max age of change email request.

### ENABLE_ACCOUNTING_START_DATE

Type: bool

Allows to enable accounting for organizations using value of accounting_start_date field.

### ENABLE_GEOIP

Type: bool

Enable detection of coordinates of virtual machines.

### EXTENSIONS_AUTOREGISTER

Type: bool

Defines whether extensions should be automatically registered.

### EXTERNAL_LINKS

Type: List[ExternalLink]

Render external links in dropdown in header. Each item should be object with label and url fields. For example: {"label": "Helpdesk", "url": "`https://example.com/`"}

### FULL_PAGE_TITLE

Type: str

It is used as default page title if it's not specified explicitly.

### GOOGLE_ANALYTICS_ID

Type: str

Identifier associated with your account and used by Google Analytics to collect the data.

### GROUP_INVITATION_LIFETIME

Type: timedelta

Defines for how long group invitation remains valid.

### HERO_IMAGE

Type: Optional[str]

Relative path to image rendered at hero section of Cloudrock UI landing page.

### HERO_LINK_LABEL

Type: Optional[str]

Label for link in hero section of Cloudrock UI landing page. It can be lead to support site or blog post.

### HERO_LINK_URL

Type: Optional[str]

Link URL in hero section of Cloudrock UI landing page.

### CLOUDROCK_UI_SENTRY_DSN

Type: Optional[str]

Sentry Data Source Name for Cloudrock UI project.

### CLOUDROCK_UI_URL

Type: str

It is used for rendering callback URL in Cloudrock UI.

### HTTP_CHUNK_SIZE

Type: int

Chunk size for resource fetching from backend API. It is needed in order to avoid too long HTTP request error.

### INITIAL_CUSTOMER_AGREEMENT_NUMBER

Type: int

Allows to tweak initial value of agreement number. It is assumed that organization owner should accept terms of services when organization is registered via Cloudrock UI.

### INVITATIONS_ENABLED

Type: bool

Allows to disable invitations feature.

### INVITATION_CIVIL_NUMBER_HELP_TEXT

Type: str

Help text for civil number field in invitation creation dialog.

### INVITATION_CIVIL_NUMBER_LABEL

Type: str

Custom label for civil number field in invitation creation dialog.

### INVITATION_CREATE_MISSING_USER

Type: bool

Allow to create FreeIPA user using details specified in invitation if user does not exist yet.

### INVITATION_DISABLE_MULTIPLE_ROLES

Type: bool

Do not allow user to grant multiple roles in the same project or organization using invitation.

### INVITATION_LIFETIME

Type: timedelta

Defines for how long invitation remains valid.

### INVITATION_MAX_AGE

Type: Optional[timedelta]

Max age of invitation token. It is used in approve and reject actions.

### INVITATION_TAX_NUMBER_LABEL

Type: str

Custom label for tax number field in invitation creation dialog.

### LOCAL_IDP_LABEL

Type: str

The label of local auth.

### LOCAL_IDP_MANAGEMENT_URL

Type: str

The URL for management of local user details.

### LOCAL_IDP_NAME

Type: str

The name of local auth.

### LOCAL_IDP_PROTECTED_FIELDS

Type: List[str]

The list of protected fields for local IdP.

### LOGGING_REPORT_DIRECTORY

Type: str

Directory where log files are located.

### LOGGING_REPORT_INTERVAL

Type: timedelta

Files older that specified interval are filtered out.

### METAL_URL

Type: str

It is used for rendering callback URL in Metal.

### NATIVE_NAME_ENABLED

Type: bool

Allows to render native name field in customer and user forms.

### NOTIFICATIONS_PROFILE_CHANGES

Type: dict

Configure notifications about profile changes of organization owners.

### NOTIFICATION_SUBJECT

Type: str

It is used as a subject of email emitted by event logging hook.

### ONLY_STAFF_CAN_INVITE_USERS

Type: bool

Allow to limit invitation management to staff only.

### ONLY_STAFF_MANAGES_SERVICES

Type: bool

Allows to restrict provider management only to staff users.

### OWNERS_CAN_MANAGE_OWNERS

Type: bool

Enables organization owners to manage other organization owners.

### OWNER_CAN_MANAGE_CUSTOMER

Type: bool

Enables organization owners to create an organization.

### POWERED_BY_LOGO

Type: Optional[str]

Relative path to image rendered at the bottom of login menu in Cloudrock UI.

### PROTECT_USER_DETAILS_FOR_REGISTRATION_METHODS

Type: List[str]

List of authentication methods which are not allowed to update user details.

### SELLER_COUNTRY_CODE

Type: Optional[str]

Specifies seller legal or effective country of registration or residence as an ISO 3166-1 alpha-2 country code. It is used for computing VAT charge rate.

### SHORT_PAGE_TITLE

Type: str

it is used as prefix for page title.

### SHOW_ALL_USERS

Type: bool

Indicates whether user can see all other users in `api/users/` endpoint.

### SIDEBAR_LOGO

Type: Optional[str]

Relative path to image rendered at the top of sidebar menu in Cloudrock UI.

### SIDEBAR_LOGO_MOBILE

Type: Optional[str]

Relative path to image rendered at the top of mobile sidebar menu in Cloudrock UI.

### SITE_ADDRESS

Type: str

It is used in marketplace order header.

### SITE_DESCRIPTION

Type: str

Description of the Cloudrock deployment.

### SITE_EMAIL

Type: str

It is used in marketplace order header and UI footer.

### SITE_LOGO

Type: Optional[str]

It is used in marketplace order header.

### SITE_NAME

Type: str

Human-friendly name of the Cloudrock deployment.

### SITE_PHONE

Type: str

It is used in marketplace order header and UI footer.

### SUPPORT_PORTAL_URL

Type: str

Support portal URL is rendered as a shortcut on dashboard

### TOKEN_KEY

Type: str

Header for token authentication.

### TOKEN_LIFETIME

Type: timedelta

Defines for how long user token should remain valid if there was no action from user.

### TRANSLATION_DOMAIN

Type: str

Identifier of translation domain applied to current deployment.

### USER_MANDATORY_FIELDS

Type: List[str]

List of user profile attributes that would be required for filling in Cloudrock UI. Note that backend will not be affected. If a mandatory field is missing in profile, a profile edit view will be forced upon user on any Cloudrock UI logged in action. Possible values are: description, email, full_name, job_title, organization, phone_number

### USER_REGISTRATION_HIDDEN_FIELDS

Type: List[str]

List of user profile attributes that would be concealed on registration form in Cloudrock UI. Possible values are: job_title, registration_method, phone_number

### USE_ATOMIC_TRANSACTION

Type: bool

Wrap action views in atomic transaction.

### VALIDATE_INVITATION_EMAIL

Type: bool

Ensure that invitation and user emails match.

## CLOUDROCK_FREEIPA plugin

Default value:

```python
CLOUDROCK_FREEIPA = {'BLACKLISTED_USERNAMES': ['root'],
 'ENABLED': False,
 'GROUPNAME_PREFIX': 'cloudrock_',
 'GROUP_SYNCHRONIZATION_ENABLED': True,
 'HOSTNAME': 'ipa.example.com',
 'PASSWORD': 'secret',
 'USERNAME': 'admin',
 'USERNAME_PREFIX': 'cloudrock_',
 'VERIFY_SSL': True}
```

### BLACKLISTED_USERNAMES

Type: list

List of username that users are not allowed to select

### ENABLED

Type: bool

Enable integration of identity provisioning in configured FreeIPA

### GROUPNAME_PREFIX

Type: str

Prefix to be appended to all group names created in FreeIPA by Cloudrock

### GROUP_SYNCHRONIZATION_ENABLED

Type: bool

Optionally disable creation of user groups in FreeIPA matching Cloudrock structure

### HOSTNAME

Type: str

Hostname of FreeIPA server

### PASSWORD

Type: str

Password of FreeIPA user with administrative privileges

### USERNAME

Type: str

Username of FreeIPA user with administrative privileges

### USERNAME_PREFIX

Type: str

Prefix to be appended to all usernames created in FreeIPA by Cloudrock

### VERIFY_SSL

Type: bool

Validate TLS certificate of FreeIPA web interface / REST API

## CLOUDROCK_HPC plugin

Default value:

```python
CLOUDROCK_HPC = {'ENABLED': False,
 'EXTERNAL_AFFILIATIONS': [],
 'EXTERNAL_CUSTOMER_UUID': '',
 'EXTERNAL_EMAIL_PATTERNS': [],
 'EXTERNAL_LIMITS': {},
 'INTERNAL_AFFILIATIONS': [],
 'INTERNAL_CUSTOMER_UUID': '',
 'INTERNAL_EMAIL_PATTERNS': [],
 'INTERNAL_LIMITS': {},
 'OFFERING_UUID': '',
 'PLAN_UUID': ''}
```

### ENABLED

Type: bool

Enable HPC-specific hooks in Cloudrock deployment

### EXTERNAL_AFFILIATIONS

Type: List[str]

List of user affiliations (eduPersonScopedAffiliation fields) that define if the user belongs to external organization.

### EXTERNAL_CUSTOMER_UUID

Type: str

UUID of a Cloudrock organization (aka customer) where new external users would be added

### EXTERNAL_EMAIL_PATTERNS

Type: List[str]

List of user email patterns (as regex) that define if the user belongs to external organization.

### EXTERNAL_LIMITS

Type: dict

Overrided default values for SLURM offering to be created for users belonging to external organization.

### INTERNAL_AFFILIATIONS

Type: List[str]

List of user affiliations (eduPersonScopedAffiliation fields) that define if the user belongs to internal organization.

### INTERNAL_CUSTOMER_UUID

Type: str

UUID of a Cloudrock organization (aka customer) where new internal users would be added

### INTERNAL_EMAIL_PATTERNS

Type: List[str]

List of user email patterns (as regex) that define if the user belongs to internal organization.

### INTERNAL_LIMITS

Type: dict

Overrided default values for SLURM offering to be created for users belonging to internal organization.

### OFFERING_UUID

Type: str

UUID of a Cloudrock SLURM offering, which will be used for creating allocations for users

### PLAN_UUID

Type: str

UUID of a Cloudrock SLURM offering plan, which will be used for creating allocations for users

## CLOUDROCK_KEYCLOAK plugin

Default value:

```python
CLOUDROCK_KEYCLOAK = {'BASE_URL': 'http://localhost:8080/auth',
 'CLIENT_ID': 'cloudrock',
 'CLIENT_SECRET': 'UUID',
 'ENABLED': False,
 'PASSWORD': 'secret',
 'REALM': 'cloudrock',
 'USERNAME': 'admin'}
```

### BASE_URL

Type: str

Base URL of Keycloak server

### CLIENT_ID

Type: str

Identification of Cloudrock client app

### CLIENT_SECRET

Type: str

Credentials are generated in Keycloak admin console

### ENABLED

Type: bool

Enable integration of group provisioning in configured Keycloak

### PASSWORD

Type: str

Password of Keycloak user with administrative privileges

### REALM

Type: str

Realm used by Cloudrock

### USERNAME

Type: str

Username of Keycloak user with administrative privileges

## CLOUDROCK_MARKETPLACE plugin

Default value:

```python
CLOUDROCK_MARKETPLACE = {'ADMIN_CAN_APPROVE_ORDER': False,
 'ANONYMOUS_USER_CAN_VIEW_OFFERINGS': True,
 'ANONYMOUS_USER_CAN_VIEW_PLANS': True,
 'DISABLE_SENDING_NOTIFICATIONS_ABOUT_RESOURCE_UPDATE': True,
 'ENABLE_RESOURCE_END_DATE': True,
 'ENABLE_STALE_RESOURCE_NOTIFICATIONS': False,
 'MANAGER_CAN_APPROVE_ORDER': False,
 'NOTIFY_ABOUT_RESOURCE_CHANGE': True,
 'NOTIFY_STAFF_ABOUT_APPROVALS': False,
 'OWNER_CAN_APPROVE_ORDER': True,
 'OWNER_CAN_REGISTER_SERVICE_PROVIDER': False,
 'THUMBNAIL_SIZE': (120, 120)}
```

### ADMIN_CAN_APPROVE_ORDER

Type: bool

If true, orders for resource can be approved by admin of the customer project

### ANONYMOUS_USER_CAN_VIEW_OFFERINGS

Type: bool

Allow anonymous users to see shared offerings in active, paused and archived states

### ANONYMOUS_USER_CAN_VIEW_PLANS

Type: bool

Allow anonymous users to see plans

### DISABLE_SENDING_NOTIFICATIONS_ABOUT_RESOURCE_UPDATE

Type: bool

Disable only resource update events.

### ENABLE_RESOURCE_END_DATE

Type: bool

Allow to view and update resource end date.

### ENABLE_STALE_RESOURCE_NOTIFICATIONS

Type: bool

Enable reminders to owners about resources of shared offerings that have not generated any cost for the last 3 months.

### MANAGER_CAN_APPROVE_ORDER

Type: bool

If true, orders for resource can be approved by manager of the customer project

### NOTIFY_ABOUT_RESOURCE_CHANGE

Type: bool

If true, notify users about resource changes from Marketplace perspective. Can generate duplicate events if plugins also log

### NOTIFY_STAFF_ABOUT_APPROVALS

Type: bool

If true, users with staff role are notified when request for order approval is generated

### OWNER_CAN_APPROVE_ORDER

Type: bool

If true, orders for resource can be approved by custom organization owner.

### OWNER_CAN_REGISTER_SERVICE_PROVIDER

Type: bool

Allow organization owner to request or mark its organization as service provider

### THUMBNAIL_SIZE

Type: tuple

Size of the thumbnail to generate when screenshot is uploaded for an offering.

## CLOUDROCK_MARKETPLACE_SCRIPT plugin

Default value:

```python
CLOUDROCK_MARKETPLACE_SCRIPT = {'DOCKER_CLIENT': {'base_url': 'unix://var/run/docker.sock'},
 'DOCKER_IMAGES': {'python': 'python:3.8-alpine', 'shell': 'alpine:3'},
 'DOCKER_RUN_OPTIONS': {'mem_limit': '64m'},
 'DOCKER_SCRIPT_DIR': None,
 'K8S_CONFIG_PATH': '~/.kube/config',
 'K8S_JOB_TIMEOUT': 1800,
 'K8S_NAMESPACE': 'default',
 'SCRIPT_RUN_MODE': 'docker'}
```

### DOCKER_CLIENT

Type: dict

Options for docker client. See also: <https://docker-py.readthedocs.io/en/stable/client.html#docker.client.DockerClient>

### DOCKER_IMAGES

Type: dict

Key is command to execute script, value is image name.

### DOCKER_RUN_OPTIONS

Type: dict

Options for docker runtime. See also: <https://docker-py.readthedocs.io/en/stable/containers.html#docker.models.containers.ContainerCollection.run>

### DOCKER_SCRIPT_DIR

Type: Optional[str]

Path to folder on executor machine where to create temporary submission scripts. If None uses OS-dependent location. OS X users, see <https://github.com/docker/for-mac/issues/1532>

### K8S_CONFIG_PATH

Type: str

Path to Kubernetes configuration file

### K8S_JOB_TIMEOUT

Type: int

Timeout for execution of one Kubernetes job in seconds

### K8S_NAMESPACE

Type: str

Kubernetes namespace where jobs will be executed

### SCRIPT_RUN_MODE

Type: str

Type of jobs deployment. Valid values: "docker" for simple docker deployment, "k8s" for Kubernetes-based one

## CLOUDROCK_OPENSTACK plugin

Default value:

```python
CLOUDROCK_OPENSTACK = {'ADMIN_CAN_MANAGE_TENANTS': False,
 'DEFAULT_BLACKLISTED_USERNAMES': ['admin', 'service'],
 'DEFAULT_SECURITY_GROUPS': ({'description': 'Security group for any access',
                              'name': 'allow-all',
                              'rules': ({'cidr': '0.0.0.0/0',
                                         'icmp_code': -1,
                                         'icmp_type': -1,
                                         'protocol': 'icmp'},
                                        {'cidr': '0.0.0.0/0',
                                         'from_port': 1,
                                         'protocol': 'tcp',
                                         'to_port': 65535})},
                             {'description': 'Security group for secure shell '
                                             'access',
                              'name': 'ssh',
                              'rules': ({'cidr': '0.0.0.0/0',
                                         'from_port': 22,
                                         'protocol': 'tcp',
                                         'to_port': 22},)},
                             {'description': 'Security group for ping',
                              'name': 'ping',
                              'rules': ({'cidr': '0.0.0.0/0',
                                         'icmp_code': -1,
                                         'icmp_type': -1,
                                         'protocol': 'icmp'},)},
                             {'description': 'Security group for remove '
                                             'desktop access',
                              'name': 'rdp',
                              'rules': ({'cidr': '0.0.0.0/0',
                                         'from_port': 3389,
                                         'protocol': 'tcp',
                                         'to_port': 3389},)},
                             {'description': 'Security group for http and '
                                             'https access',
                              'name': 'web',
                              'rules': ({'cidr': '0.0.0.0/0',
                                         'from_port': 80,
                                         'protocol': 'tcp',
                                         'to_port': 80},
                                        {'cidr': '0.0.0.0/0',
                                         'from_port': 443,
                                         'protocol': 'tcp',
                                         'to_port': 443})}),
 'MANAGER_CAN_MANAGE_TENANTS': False,
 'SUBNET': {'ALLOCATION_POOL_END': '{first_octet}.{second_octet}.{third_octet}.200',
            'ALLOCATION_POOL_START': '{first_octet}.{second_octet}.{third_octet}.10'},
 'TENANT_CREDENTIALS_VISIBLE': False}
```

### ADMIN_CAN_MANAGE_TENANTS

Type: bool

If true, admin can delete or change configuration of tenants.

### DEFAULT_BLACKLISTED_USERNAMES

Type: list

Usernames that cannot be created by Cloudrock in OpenStack

### DEFAULT_SECURITY_GROUPS

Type: tuple

Default security groups and rules created in each of the provisioned OpenStack tenants

### MANAGER_CAN_MANAGE_TENANTS

Type: bool

If true, manager can delete or change configuration of tenants.

### SUBNET

Type: dict

Default allocation pool for auto-created internal network

### TENANT_CREDENTIALS_VISIBLE

Type: bool

If true, generated credentials of a tenant are exposed to project users

## CLOUDROCK_OPENSTACK_TENANT plugin

Default value:

```python
CLOUDROCK_OPENSTACK_TENANT = {'ALLOW_CUSTOMER_USERS_OPENSTACK_CONSOLE_ACCESS': True,
 'ALLOW_DIRECT_EXTERNAL_NETWORK_CONNECTION': False,
 'MAX_CONCURRENT_PROVISION': {'OpenStackTenant.Instance': 4,
                              'OpenStackTenant.Snapshot': 4,
                              'OpenStackTenant.Volume': 4},
 'REQUIRE_AVAILABILITY_ZONE': False}
```

### ALLOW_CUSTOMER_USERS_OPENSTACK_CONSOLE_ACCESS

Type: bool

If true, customer users would be offered actions for accessing OpenStack Console

### ALLOW_DIRECT_EXTERNAL_NETWORK_CONNECTION

Type: bool

If true, allow connecting of Instances directly to external networks

### MAX_CONCURRENT_PROVISION

Type: dict

Maximum parallel executions of provisioning operations for OpenStackTenant resources

### REQUIRE_AVAILABILITY_ZONE

Type: bool

If true, specification of availability zone during provisioning will become mandatory

## CLOUDROCK_PID plugin

Default value:

```python
CLOUDROCK_PID = {'DATACITE': {'API_URL': 'https://example.com',
              'COLLECTION_DOI': '',
              'PASSWORD': '',
              'PREFIX': '',
              'PUBLISHER': 'Cloudrock',
              'REPOSITORY_ID': ''}}
```

### DATACITE

Type: dict

Settings for integration of Cloudrock with Datacite PID service. Collection DOI is used to aggregate generated DOIs.

## CLOUDROCK_SLURM plugin

Default value:

```python
CLOUDROCK_SLURM = {'ALLOCATION_PREFIX': 'cloudrock_allocation_',
 'CUSTOMER_PREFIX': 'cloudrock_customer_',
 'DEFAULT_LIMITS': {'CPU': 16000, 'GPU': 400, 'RAM': 102400000},
 'ENABLED': False,
 'PRIVATE_KEY_PATH': '/etc/cloudrock/id_rsa',
 'PROJECT_PREFIX': 'cloudrock_project_'}
```

### ALLOCATION_PREFIX

Type: str

Prefix for SLURM account name corresponding to Cloudrock allocation

### CUSTOMER_PREFIX

Type: str

Prefix for SLURM account name corresponding to Cloudrock organization.

### DEFAULT_LIMITS

Type: dict

Default limits of account that are set when SLURM account is provisioned.

### ENABLED

Type: bool

Enable support for SLURM plugin in a deployment

### PRIVATE_KEY_PATH

Type: str

Path to private key file used as SSH identity file for accessing SLURM master.

### PROJECT_PREFIX

Type: str

Prefix for SLURM account name corresponding to Cloudrock project.

## Other variables

### DEFAULT_FROM_EMAIL

Type: str, default value: webmaster@localhost

Default email address to use for automated correspondence from Cloudrock.

### DEFAULT_REPLY_TO_EMAIL

Type: str

Default email address to use for email replies.

### IMPORT_EXPORT_USE_TRANSACTIONS

Type: bool, default value: True

Controls if resource importing should use database transactions. Using transactions makes imports safer as a failure during import won???t import only part of the data set.

### IPSTACK_ACCESS_KEY

Type: Optional[str]

Unique authentication key used to gain access to the ipstack API.

### LANGUAGES

Type: List[Tuple[str, str]], default value: (('en', 'English'), ('et', 'Eesti'))

The list is a list of two-tuples in the format (language code, language name) ??? for example, ('ja', 'Japanese'). This specifies which languages are available for language selection.

### LANGUAGE_CODE

Type: str, default value: en

Represents the name of a default language.

### USE_PROTECTED_URL

Type: bool, default value: False

Protect media URLs using signed token.

### VERIFY_WEBHOOK_REQUESTS

Type: bool, default value: True

When webook is processed, requests verifies SSL certificates for HTTPS requests, just like a web browser.

