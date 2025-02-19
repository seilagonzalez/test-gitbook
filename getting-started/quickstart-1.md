---
icon: key-skeleton
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

# Key Concepts

### WALLET STORAGE (POD)

Wallet Storage, also known as a Pod, is a unique component within the Solid ecosystem that enables individuals to store, manage, and control access to their data. Each Wallet Storage functions as a private and secure storage space where users can decide who gets access to their information and how it is shared across applications.

### WEBID

A WebID is a URI uniquely identifying an entity in a Solid ecosystem. Digital identifier to identify a user, organizations, and agents.&#x20;

A WebID Document is an RDF document dereferenced from the WebID URI. This WebID Document allows Solid applications and services to discover services used or trusted by the entity that controls the WebID, such as their trusted Identity Providers, Solid Wallet Storages, and potentially some public personal information.\
[https://www.inrupt.com/videos/what-is-a-webid](https://www.inrupt.com/videos/what-is-a-webid)

### ACCESS GRANTS

Access grants in the context of Solid are a crucial part of managing resource permissions. They have the shape of a verifiable credential, providing a secure and standardized way to grant access rights. These credentials can assert specific permissions, such as read or write access to data, and are verified to ensure authenticity. Verifiable credentials facilitate decentralized identity management, allowing for flexible and interoperable permission structures in Solid ecosystems.

### ACCESS CONTROL POLICIES

Access Control Policies (ACPs) in Solid ecosystems define rules for who can access specific resources and what actions they can perform. These policies use a standardized framework to specify permissions, such as reading, writing, and modifying data within a Solid Wallet Storage. Access Control Resources (ACRs) are specific entities within a Solid Pod that store these rules and manage the application of policies.&#x20;

