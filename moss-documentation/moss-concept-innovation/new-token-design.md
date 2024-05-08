# New Token Design

## New Token Design

ERC20 tokens are Ethereum-based standard tokens that can be traded and transferred on the Ethereum network. But the essence of ERC20 is based on the EOA wallet design. EOA wallet has no state and code storage, and the smart contract wallet is different.

Almost all ERCs related to tokens are adding functions, our opinion is the opposite, we think the token contract should be simpler, more functions are taken care of by the smart contract wallet.

Our proposal is to design a simpler token asset based on the smart contract wallet,

It aims to achieve the following goals:

1. Keep the asset contract simple, only need to be responsible for the transaction function
2. approve and allowance functions are not managed by the token contract , approve and allowance should be configured at the user level instead of controlled by the asset contract, increasing the user’s more playability , while avoiding part of the ERC20 contract risk.
3. Remove the transferForm function, and a better way to call the other party’s token assets is to access the other party’s own contract instead of directly accessing the token asset contract.
4. Forward compatibility with ERC20 means that all fungible tokens can be compatible with this proposal.

**Examples**

The third party calls the user’s token transaction`(transferForm)`,

Judges whether the receiving address is safe `(safeTransferForm)`,

Permit extension for signed approvals `(ERC-2612,``permit)`

Authorizes the distribution of the user’s own assets`(approve, allowance)`,

Add the transfer hook function. `(ERC-777, hook)`

The above work should be handled by the user’s smart contract wallet, rather than the token contract itself.
