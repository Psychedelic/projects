# Internet Computer Improvement Proposal

Principal ID’s as Universal Identifiers

## Summary

We propose a standard for using Principal ID’s as the universal unique identifier for the Internet Computer, instead of using Account ID’s, Wallet ID’s, User ID’s, or any other additional unique identifier that is currently being used for ICP, tokens, apps, cycles, etc.. Furthermore this proposal aims to establish an alternative approach to user identity/authentication on the Internet Computer that moves away from the hostname specific Principal ID’s currently being used by Internet Identity, and instead optimizes/caters more to the Web3/crypto/token/composability side of the Internet Computer ecosystem by following the Web3 identity/auth/UX patterns users are already familiar with. 

## Motivation

One of the great parts about Ethereum is that all a user needs is a wallet address and they can do anything/everything they want, and all their assets/activity can be seamlessly surfaced in a user-centric, interface agnostic way. Users (and apps) only ever have to worry about that 1 unique identifier (the wallet/account address). The simplicity avoids confusion/frustration/lock-in, and also makes it very easy on developers to build around. Also one of the biggest benefits of this approach is the composability it brings to the Ethereum platform, where apps can permissionlessly integrate smart contracts, and users can go interface to interface and ‘bring their account’ to each one and choose whichever interface they prefer to interact with their assets/contracts and perform the actions they want. This creates a 10x better user experience vs. the app specific account paradigm of Web2 (and of Internet Identity). 

### Current Issues Preventing the Above on the Internet Computer

There are two main issues. 


1. The Internet Computer currently has several different unique identifiers that are being used across the platform for different purposes
2. Internet Identity is not suitable for Web3/crypto/token/composability type use cases

**1)** The Internet Computer currently has several different unique identifiers that are being used across the platform for different purposes

Principal ID’s are what own/control canisters. However they currently can’t hold ICP or cycles. 



*   **ICP** is held by account ID’s (a separate unique identifier in addition to Principal ID’s). Account ID’s only exist within the ICP ledger canister, they don’t exist anywhere else on the Internet Computer. 
*   **Cycles** can only be held by canisters, not Principal ID’s. 

The issue with this approach is that with account ID’s, now users need to worry about 2 unique identifiers (Principal ID & Account ID). Plus you can only send/receive ICP to Account ID’s, so it creates a confusing user experience when sending/receiving ICP. Our fear is that if other tokens follow in the ICP’s footsteps and associate token balances with Account ID’s, it will create a poor user experience for Internet Computer users. **<span style="text-decoration:underline;">Our recommendation would instead be for tokens to associate balances directly with Principal ID’s</span>**. We think the benefits of doing so greatly outweigh the cons (especially when compared to the pros/cons of using account ID’s). 

**2)** Internet Identity is not suitable for Web3/crypto/token/composability type use cases

While Internet Identity is an awesome identity/auth option for Web2 type apps that are more siloed, we feel it falls short in many areas, and is essentially unusable for Web3 type apps (ex. crypto, DeFi, tokens, aggregators, etc.). This is mainly because of the following Internet Identity design decisions that lead to the following issues:



*   Hostname Specific Principal ID’s 
*   Removal of the Target field 
*   No ability for users to use same Principal ID’s across apps
*   No easy composability across apps (ex. the Principal ID’s of two different apps don’t map to one another)
*   Service worker required to auth each user/session. And user needs to re-auth themselves each session across each app (for example, imagine switching between uniswap, sushiswap, 1inch, etc. using Internet Identity and how that experience would compare to the current experience of doing it on Ethereum with metamask)
*   Token balances become interface specific
*   Users would need to transfer token balances in between interfaces in order to use them for example in DeFi 
*   Apps are all required to build UI around surfacing token balances, sending/receiving tokens, signing messages/transaction, etc. 
*   Full interface lock-in. Significant trust must be placed on the interface

These issues, coupled with issue #1, create an incredibly complex and convoluted landscape for both Internet Computer users and developers. 

## Solution



1. Associate everything with Principal ID’s
    *   With emerging Token Standards, we feel all tokens going forward should use Principal ID’s to associate user balances. 
    *   With Dank (dank.ooo), users can now associate ICP & Cycles with Principal ID’s. 
2. Introduce alternative to Internet Identity for Web3/token/crypto type apps/use cases
    *   With Plug (plug.ooo), users will have a metamask like experience where they can hold ICP, cycles, and other tokens, and sign into IC apps with just a principal ID. 
    *   Similar to metamask, users can generate multiple Principal ID’s, and choose which Principal ID’s they want to associate with each app, and easily switch between them
    *   Similar to metamask, Plug will be super easy for IC apps to integrate, and will eliminate the burden on apps to create their own UI around balances, sending/receiving, signing transactions, etc. 
    *   The goal is that overtime other wallets and solutions like Plug will emerge creating a vibrant ecosystem of options for users to choose from (ex. similar to like Wallet Connect on Ethereum)
