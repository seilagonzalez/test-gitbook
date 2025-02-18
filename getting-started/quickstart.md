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

### Get an Account[#](https://start.inrupt.com)

1. Create your account at [https://start.inrupt.com](https://start.inrupt.com)
2. Save your API credentials securely
3. You are now able to use our sandbox environment Pod Spaces.

### Generate CCs\[#]https://login.inrupt.com/registration.html)

1. To generate your client credentials: Go to this page to register your app. [https://login.inrupt.com/registration.html](https://login.inrupt.com/registration.html)
2. Use the client credential to create a session.

{% code title="session.ts" %}
```typescript
async function initializeAndLoginSession(): Promise<Session | null> {
  const session = new Session();
  try {
    await session.login({
      clientId: process.env.CLIENT_ID,
      clientSecret: process.env.CLIENT_SECRET,
      oidcIssuer: "https://login.inrupt.com",
      tokenType: "Bearer", //no supported DPop
    });
    if (session.info.isLoggedIn && session.info.webId) {
      console.log("Session logged in successfully with WebID");
      return session;
    } else {
      console.error("User is not logged in");
      return null;
    }
  } catch (error) {
    console.error("Error during login:", error);
    return null;
  }
}
```
{% endcode %}

3. Now include some data in the Wallet.

```typescript
PUT Data#
async function uploadFile() {
  const session = await initializeAndLoginSession();
  const walletAPI = "https://datawallet.inrupt.com";
  const fileName= "Name of the file";
  try {
    const path = "path/where/the/file/is/located"+fileName;
    const fileBuffer = await readFile(path);

    const formData = new FormData();

    const file = new File([fileBuffer], path);
    formData.append("file", file);

    formData.append("fileName", fileName);
    const response = await session?.fetch(walletAPI, {
      method: "PUT",
      body: formData,
    });

    if (response?.status === 200) {
      return "File uploaded sucessfully";
    } else {
      console.log(response);
    }
  } catch (error) {
    console.error("Error uploading file:", error);
    throw error;
  }
}

```

4. Fetch data from Wallet.

```typescript

GET Data#
async function getData() {
  const session = await initializeAndLoginSession();
  const endpoint = "https://datawallet.inrupt.com";
  try {
    const response = await session?.fetch(endpoint, {
      method: "GET"
    });
    if (response?.status === 200) {
      const data = await response.json();
      return data;
    } else {
      console.error("Error getting data:", response?.status);
      return null;
    }
  } catch (error) {
    console.error("Error:", error);
    return null;
  }
}
```

