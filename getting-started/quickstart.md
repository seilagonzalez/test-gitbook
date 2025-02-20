---
icon: bullseye-arrow
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Quickstart

This guide will help you get started using our API. Follow these steps to quickly begin managing data.

### Get an Account

1. Create your account at [https://start.inrupt.com](https://start.inrupt.com)
2. Save your API credentials securely
3. You are now able to use our sandbox environment Pod Spaces.

### Generate Client Credentials

1. To generate your client credentials: Go to this page to register your app. [https://login.inrupt.com/registration.html](https://login.inrupt.com/registration.html)
2. Use the client credential to create a session.

{% code title="Session" %}
```javascript
async function initializeAndLoginSession() {
  const session = new Session();
  await session.login({
    clientId: process.env.CLIENT_ID,
    clientSecret: process.env.CLIENT_SECRET,
    oidcIssuer: "https://login.inrupt.com",
    tokenType: "Bearer",
  });
  
  if (session.info.isLoggedIn && session.info.webId) {
    console.log("Session logged in successfully with WebID");
    return session;
  } else {
    console.error("User is not logged in");
    return null;
  }
}

 
```
{% endcode %}

## Load data in the Wallet

```typescript
PUT Data
async function uploadFile() {
  const session = await initializeAndLoginSession();
  const walletContainer = "https://datawallet.inrupt.com/wallet";
  const path = "path/where/the/file/is/located" + "/text.txt";
  const fileBuffer = await readFile(path);
  const formData = new FormData();
  const file = new File([fileBuffer], path);
  formData.append("file", file);
  formData.append("fileName", fileName);

  const response = await session.fetch(walletContainer, {
    method: "PUT",
    body: formData,
  });

  if (response.status === 200) {
    return "File uploaded successfully";
  } else {
    console.log(response);
  }
}

```

## Get the Wallet Data

```typescript

GET Data
async function getFile() {
  const session = await initializeAndLoginSession();
  const walletContainer = "https://datawallet.inrupt.com/wallet";
  const file = walletContainer + "/text.txt";
  
  if (!session) {
    throw new Error("Session is undefined");
  }
  
  const response = await session.fetch(file, {
    method: "GET",
  });
  
  if (response.status === 200) {
    const fetchCredential = await response.text();
    return fetchCredential;
  }
}

```

## Delete data from the Wallet

```typescript
Delete Data
async function deleteFile() {
  const session = await initializeAndLoginSession();
  const walletContainer = "https://datawallet.inrupt.com/wallet";
  const file = walletContainer + "/text.txt";
  
  if (!session) {
    throw new Error("Session is undefined");
  }
  
  const response = await session.fetch(file, {
    method: "DELETE",
  });
  
  if (response.status === 200) {
    return "file deleted successfully";
  }
}
```
