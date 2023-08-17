# Studio overview

Ubit Studio is a DApp \(Decentralized App\) running on the Ethereum and Ubit networks. It allows anybody without technical knowledge to launch a community and integrate a token into it. With Ubit studio, a token is easily minted on Ethereum through a user friendly wizard. It's then moved through the bridge to the Ubit to add business and community features to it and manage it.

[![](../.gitbook/assets/you6.png) ](https://www.youtube.com/channel/UC7NaJ0UhmyHi5MvZSk61akA/videos?view_as=subscriber)

Via the DApp you can access the contracts and services of the Ubit network. You can launch your community on the Ubit network with a token bridged to Ethereum, intergate web3.0 services from the DeFi \(Decentralized Finance\) ecosystem. The community is upgraded by a variety of plugins that customize the community to your needs. It allows you to:

* Add to your community users, business, admins and more tailor made roles
* Define transfer and bonus rules for the community members
* Cover transaction costs for you customer
* Integrate a white label wallet
* Make bounties \(soon to come\)
* You can add your own plugins \(soon to come\)
* Local dapp store \(soon to come\)

The logic is defined by Ethereum compatible smart contracts and backend services that listen to the events on the blockchain. We prefer to use the Ubit chain for fast and cheap transactions, but some significant events necessarily happen on the Ethereum network, as a gateway to the whole Ethereum ecosystem. We do not own private user data, it is controlled by the user themselves, via 3box and stored in IPFS.

![Ubit Studio architecture](../.gitbook/assets/image%20%283%29.png)

## Backend Infrastructure

The backend is composed of the following independent services

* Studio API Backend has two purposes. Provides an API for fast and convenient querying of the blockchain data for the Studio DApp. Transmits heavy and complicated transaction flows on behalf of the user.
* Ubit-funder service used to fund community members and wallet users on the Ubit blockchain.
* Ubit IPFS proxy used for fast fetching and storing data in IPFS.

## Contracts

Ubit studio is designed to launch DeFi communities on the Ubit network. The community contract binds together most of the services and features of the Studio. Among other things it consists of:

* Entities List contract to store community members and their roles
* Community UBIT20 tokens on Ubit network with transfer rules
* UBIT20 tokens on Ethereum. This is the token that the user issues as part of the community deployment process
* [Multitoken bridge](https://github.com/fuseio/bridge-contracts) - to minimize friction and costs we extended the POA UBIT20-UBIT20 bridge contract to many-UBIT20-to-many contract.

## Plugins

The plugins are used to customize the community to your specific needs. These can be smart contracts, backend services or the integration of both. The currently available plugins are:

* Business List - allows you to add businesses to you community. Businesses are Entities List members with special roles.
* Join Bonus - define a join bonus for new community members.
* Fiat Ramp - Currently integrated to [Transak](https://transak.com/) and [Moonpay](https://www.moonpay.io/) to allow easy deposit and withdraw using Bank Accounts and Payment Cards.
* More plug-ins coming soon.

