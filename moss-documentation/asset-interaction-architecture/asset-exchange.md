# Asset Exchange

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
