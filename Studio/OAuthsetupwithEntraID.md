# OAuth setup with Entra ID

This page is relevant for Hackolade Studio client connection to a Collibra instance using an identified user.&nbsp; It does not apply to a server or CLI instance of Hackolade Studio establishing a [machine-to-machine connection to Collibra](<Machine-to-machineconnectiontoCo.md>) using a service account. &nbsp;

## &#49;. Register an Application in Microsoft Entra ID

**Note:** we start by the setup **in Azure Entra ID**

&nbsp;

1. Go to **Azure Portal \> Microsoft Entra ID \> App registrations**
1. Click **New registration**

   1. Configure:
   1. Name (example): Collibra Integration

1. Supported account types: usually **Single tenant**
1. After creation:

   1. Save **Application (client) ID**
   1. Save **Directory (tenant) ID**

&nbsp;

More detailed instructions in the [official Microsoft documentation](<https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app> "target=\"\_blank\"")

&nbsp;

## &#50;. Configure API Permissions of the Application

1. Go to **API Permissions in the left panel**
1. Add:

   1. User.Read&nbsp; (required)
   1. openid profile offline\_access (optional)

&nbsp;

&nbsp; &nbsp; ![Collibra Entra ID API permissions](<lib/Collibra Entra ID API permissions.png>)

&nbsp;

3. Click **Grant admin consent**

&nbsp;

## &#51;. Retrieve OpenID Configuration from the Overview of the Application

Copy the **Entra well-known endpoint**:

&nbsp;

> https://login.microsoftonline.com/{tenant-id}/v2.0/.well-known/openid-configuration

&nbsp;

Or:

&nbsp;

Go to **Overview \> Endpoints**

Copy and open the link from **the OpenID Connect metadata document**

&nbsp;

![Collibra Entra ID JWT endpoints](<lib/Collibra Entra ID JWT endpoints.png>)

&nbsp;

From this JSON, extract:

* jwks\_uri → used in Collibra
* issuer → used in Collibra

&nbsp;

&nbsp;

&nbsp;

## &#52;. Map Values to Collibra Configuration

**Note:** need to configure Collibra **using Collibra console**

&nbsp;

&#49;. Open Collibra console: https://console-{company-domain}.collibra.com

&#50;. Select your environment -\> **Data Governance Center \>&nbsp; Configuration \>&nbsp; Security configuration \> JWT**

&nbsp;

![Collibra Entra ID JWT security config](<lib/Collibra Entra ID JWT security config.png>)

&nbsp;

Next properties should be mapped:

&nbsp;

&nbsp;

| **Collibra JWT property name** | **From Entra ID** | **Example** | **Comment** |
| --- | --- | --- | --- |
| JSON Web Key Set URL | jwks\_uri - from well-known endpoint endpoint | https://login.microsoftonline.com/{tenant-id}/discovery/v2.0/keys |  |
| JWT Token Types |  | at+jwt,jwt | Keep default Collibra's value (if not changed token configuration in Entra ID) |
| JWT Algorithms | RS256 |  | Leave it blank (if not changed token configuration in Entra ID) |
| JWT Issuer | issuer - from well-known endpoint endpoint | https://login.microsoftonline.com/{tenant-id}/oauth2/v2.0/token |  |
| JWT Audience | from Access token for Entra ID application |  | To determine the JWT Audience, retrieve an access token from Microsoft Entra ID and decode it (for example, using jwt.io or Postman). Use the value of the audience claim from the token. **Note:** In some configurations, the Application ID URI may not be defined. In such cases, the audience is determined by the resource requested during token generation, so decoding the token is the only reliable method. |
| JWT Principal ID Claim Name | One of the supported values from claims\_supported - from well-known endpoint endpoint | preferred\_username | Ensure a Collibra internal user exists Username must match this claim value |
| JWT Maximum Clock Skew |  |  | Leave it blank |


&nbsp;

&nbsp;

&nbsp;

&nbsp;

