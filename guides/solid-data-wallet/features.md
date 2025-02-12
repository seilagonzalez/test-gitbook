---
icon: pallet-box
---

# Features

### Login[#](broken-reference)

The Data Wallet allows users to log in using an identity provider (IDP) configured at build time and follows the [Solid OIDC](https://solidproject.org/TR/oidc-primer) flow.

The default IDP for PodSpaces will be [https://login.inrupt.com/](https://login.inrupt.com/). After logging in, the user is taken to the home tab.

### Home[#](broken-reference)

#### Managing Data in the Wallet[#](broken-reference)

Users are able to browse and manage the contents of their Wallet on the Home tab.

**Adding Data to the Wallet**[**#**](broken-reference)

The Add function allows users to upload data to the Wallet from the phone file system, the photo library, or by taking a photo with the camera.



Note

The ESS Wallet Service restricts the size of resources uploaded to 10MB. Resources larger than this limit will not be uploaded.

**File**[**#**](broken-reference)

When File is selected, the OS File browser is opened. Users can select a file from their file system and the file is uploaded to the Wallet.

**Photo**[**#**](broken-reference)

When Photo is selected, the OS Photo gallery is opened. Users can select a photo from their photo library and the photo is uploaded to the Wallet.

**Camera**[**#**](broken-reference)

When Camera is selected, the OS camera is started. Users can take a photo with their phone camera and the photo is uploaded to the Wallet.

**Scan**[**#**](broken-reference)

Users can use the Scan function to scan a QR code and download a resource, such as a verifiable credential, image, binary file, or cryptographic key, and store it in the Wallet. The QR code must contain details of the resource to be downloaded. For example:

```
{
   "uri": "https://storage.example/data/MyImage",
   "contentType":"image/png"
}
```

#### Viewing data in the Wallet[#](broken-reference)

On the Home tab, selecting a resource will display its content as follows:

If the file is a W3C Verifiable Credential, it is opened and the following information from the VC is displayed:

* The claim, the metadata, and an icon showing the revocation status.
* The signature of the credential will be checked and the revocation list obtained will need to be obtained to validate the credential.

If the file is a Photo, it is opened and displayed.

If the file is not in a supported image format or a credential, it will not be opened or displayed, however, the Actions menu will open so the user can choose an action to take, such as downloading it to the device or deleting it from the Wallet.

### Profile[#](broken-reference)

This tab displays the profile information of the Wallet owner.

Users can see their WebID, name, and profile picture (if set). A QR code is also provided which can be used to share the user’s WebID. Additionally, users can logout from this tab using the three-dots menu icon.

#### Sharing User’s Digital Identity[#](broken-reference)

The Wallet displays the user’s WebID as a QR code. This can be used to create an Access Request.

Applications can scan the QR code in order to obtain the WebID. Once they have the WebID they can locate the inbox associated with the Wallet and use this to create Access Requests for data stored within it. Access Requests must be approved by the Wallet holder before data can be accessed.



### Requests[#](broken-reference)

This tab shows all pending Access Requests the user has received for data inside the Wallet. From here, the user can view request details, such as requester, access mode, the name of the resource and the access expiry date. The user can choose to Confirm or Deny the request. If the user confirms, the requester will be granted the specified access mode (such as read or write) to the resource.



### Access[#](broken-reference)

This tab shows what access has been granted to other agents.

For each agent, there is a list of the Wallet resources they have been approved access. Users have the option to revoke access to specific resources, or revoke all access from the agent.

