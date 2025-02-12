---
icon: wrench
---

# Installation

### Prerequisites[#](broken-reference)

To build and test the Data Wallet you will need the following installed:

* [Git](https://git-scm.com/),
* [Node and NPM](https://nodejs.org/),
* [Expo Go](https://expo.dev/go) - install this app on your mobile phone for on-device testing,
* A [PodSpaces account](https://start.inrupt.com/profile?utm_campaign=Data%20Wallet%20PodSpaces\&utm_source=docs-page).

### Getting Started[#](broken-reference)

In this tutorial, we will walk you through configuring and setting up your project to test on a physical device using Expo Go.

#### What You Will Achieve[#](broken-reference)

By working through this guide, you will:

1. Install the project dependencies.
2. Establish a correctly configured development environment.
3. Successfully install your project into the Expo Go app on your device.
4. Celebrate your accomplishment with a well-deserved coffee break.

#### Install Dependencies[#](broken-reference)

First, clone the [project](https://github.com/openwallet-foundation-labs/solid-data-wallet) and install dependencies using NPM.

```
$ git clone https://github.com/openwallet-foundation-labs/solid-data-wallet
$ cd solid-data-wallet
$ npm ci
```

#### Configuration and Setup[#](broken-reference)

**Configure Build Environment**[**#**](broken-reference)

Copy the contents of `.env.sample` file into `.env`. Only two of these variables are relevant to this tutorial as they define the backend Wallet Services the Wallet will connect to:

```
EXPO_PUBLIC_LOGIN_URL=https://datawallet.inrupt.com/oauth2/authorization/wallet-app
EXPO_PUBLIC_WALLET_API=https://datawallet.inrupt.com
```

**Running in Expo**[**#**](broken-reference)

To start Expo, run the following command:

At this point you could open emulators for specific platforms but for the purposes of this tutorial, use the platform-independent Expo Go environment.

After Expo has started, make sure it targets the Expo Go environment (as opposed to “development build”). This will display a QR code which you will need to scan with your device.

The Wallet application will then build and install into your device for you to test.

**Taking this further**[**#**](broken-reference)

If you are ready to start making changes to the Wallet you will need to use more advanced configuration and tooling. This is described in detail in the [Wallet repository](https://github.com/openwallet-foundation-labs/solid-data-wallet).
