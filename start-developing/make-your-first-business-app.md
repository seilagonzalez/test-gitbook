# Make your first Business Application

### Get an Account

1. Create a business account at [https://start.inrupt.com](https://start.inrupt.com)
2. Save your API credentials securely
3. You are now able to use our sandbox environment Pod Spaces.



### Create an Access Request

Things that you need to know:

1. You need to know the resourceOwner WebID
2. the location of the

````
// Some code
```javascript
import { issueAccessRequest } from "@inrupt/solid-client-access-grants";
    const vcData = await issueAccessRequest(
      {
        access: { read: true },
        resourceOwner: resourceOwner,
        resources: [userPodStorage + '/wallet/dummy.json'],
        expirationDate: new Date(Date.now() + 60 * 60 * 10000),
      },
      {
        fetch: enterpriseSession.fetch,
      }
    );

```
````
