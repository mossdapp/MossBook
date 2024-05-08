# First Principles: Value Internet, Good Asset Interaction Architecture



### Asset Interaction

Whether virtual or real, all asset interactions are based on a secure environment. Our discussion is based on the premise of blockchain.

#### Active Asset Transfer

For example: Alice transferring assets to Bob. This involves three roles: owner Alice, asset token, and recipient Bob.

How to ensure that there are no obstacles on the way of Alice transferring assets and that they can be successfully transferred to Bob?

```
   --> Blockchain-based ERC20, ERC721, and programmable assets ensure the security of asset transfers.

```

Shortcomings:

For example, Alice cannot manage how to transfer to and receive from others, such as limiting the amount she can transfer at a time, checking if the receiving address is a black hole contract address, or if the address belongs to a blacklist.

New solution:

Alice manages how to transfer using the MOSS asset management module, which provides the interface for asset transfer.

#### Authorized Asset Extraction

For example: Bob requesting asset extraction from Alice.

This involves three roles: owner Alice, asset token, and requester Bob.

How to ensure that Bob can successfully receive the assets?

* \-> Blockchain-based ERC20, ERC721, also provide asset authorization functionality.

Shortcomings:

Alice cannot manage how to give and under what conditions, who can receive, and how many types of assets can be received. This should be decided by Alice herself, using her programmable wallet and programmable assets responsible for secure transfers.

New solution:

Alice manages how to authorize asset extraction, using the MOSS asset management module, which provides the interface for asset authorization management.

#### Asset Exchange

For example: Alice wants to exchange assets with Bob. This involves whether intermediaries or mediators are required.

Intermediary: Emphasizes the coordinating role in various relationships and transactions, participating in asset management.

Mediator: Specifically refers to channels used to convey information and content, only providing information.

This involves five roles:

Buyer, seller, trading assets x↔y, trading medium, trading intermediary (token exchange).

|                                      | Buyer | Seller                                                   | Trading Intermediary              | Trading Medium                       | Trading Asset |
| ------------------------------------ | ----- | -------------------------------------------------------- | --------------------------------- | ------------------------------------ | ------------- |
| Uniswap                              | √     | Uniswap LP                                               | Uniswap smart contract            | Uniswap frontend                     | ERC20↔ERC20   |
| Metamask Swap                        | √     | LP from multiple Dex                                     | Aggregates multiple Dex platforms | MetaMask wallet                      | ERC20↔ERC20   |
| MOSS user dex module                 | √     | MOSS user                                                | None                              | MOSS user frontend module            | ERC20↔ERC20   |
| MOSS aggregated dex trading platform | √     | LP from multiple Dex and all MOSS users                  | Optional                          | MOSS aggregated dex trading platform | ERC20↔ERC20   |
| Opensea                              | √     | Seller entrusts to Opensea                               | Opensea smart contract            | Opensea frontend                     | ERC721↔ERC20  |
| Blur                                 | √     | Seller entrusts to multiple NFT platforms                | Aggregates multiple NFT platforms | Blur frontend                        | ERC721↔ERC20  |
| MOSS user nft market module          | √     | MOSS user                                                | None                              | MOSS user frontend module            | ERC721↔ERC20  |
| MOSS aggregated nft market platform  | √     | Seller entrusts to multiple NFT platforms and MOSS users | Optional                          | MOSS aggregated nft market           | ERC721↔ERC20  |

Existing model shortcomings:

For asset interaction, it is necessary to go through an intermediary platform, authorize the intermediary, and some intermediaries also require providing asset liquidity to exchange assets. Each intermediary or LP pair requires a transaction fee.

In the absence of MOSS, buyers, sellers, and intermediary liquidity providers are not programmable and do not have states.

From a security perspective, the trading items, trading media, and trading intermediaries should be open-source and non-upgradeable.

New solution:

MOSS provides a solution without intermediaries and with aggregated media. Under the premise
