---
description: HERE WE EXPLAIN HOW TO GET AN ACCOUNT IN POD SPACES AND KEY CONCEPTS
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

### Get an Account[#](broken-reference)

1. Create your account at [https://start.inrupt.com](https://start.inrupt.com)
2. Save your API credentials securely
3. You are now able to use our sandbox environment Pod Spaces.

### Generate CCs[#](broken-reference)

1. To generate your client credentials: 
   Go to this page to register your app. [https://login.inrupt.com/registration.html](https://login.inrupt.com/registration.html)
2. Use the client credential to create a session.

{% code title="session.ts" %}
```typescript
async function initializeAndLoginSession(): Promise<Session | null> {
  const session = new Session();
  try {
    await session.login({
      clientId: process.env.CLIENT_ID,
      clientSecret: process.env.CLIENT_SECRET,
      oidcIssuer: process.env.IDP,
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
{% endcode %}