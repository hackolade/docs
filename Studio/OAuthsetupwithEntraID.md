# OAuth setup with Entra ID

This page is relevant for Hackolade Studio client connection to a Collibra instance using an identified user. It does not apply to a server or CLI instance of Hackolade Studio establishing a [machine-to-machine connection to Collibra](Machine-to-machineconnectiontoCo.md) using a service account.

&nbsp;

## 1. Register an Application in Microsoft Entra ID

> [!NOTE]
> We start by the setup **in Azure Entra ID**

&nbsp;

1. Go to **Azure Portal > Microsoft Entra ID > App registrations**
2. Click **New registration**
   1. Configure:
   2. Name (example): `Collibra Integration`
3. Supported account types: usually **Single tenant**
4. After creation:
   1. Save **Application (client) ID**
   2. Save **Directory (tenant) ID**

&nbsp;

More detailed instructions in the [official Microsoft documentation](<https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app> "target=\"_blank\"")

&nbsp;

## 2. Configure API Permissions of the Application

1. Go to **API Permissions in the left panel**
2. Add:
   1. `User.Read` (required)
   2. `openid profile offline_access` (optional)

&nbsp;

![Collibra Entra ID API permissions](<lib/Collibra Entra ID API permissions.png>)

1. Click **Grant admin consent**

&nbsp;

## 3. Retrieve OpenID Configuration from the Overview of the Application

Copy the **Entra well-known endpoint**:

&nbsp;

```text
https://login.microsoftonline.com/{tenant-id}/v2.0/.well-known/openid-configuration
```

&nbsp;

Or:

&nbsp;

Go to **Overview > Endpoints**\
Copy and open the link from **the OpenID Connect metadata document**

&nbsp;

![Collibra Entra ID JWT endpoints](<lib/Collibra Entra ID JWT endpoints.png>)

&nbsp;

From this JSON, extract:

- `jwks_uri` → used in Collibra
- `issuer` → used in Collibra

&nbsp;

## 4. Map Values to Collibra Configuration

> [!NOTE]
> Need to configure Collibra **using Collibra console**

&nbsp;

1\. Open Collibra console: https://console-{company-domain}.collibra.com\
2\. Select your environment -> **Data Governance Center > Configuration > Security configuration > JWT**

&nbsp;

![Collibra Entra ID JWT security config](<lib/Collibra Entra ID JWT security config.png>)

&nbsp;

Next properties should be mapped:

&nbsp;

<table style="width:100%">
<colgroup><col style="width:14%"><col style="width:29%"><col style="width:30%"><col style="width:27%"></colgroup>
<thead>
<tr>
<th>Collibra JWT property name</th>
<th>From Entra ID</th>
<th>Example</th>
<th>Comment</th>
</tr>
</thead>
<tbody>
<tr>
<td>JSON Web Key Set URL</td>
<td><code>jwks_uri</code> - from well-known endpoint endpoint</td>
<td>https://login.microsoftonline.com/{tenant-id}/discovery/v2.0/keys</td>
<td></td>
</tr>
<tr>
<td>JWT Token Types</td>
<td></td>
<td>at+jwt,jwt</td>
<td>Keep default Collibra's value (if not changed token configuration in Entra ID)</td>
</tr>
<tr>
<td>JWT Algorithms</td>
<td>RS256</td>
<td></td>
<td>Leave it blank (if not changed token configuration in Entra ID)</td>
</tr>
<tr>
<td>JWT Issuer</td>
<td><code>issuer</code> - from well-known endpoint endpoint</td>
<td>https://login.microsoftonline.com/{tenant-id}/oauth2/v2.0/token</td>
<td></td>
</tr>
<tr>
<td>JWT Audience</td>
<td>from Access token for Entra ID application</td>
<td></td>
<td><p>To determine the JWT Audience, retrieve an access token from Microsoft Entra ID and decode it (for example, using jwt.io or Postman).<br>Use the value of the audience claim from the token.</p><blockquote><p>[!NOTE]</p><p>In some configurations, the Application ID URI may not be defined. In such cases, the audience is determined by the resource requested during token generation, so decoding the token is the only reliable method.</p></blockquote></td>
</tr>
<tr>
<td>JWT Principal ID Claim Name</td>
<td>One of the supported values from <code>claims_supported</code> - from well-known endpoint endpoint</td>
<td>preferred_username</td>
<td><ul><li>Ensure a Collibra internal user exists</li><li>Username must match this claim value</li></ul></td>
</tr>
<tr>
<td>JWT Maximum Clock Skew</td>
<td></td>
<td></td>
<td>Leave it blank</td>
</tr>
</tbody>
</table>
