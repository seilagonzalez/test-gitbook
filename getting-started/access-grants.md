---
icon: badge-check
---

# Access Grants

### Get a Business Account

1. Create a business account at [https://start.inrupt.com](https://start.inrupt.com)
2. Save your API credentials securely
3. You are now able to use our sandbox environment Pod Spaces.



### Create an Access Request

Things that you need to know:

1. You need to know the resource owner's WebID.
2. You can find the userWalletStorage in the resource owner WebID
3. The location of the resource you want to access
4. Create a session for the business application.

```javascript

import { issueAccessRequest } from "@inrupt/solid-client-access-grants";
    const vcData = await issueAccessRequest(
      {
        access: { read: true },
        resourceOwner: resourceOwner,
        resources: [userWalletStorage + '/wallet/text.txt'],
        expirationDate: new Date(Date.now() + 60 * 60 * 10000),
      },
      {
        fetch: businessSession.fetch,
      }
    );

```



### Send the Access Request to the Inbox

```javascript
const inboxUrl = new URL('inbox/', userWalletStorage).toString();
const vcId = vcData.id.substring('https://vc.inrupt.com/vc/'.length);

const verifiablePresentation = JSON.stringify({
  '@context': ['https://www.w3.org/2018/credentials/v1'],
  type: 'VerifiablePresentation',
  verifiableCredential: [vcData]
});

const response = await enterpriseSession.fetch(inboxUrl, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Slug': vcId
  },
  body: verifiablePresentation
});
```

## VIEW ACCESS REQUESTS



## ACCEPT ACCESS REQUEST

## VIEW ACCESS GRANTS
