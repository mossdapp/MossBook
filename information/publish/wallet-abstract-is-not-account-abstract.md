# Wallet Abstract - is not Account Abstract

First of all, we have to understand that accounts and wallets have always been two things, but the initial development of blockchain made everyone think they are the same concept.

I think Wallet Abstraction include Asset management abstraction, payment abstraction, Identity abstraction.

In real life, a wallet is an item or tool used to store, manage, and conduct currency transactions. Its meaning includes the following aspects:

1. **Currency Storage and Management**: A wallet is where people store notes, coins, and other forms of currency. It allows individuals to carry a certain amount of cash with them at all times in order to cover daily expenses and purchase goods and services(like erc20).
2. **Payment Instruments**: Wallets typically include credit cards, debit cards, and other payment cards that enable individuals to make electronic payments. These cards can be used with POS terminals, ATM machines and other devices to facilitate shopping and cash withdrawals (like different token trasfer,approve).
3. **Personal Items and Photos**: Some people keep family photos, small keepsakes, or other personal items in their wallets to carry with them and display(like nft).
4. **Identity Verification and Personal Information**: Wallets usually contain important identity and personal information proof documents such as personal ID cards, driving licenses, membership cards, and health cards. These documents are used for identity verification and proof of personal identity when required(like did).

The same is true in WEB2，This is WeChat, with screenshots of its account, wallet UI.\
The picture on the left is like the existing AA function, and the right is the wallet function, so the account abstraction and wallet abstraction should be completely **different** function and UI.

[![微信截图\_20231117012107](https://ethresear.ch/uploads/default/optimized/2X/7/713f344f7c20c35d8059216ad27c2a8482fd8829\_2\_516x499.jpeg)微信截图\_20231117012107944×914 130 KB](https://ethresear.ch/uploads/default/original/2X/7/713f344f7c20c35d8059216ad27c2a8482fd8829.jpeg)

The wallets and accounts we designed are all in the form of plug-ins(own dapp), but the wallet mainly implements these functions.

**Asset Manage(include all ERC20 & ERC721)**\
Assets, **Approve**, Legacies are genuinely managed by user wallets.

**Payment**\
Abstracted payments, customized payment, blacklists

**Identification Info**\
Verification of identity information and personal information.

We transfer all token management functions and transaction functions to the wallet plug-in itself，as plug-in, it can support more customized functions and improve security.
