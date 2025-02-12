---
icon: address-card
coverY: 0
---

# WebId Document Best Practices

### WebID Document Best Practice <a href="#xxx4h9nrrqcq" id="xxx4h9nrrqcq"></a>

### Introduction <a href="#id-269xsi17lc5" id="id-269xsi17lc5"></a>

This guide provides advice and best practices for creating and maintaining WebID Documents.

It will cover the following:

* Basic makeup of a WebID Document for use in a managed ecosystem
* How it is used in Solid Identity
* Considerations for architects on protecting WebID Documents on behalf of users in managed ecosystems.

### What is a WebID? <a href="#i81ddfcv2y03" id="i81ddfcv2y03"></a>

A WebID is a URI that uniquely identifies an entity in a Solid ecosystem.

More can be found here: [What is a WebID?](https://www.inrupt.com/videos/what-is-a-webid)

A WebID Document is an RDF document dereferenced from the WebID URI. This WebID Document allows Solid applications and services to discover services used or trusted by the entity that controls the Webid, such as their trusted Identity Providers, Solid Wallet Storages, and potentially some public personal information.

The WebID Document is an RDF public document and should be expressed in Turtle format, although other formats may be available.

**WebID Document Content**

The authority governing the Solid ecosystem should have control over and define the content of the WebID Document.

A WebID Document will likely contain three pieces of information:

1. A list of the entities trusted OIDC issuers used to assert their identity for access to Solid servers and apps.
2. The Solid Wallet Storages associated with that particular WebID. Applications may not have a Wallet Storage.
3. The type of entity the WebID belongs to. This could be an agent, person, or organization. By default, a WebID identity is classified as an agent, and we use the [FOAF](http://xmlns.com/foaf/0.1/) vocabulary to describe it.

Optionally, the profile could include a list of extended WebID Documents. These extended profiles are stored in Solid Wallet Storage and could be publicly accessible or protected by access control.

**Example of the minimum requirement for a WebID Document**

<mark style="color:purple;">`<https://id.inrupt.com/dave>`</mark>

<mark style="color:purple;">`a <http://xmlns.com/foaf/0.1/Agent> ;`</mark>

<mark style="color:purple;">`<http://www.w3.org/ns/pim/space#storage>`</mark>

<mark style="color:purple;">`<https://storage.inrupt.com/bb79f34c-3e25-4b9d-9b68-0193e5491111/>;`</mark>

<mark style="color:purple;">`<http://www.w3.org/ns/solid/terms#oidcIssuer>`</mark>

<mark style="color:purple;">`<https://login.inrupt.com> ;`</mark>

<mark style="color:purple;">`<http://xmlns.com/foaf/0.1/isPrimaryTopicOf>`</mark>

<mark style="color:purple;">`<https://storage.inrupt.com/bb79f34c-3e25-4b9d-9b68-0193e5491111/profile>.`</mark>



**OIDC Issuer**

\<http://www.w3.org/ns/solid/terms#oidcIssuer> \<https://login.inrupt.com> ;

The WebID Document must contain at least one Solid OIDC identity provider. Without this, the entity cannot use any Solid services that require authentication.

As part of the authentication flow, Solid Applications and Solid Servers will ensure the issuer providing the identity token is present in the WebID Document. If it is not present, the session will terminate. Only trusted IDPs must be added to the WebID Document.

The WebID Document can list multiple Identity Providers, which means more than one Solid OIDC provider can assert the same identity for a given entity or user. Assuming that all Identity Providers are onboarded, trusted, and are known providers of the WebID service, the user or application can choose which IDP to use.

**Solid Wallet Storage Storage**

The WebID Document is the primary mechanism to discover Solid Wallet Storage so that applications and services can write or fetch data. In most deployments, the user will have one Solid Wallet Storage but also may have many. If multiple Wallet Storages are present, the WebID Document must contain some metadata to aid in selecting a Solid Wallet Storage. A common way to achieve this is by using _rdfs:label_ as a description property to provide human-readable labels written by the operator. For instance, if users utilize a health app, they could choose the "Health Wallet" rather than a "Finance Wallet."



<mark style="color:purple;">`prefix foaf: <http://xmlns.com/foaf/0.1/>`</mark>

<mark style="color:purple;">`prefix pim: <http://www.w3.org/ns/pim/space#>`</mark>

<mark style="color:purple;">`prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>`</mark>

<mark style="color:purple;">`prefix solid: <http://www.w3.org/ns/solid/terms#>`</mark>

<mark style="color:purple;">`<https://id.inrupt.com/LindaSmith> a foaf:Person;`</mark>

<mark style="color:purple;">`pim:storage <https://storage.inrupt.com/bb79f34c-3e25-4b9d-9b68-0193e5491111/>, <https://storage.inrupt.com/bb79f34c-3e25-4b9d-9b68-0193e5491112/>;`</mark>

<mark style="color:purple;">`solid:oidcIssuer <https://login.inrupt.com> ;`</mark>

<mark style="color:purple;">`foaf:isPrimaryTopicOf <https://storage.inrupt.com/bb79f34c-3e25-4b9d-9b68-0193e5491111/profile>.`</mark>

<mark style="color:purple;">`<https://storage.inrupt.com/bb79f34c-3e25-4b9d-9b68-0193e5491111/> a pim:ControlledStorage;`</mark>

<mark style="color:purple;">`rdfs:label "National Health Service Solid Wallet Storage"@en.`</mark>

<mark style="color:purple;">`<https://storage.inrupt.com/bb79f34c-3e25-4b9d-9b68-0193e5493912/> a pim:ControlledStorage;`</mark>

<mark style="color:purple;">`rdfs:label "Ward Bank Solid Wallet Storage"@en.`</mark>



**Personal Information**

The WebID Document associated with a WebID may contain personal details about the user identified by the WebID. Users have the option to share their personal information in the WebID Document. Since we are referring to public face profile information, this option is exclusively available to users and does not require any explanation for agents, such as backend services.

**Vocabulary**

To promote application interoperability, we recommend a set of vocabularies to use in the WebID Document. This recommendation aims to enumerate the concepts and properties employed for most WebID services. As mentioned above in the WebID Document content section, three main concepts are referenced in a WebID Document: the type of entity, the identity providers for the users to authenticate, and the list of Solid Wallet Storages that belong to that particular WebID. The entities that hold WebID Documents can be classified as an agent, a person, or an organization using the [FOAF](http://xmlns.com/foaf/0.1/) vocabulary.

To describe the different Identity Providers, we use the[ Solid term](http://www.w3.org/ns/solid/terms) vocabulary and specifically utilize the property _oidcIssuer_. The Workspace Ontology is the recommended vocabulary for expressing Solid Wallet Storage, with _pim:storage_ being the associated property. Finally, the WebID Service administrator can decide the term for a specific property (predicate) for a possible extended profile(s).

**WebID Document Edits**

Adding untrusted OIDC Issuers or unauthorized non-user-controlled Wallet Storage to the WebID Document could constitute a security threat.

As it is unlikely that regular users will understand this significance, the governing body overseeing the managed Solid ecosystem must enforce strict controls over how modifications are made to the WebID Document. Secure tooling or applications must be created to wrap up the WebID service.

Considering the severe risks involved, regular users must be only granted permission to edit their WebID Document under extremely controlled circumstances. A WebID editor application built by the governing body should be responsible for validating and approving any potential changes. The validation process should ensure that the agent making the changes is allowed to do so and that the changes themselves are in line with the ecosystem’s security policies.

As mentioned in the document, multiple OIDC issuers can be listed in a single WebID Document.

Whilst ESS has additional guards to ensure untrusted Issuers cannot be used to authenticate users in the form of service allow lists, this should not be used as the only line of defense. Allow lists can become large and cumbersome in complex deployments.

If the Issuer Allow List grows significantly, one potential solution could be [OIDC Federation](https://openid.net/specs/openid-connect-federation-1_0.html), which would allow multiple federations and various Identity Providers. This specification is still in its early stages, but it would instruct establishing trust among a group of IdPs.

### &#x20;<a href="#s9zu0hpy0qf9" id="s9zu0hpy0qf9"></a>
