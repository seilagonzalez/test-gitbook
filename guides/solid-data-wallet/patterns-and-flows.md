---
icon: pallet-box
---
# UI Patterns and Flows

## Architecture

The architecture of the Solid Data Wallet consists of a Backend-for-Frontend web application pattern with these key components:

* **Data Wallet mobile application:** The Wallet user-facing mobile application that users interact with. It communicates exclusively with Inrupt's Enterprise Solid Server (ESS) Wallet Service.

* **ESS Wallet Service:** Acts as an intermediary between the Wallet mobile app and the underlying ESS microservices. It handles:
  * Storing data in Pod Services
  * CRUD operations for the Wallet
  * Provisioning Wallet storage and authorizations
  * Invoking ESS Access Grants for consent flows
  * Fetching WebID information

## Storage Organization

The Wallet uses these containers at provision time:

* `/wallet`
* `/inbox` 
* `/accessgrants`
* `/accessrequests`

## Access Requests and Grants

### Managing Requests

The Wallet Service manages Access Requests and Grants within storage. Key functions include:

* Listing pending requests from the `/inbox`
* Approving/rejecting requests
* Moving approved requests to `/accessrequests`
* Storing grants in `/accessgrants`

### Grant Details

Access Grants show:
* Expiry date
* Purpose
* Resource Name
* Data Requester WebID info

### Revoking Access

Users can revoke grants via the `/accessgrants/{id}` endpoint.

## Resource Management

### Downloading Resources

Users can:
* Scan QR codes for resources
* Store external resources in their Wallet
* Have the Wallet Service securely save items

### Sharing Resources

The sharing flow:
1. User generates a QR code with resource info
2. Third party scans the code
3. Access Request is created
4. User approves access
5. Grant is issued

Example QR code data:
```json
{
  "webid": "https://www.example.com/id",
  "resource": "https://storage.inrupt.com/934ed7a345/wallet/IMG_0005.jpg"
}