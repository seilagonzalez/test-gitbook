# UI Patterns and Flows

## Architecture

The architecture of the Solid Data Wallet consists of a Backend-for-Frontend web application pattern with the following key components:

**Data Wallet mobile application:** The Wallet user-facing mobile application that users interact with. As of today, it communicates exclusively with Inrupt's Enterprise Solid Server (ESS) Wallet Service.

**ESS Wallet Service:** The Wallet Service acts as an intermediary between the Wallet mobile app and the underlying ESS microservices. The Wallet Service is responsible for:

* Storing data in Pod Services
* All CRUD operations for the Wallet
* Provisioning the Wallet storage and the correct authorizations for containers like the inbox
* Invoking the ESS Access Grants microservice to initiate a consent flow (Access Requests and Access Grants)
* Fetching the WebID from the WebID Service to obtain information about the Wallet user

### Wallet Storage Organization

The Wallet uses a simple storage structure to manage resources, receive requests for access to data, and manage the lifecycle of Access Requests and Grants. The following containers are created at provision time:

```bash
/wallet
/inbox
/accessgrants
/accessrequests