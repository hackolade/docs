---
description: Register an application in Microsoft Entra ID so Hackolade Studio users can connect to Collibra with OAuth.
seoTitle: Collibra OAuth setup with Microsoft Entra ID
image: lib/Collibra Entra ID JWT endpoints.png
---
# OAuth setup with Entra ID

This page is relevant for Hackolade Studio client connection to a Collibra instance using an identified user. It does not apply to a server or CLI instance of Hackolade Studio establishing a [machine-to-machine connection to Collibra](Machine-to-machineconnectiontoCo.md) using a service account.

## 1. Register an Application in Microsoft Entra ID

> [!NOTE]
> We start by the setup **in Azure Entra ID**

1. Go to **Azure Portal > Microsoft Entra ID > App registrations**
2. Click **New registration**
   1. Configure:
   2. Name (example): `Collibra Integration`
3. Supported account types: usually **Single tenant**
4. After creation:
   1. Save **Application (client) ID**
   2. Save **Directory (tenant) ID**

More detailed instructions in the [official Microsoft documentation](<https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app> "target=\"_blank\"")

## 2. Configure API Permissions of the Application

1. Go to **API Permissions in the left panel**
2. Add:
   1. `User.Read` (required)
   2. `openid profile offline_access` (optional)

![Collibra Entra ID API permissions](<lib/Collibra Entra ID API permissions.png>)

1. Click **Grant admin consent**

## 3. Retrieve OpenID Configuration from the Overview of the Application

Copy the **Entra well-known endpoint**:

```text
https://login.microsoftonline.com/{tenant-id}/v2.0/.well-known/openid-configuration
```

Or:

Go to **Overview > Endpoints**\
Copy and open the link from **the OpenID Connect metadata document**

![Collibra Entra ID JWT endpoints](<lib/Collibra Entra ID JWT endpoints.png>)

From this JSON, extract:

- `jwks_uri` → used in Collibra
- `issuer` → used in Collibra

## 4. Map Values to Collibra Configuration

> [!NOTE]
> Need to configure Collibra **using Collibra console**

1\. Open Collibra console: `https://console-{company-domain}.collibra.com`\
2\. Select your environment -> **Data Governance Center > Configuration > Security configuration > JWT**

![Collibra Entra ID JWT security config](<lib/Collibra Entra ID JWT security config.png>)

Next properties should be mapped:

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
<td>Collibra uses <code>sub</code> by default. Enter the claim whose value is exactly the Collibra username, for example <code>preferred_username</code> when Collibra usernames are sign-in names. A Collibra user with this exact username must exist. See <a href="https://hackolade.com/help/OAuthsetupwithEntraID.html#5.%20How%20Collibra%20matches%20the%20token%20to%20a%20user">section 5</a> below.</td>
</tr>
<tr>
<td>JWT Maximum Clock Skew</td>
<td></td>
<td></td>
<td>Leave it blank</td>
</tr>
</tbody>
</table>

## 5. How Collibra matches the token to a user

When you connect from Hackolade Studio, Microsoft Entra ID issues an access token for your user, and Hackolade Studio sends this token to Collibra. Collibra reads one value from the token and looks for a Collibra user with exactly this username. If no user matches, Collibra refuses the connection, even when all other JWT properties are correct.

An access token contains several fields, called claims. Each claim has a name and a value. For example, the decoded token of John Doe contains these claims, among others (Microsoft lists all of them in its [access token claims reference](<https://learn.microsoft.com/en-us/entra/identity-platform/access-token-claims-reference> "target=\"_blank\""), if you want to know what each claim contains):

```text
sub: "AAAAAAAAAAAAAAAAAAAAAIkzqFVrSaSaFHy782bbtaQ"
preferred_username: "john.doe@yourcompany.com"
aud: "..."
iss: "..."
```

In the `JWT Principal ID Claim Name` property, you set which claim Collibra reads. The default value is `sub`, as described in the [Collibra JWT authentication guide](<https://developer.collibra.com/tutorials/rest-api-json-web-token> "target=\"_blank\""). Entra ID fills `sub` with an identifier generated for your application. The default value works only if your Collibra usernames contain exactly this identifier.

In this example, the Collibra username of John Doe is his sign-in name, `john.doe@yourcompany.com`. This value is in the `preferred_username` claim, not in `sub`. With `sub`, no user matches. With `preferred_username`, Collibra finds the user:

![Collibra compares the claim selected in JWT Principal ID Claim Name with the Collibra username: sub does not match, preferred_username matches](<lib/Collibra Entra ID claim matching.png>)

To check which claim to use for your organization:

1. Retrieve an access token for a test user and decode it, as described for the JWT Audience above.
2. In Collibra, open this user and note the username.
3. In the decoded token, find the claim whose value is exactly this username, and enter the name of this claim in `JWT Principal ID Claim Name`. If this claim is `sub`, keep the default value.

If no claim of the token contains the Collibra username, add the missing claim in Entra ID as an optional claim (`App registrations > your application > Token configuration`), or align the Collibra usernames with a claim that the token already contains.

> [!NOTE]
> The value of `preferred_username` can change in Entra ID, for example after a name change. When it changes, update the username in Collibra as well, otherwise Collibra refuses the connection of this user.
