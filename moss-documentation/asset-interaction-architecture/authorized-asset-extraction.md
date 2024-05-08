# Authorized Asset Extraction

#### Authorized Asset Extraction

For example: Bob requesting asset extraction from Alice.

This involves three roles: owner Alice, asset token, and requester Bob.

How to ensure that Bob can successfully receive the assets?

* \-> Blockchain-based ERC20, ERC721, also provide asset authorization functionality.

Shortcomings:

Alice cannot manage how to give and under what conditions, who can receive, and how many types of assets can be received. This should be decided by Alice herself, using her programmable wallet and programmable assets responsible for secure transfers.

New solution:

Alice manages how to authorize asset extraction, using the MOSS asset management module, which provides the interface for asset authorization management.
