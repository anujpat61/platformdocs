---
sidebar_position: 1
sidebar_label: SAML Quickstart
sidebar_custom_props:
  icon: KeyRound
---

# SAML Quickstart

Integrate SAML with Quilr for enterprise Single Sign-On (SSO) authentication.

- **Category:** SAML/SSO
- **Integration Type:** SAML 2.0

## Setup

1. Go to **Integrations** and open the **Available** tab.
2. Click **+ Add** on the **SAML** tile.
3. Provide the configuration details below from your identity provider.
4. Click **Allow** to complete the setup.

## Required Configuration

- Identity Provider metadata
- SAML assertion consumer service (ACS) URL
- Certificate configuration

## What This Integration Does

- Enables SSO authentication for Quilr.
- Integrates with enterprise identity providers.
- Provides secure authentication workflows.

---

## Okta SAML Configuration

Configure Okta as your SAML identity provider for Quilr Single Sign-On (SSO).

### Prerequisites

- Okta administrator access
- Quilr administrator access
- Your organization's email domain configured in Quilr

### Step 1: Create a New SAML Application in Okta

1. Log in to your **Okta Admin Console** at `https://your-subdomain-admin.okta.com`
2. Navigate to **Applications** → **Applications**
3. Click **Create App Integration**
4. Select **SAML 2.0** and click **Next**
5. Enter an **App name** (e.g., "Quilr")
6. Optionally upload a logo for easy identification
7. Click **Next**

### Step 2: Configure SAML Settings in Okta

In the **Configure SAML** step, set the following:

#### General Settings

| Okta Field | Value |
|------------|-------|
| **Single sign-on URL** | `https://<your-quilr-domain>/bff/auth/auth/saml/callback` |
| **Use this for Recipient URL and Destination URL** | ✓ Checked |
| **Audience URI (SP Entity ID)** | `https://<your-quilr-domain>/bff/auth/saml/metadata/<tenant-id>` |
| **Default RelayState** | `<tenant-id>` |
| **Name ID format** | EmailAddress |
| **Application username** | Email |

#### Advanced Settings

| Setting | Recommended Value |
|---------|-------------------|
| **Response** | Signed |
| **Assertion Signature** | Signed |
| **Signature Algorithm** | RSA-SHA256 |
| **Digest Algorithm** | SHA256 |
| **Assertion Encryption** | Unencrypted |

### Step 3: Complete App Creation

1. In the **Feedback** step, select **I'm an Okta customer adding an internal app**
2. Click **Finish**

### Step 4: Get Okta IDP Details

After creating the application, go to the **Sign On** tab and click **View SAML setup instructions** or **View IdP metadata**.

Collect the following values to configure in Quilr:

| Quilr Field | Where to Find in Okta |
|-------------|----------------------|
| **IDP Entity ID** | Identity Provider Issuer |
| **IDP SSO URL** | Identity Provider Single Sign-On URL |
| **IDP SLO URL** | Identity Provider Single Logout URL (if available) |
| **IDP Signing Certificate** | X.509 Certificate (download and copy contents) |

#### Downloading the Certificate

1. In the **Sign On** tab, scroll to **SAML Signing Certificates**
2. Click **Actions** → **Download certificate** for the active certificate
3. Open the downloaded `.cert` file and copy the contents

### Step 5: Assign Users and Groups in Okta (Optional)

1. Go to the **Assignments** tab in your Okta application
2. Click **Assign** → **Assign to People** or **Assign to Groups**
3. Select the users or groups who should have access to Quilr
4. Click **Save and Go Back**
5. Users must be assigned to the application to authenticate via SAML

### Configure Quilr SAML Integration

### Step 1 : - 

1. In Quilr, go to **Integrations** → **Available** tab
2. Click **+ Add** on the **SAML** tile
3. Enter the following configuration:

| Quilr Field | Value |
|-------------|-------|
| **Name** | Okta SSO (or your preferred name) |
| **IDP Entity ID** | Paste the Identity Provider Issuer from Okta |
| **IDP SSO URL** | Paste the Identity Provider Single Sign-On URL from Okta |
| **IDP SLO URL** | Paste the Single Logout URL from Okta (optional) |
| **IDP Signing Certificate** | Paste the X.509 certificate from Okta |
| **Domain** | Your organization's email domain (e.g., `company.com`) |
| **Name ID Format** | `emailAddress` |
| **Signature Algorithm** | `SHA256` |
| **Want Assertions Signed** | `Yes` |
| **Want Authn Response Signed** | `Yes` |
| **Enforce SAML** | `Yes` to reauthenticate via Okta, `No` to allow independent login methods |

4. Click **Allow** to save the configuration

### Step 2: Test the Integration

1. Open an incognito/private browser window
2. Navigate to your Quilr login page
3. If **Enforce SAML** is enabled:
   - Clicking Microsoft or Google login will redirect to Okta
4. If **Enforce SAML** is disabled:
   - You can test SAML by entering your email domain
5. Authenticate with your Okta credentials
6. You should be redirected back to Quilr and logged in

### Okta Troubleshooting

| Issue | Solution |
|-------|----------|
| "Invalid signature" error | Verify the IDP Signing Certificate is correctly copied without extra spaces or line breaks |
| "User not found" error | Ensure the user is assigned to the application in Okta |
| "Invalid audience" error | Verify the Audience URI (SP Entity ID) in Okta matches Quilr's SP metadata |
| Login redirects but fails | Check that the Single sign-on URL matches your Quilr environment |
| "SAML Response not valid" | Ensure both Response and Assertion signatures are enabled in Okta |

