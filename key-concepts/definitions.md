# Definitions

**Identity Provider**\
An **Identity Provider** is a system that creates and manages identity information for entities. The IdP enables entities to authenticate and connect to applications and services. Identity Providers (IdPs) comply with the Solid's OpenID Connect (OIDC) protocol. The protocol is built on top of the OAuth 2.0 authorization framework. Solid OIDC is used for authentication in Solid ecosystems and provides digitally signed ID tokens that contain the entity’s WebID.

**Solid Wallet Storage**

**Solid Wallet Storage** is a data storage unit that enables users and organizations to securely manage, store, access, and share their data. These decentralized data stores operate as web servers for data, providing users complete control over their data and the ability to determine who can access it.

**Solid Application**

An **application** in Solid can be both a user-piloted app, like a mobile app, a traditional web app with a user interface (either browser only or a browser app with a backend component), or a back-end service that acts autonomously with its own identity and has no user interface. Application is a broad term that just means software.

**WebID**

A **WebID** is a URI that identifies an entity. It resolves to a WebID Document, which contains structured data about the WebID owner to aid other Solid applications in working with it (such as the entity’s trusted identity providers or Solid Wallet Storages). WebID is the first-class identifier in Solid today and can be used to identify people, organizations, or things.

**Agent**

An **agent** in Solid is something that has autonomy. Both people and applications can be agents, as can organizations, devices, or groups of people. We identify agents with a WebID.

**Entity**

An **entity** in Solid is a thing that exists. This can be a person, but it can also be a building or a car. Entities may or may not be agents. Entities have WebIDs in order to be identifiable on the web.

**Client**

A **client,** in the broadest sense, is an application that utilizes the services of another. For instance, a backend application will be the _client_ of an identity provider. A browser app will be the _client_ of the Solid server and also a _client_ of an identity provider. It is important to note that a client can mean different things in different contexts, so the term is best avoided unless talking about specific contexts or flows (like the OAuth2.0 _client credential grant,_ for example).

**Solid Managed Ecosystem**

A **Solid Ecosystem** consists of multiple applications and services involved in fetching and writing data into Solid Server(s). However, in a **Solid Managed Ecosystem**, only trusted and known applications and services can interact with the Solid Server(s). In such a scenario, restrictions are placed on the Solid Server(s) configuration to prevent any untrusted applications from accessing it.