For additional details, see the [Okta SAML Documentation](https://help.okta.com/en-us/content/topics/apps/apps_app_integration_wizard_saml.htm).

---

## OneLogin SAML Configuration

Configure OneLogin as your SAML identity provider for Quilr Single Sign-On (SSO).

### Prerequisites

- OneLogin administrator access
- Quilr administrator access
- Your organization's email domain configured in Quilr

### Step 1: Create a New Application in OneLogin

1. Log in to your **OneLogin Admin Portal** at `https://your-subdomain.onelogin.com/admin`
2. Navigate to **Applications** → **Add App**
3. Search for **"SAML Custom Connector (Advanced)"** and select it
4. Enter a **Display Name** (e.g., "Quilr")
5. Optionally upload a logo for easy identification
6. Click **Save**

### Step 2: Configure Application Settings in OneLogin

In the **Configuration** tab of your OneLogin application, set the following:

| OneLogin Field | Value |
|----------------|-------|
| **RelayState** | `<tenant-id>` |
| **Audience (EntityID)** | Copy from Quilr's SP Metadata XML (EntityID) |
| **Recipient** | `https://<your-quilr-domain>/bff/auth/auth/saml/callback` |
| **ACS (Consumer) URL** | `https://<your-quilr-domain>/bff/auth/auth/saml/callback` |
| **ACS URL Validator** | `.*` or `https://your-quilr-domain\.com/bff/auth/auth/saml/callback` |
| **Single Logout URL** | Leave empty unless SLO is required |

### Step 3: Configure SAML Parameters

In the **Parameters** tab:

1. Ensure the **NameID** parameter is configured
2. Set **NameID value** to the user's email address
3. This ensures Quilr receives the user's email for authentication

### Step 4: Configure SSO Settings

In the **SSO** tab, configure the following security settings:

| Setting | Recommended Value |
|---------|-------------------|
| **SAML Signature Element** | Both (Response and Assertion) |
| **SAML nameID format** | Email |
| **SAML Signature Algorithm** | SHA-256 |

### Step 5: Get OneLogin IDP Details

From the **SSO** tab in OneLogin, collect the following values to configure in Quilr:

| Quilr Field | Where to Find in OneLogin |
|-------------|---------------------------|
| **IDP Entity ID** | Issuer URL |
| **IDP SSO URL** | SAML 2.0 Endpoint (HTTP-POST) |
| **IDP SLO URL** | SLO Endpoint (HTTP-Redirect) |
| **IDP Signing Certificate** | X.509 Certificate → Click "View Details" and copy |

### Step 6: Assign Users in OneLogin

1. Go to the **Access** tab in your OneLogin application
2. Assign the appropriate users or roles who should have access to Quilr
3. Users must be assigned to the application to authenticate via SAML

### Configure Quilr SAML Integration

### Step 1: - 

1. In Quilr, go to **Integrations** → **Available** tab
2. Click **+ Add** on the **SAML** tile
3. Enter the following configuration:

| Quilr Field | Value |
|-------------|-------|
| **Name** | OneLogin SSO (or your preferred name) |
| **IDP Entity ID** | Paste the Issuer URL from OneLogin |
| **IDP SSO URL** | Paste the SAML 2.0 Endpoint (HTTP-POST) from OneLogin |
| **IDP SLO URL** | Paste the SLO Endpoint from OneLogin (optional) |
| **IDP Signing Certificate** | Paste the X.509 certificate from OneLogin |
| **Domain** | Your organization's email domain (e.g., `company.com`) |
| **Name ID Format** | `emailAddress` |
| **Signature Algorithm** | `SHA256` |
| **Want Assertions Signed** | `Yes` |
| **Want Authn Response Signed** | `Yes` |
| **Enforce SAML** | `Yes` to redirect Microsoft/Google logins to OneLogin, `No` to allow independent login methods |

4. Click **Allow** to save the configuration

### Step 2: Test the Integration

1. Open an incognito/private browser window
2. Navigate to your Quilr login page
3. If **Enforce SAML** is enabled:
   - Clicking Microsoft or Google login will redirect to OneLogin
4. If **Enforce SAML** is disabled:
   - You can test SAML by entering your email domain
5. Authenticate with your OneLogin credentials
6. You should be redirected back to Quilr and logged in

### OneLogin Troubleshooting

| Issue | Solution |
|-------|----------|
| "Invalid signature" error | Verify the IDP Signing Certificate is correctly copied without extra spaces or line breaks |
| "User not found" error | Ensure the user is assigned to the application in OneLogin |
| "Invalid audience" error | Verify the Audience (EntityID) in OneLogin matches Quilr's SP metadata |
| Login redirects but fails | Check that the ACS URL matches your Quilr environment |

For additional details, see the [OneLogin SAML Configuration Guide](https://onelogin.service-now.com/support?id=kb_article&sys_id=8a1f3d501b392510c12a41d5ec4bcbcc).

---

## Configuration Options

### Enforce SAML

The **Enforce SAML** option controls how users authenticate:

| Setting | Behavior |
|---------|----------|
| **Yes** | Microsoft and Google login attempts redirect to your SSO provider |
| **No** | Users can choose between Microsoft, Google, or SAML independently |

This is useful for organizations that want to enforce centralized authentication for all users.

### Certificate Tips

- Headers (`-----BEGIN CERTIFICATE-----`) are optional
- Line breaks are automatically handled
- Ensure the complete certificate content is copied

### Certificate Rotation

When your IdP rotates certificates:
1. Download new certificate from IdP
2. Update in Quilr SAML configuration
3. Test the integration
