# ERC-7561: Simple NFT, Simplified ERC-721

### Abstract

This ERC is a new NFT asset designed based on the user contract wallet (including AA), and is forward compatible with ERC-721，to keep nft assets simple, this ERC removes some functions of ERC-721.

### Motivation

ERC-721 are Ethereum-based standard nft that can be traded and transferred on the Ethereum network. But the essence of ERC-721 is based on the EOA wallet design. EOA wallet has no state and code storage, and the smart contract wallet is different.

Almost all ERCs related to NFT are adding functions, our opinion is the opposite, we think the NFT contract should be simpler, more functions are taken care of by the smart contract wallet.

Our proposal is to design a simpler NFT asset based on the smart contract wallet,

It aims to achieve the following goals:

1. Keep the NFT contract simple, only need to be responsible for the transaction function
2. approve and allowance functions are not managed by the NFT contract , approve and getApproved should be configured at the user level instead of controlled by the nft contract, increasing the user's more playability , while avoiding part of the ERC-721 contract risk.
3. Remove the safeTransferFrom function, and a better way to call the other party's nft assets is to access the other party's own contract instead of directly accessing the nft asset contract.
4. Forward compatibility with ERC-721 means that all nft can be compatible with this proposal.

### Specification

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119 and RFC 8174.

Compliant contracts MUST implement the following interface:

```solidity
pragma solidity ^0.8.20;

/**
 * @title ERC7561 Simple nft interface 
 * @dev See https://ercs.ethereum.org/ERCS/erc-7561
 */
interface IERC7561 {
    /**
     * @notice Used to notify transfer nft.
     * @param from Address of the from
     * @param to Address of the receive
     * @param tokenId The transaction token id 
     */
    event Transfer(
        address indexed from,
        address indexed to,
        uint256 indexed tokenId
    );

    /**
     * @notice  Count all NFTs assigned to an owner
     * @param owner Address of the owner
     * @return The number of NFTs owned by `owner`, possibly zero
     */
    function balanceOf(address owner) 
        external
        view
        returns (uint256);

    /**
     * @notice Find the owner of an NFT
     * @param tokenId The identifier for an NFT
     * @return The address of the owner of the NFT
     */
    function ownerOf(uint256 tokenId) 
        external  
        view
        returns (address);
	  

    /**
     * @notice Transfer ownership of an NFT
     * @param from Address of the from
     * @param to Address of the to
     * @param tokenId The NFT to transfer
     */
    function transferFrom(address from, address to, uint256 tokenId) external;

}
```

### Rationale

The purpose of the proposal is to add a simple nft for Ethereum smart contract wallet. Token contracts are only responsible for transactions and define assets.

**Examples**

Judges whether the receiving address is safe (ERC-721, safeTransferForm),

ERC-721 Consecutive Transfer Extension(ERC-2309),

No Intermediary NFT Trading Protoco(ERC-6105),

authorizes the distribution of the user's own assets (ERC-721, approve, allowance) and many proposals based on ERC-721 extension

The above work should be handled by the user's smart contract wallet or wallet pulgin, rather than the nft contract itself.

### Backwards Compatibility

As mentioned in the beginning, this ERC is forward compatible with ERC-721, ERC-721 is backward compatible with this ERC. In order to support backward compatibility with ERC-721, we also mentioned backward compatible code in the Reference Implementation.

### Reference Implementation

**forward compatible with ERC-721**

```solidity
pragma solidity ^0.8.20;

import "./IERC7561.sol";
import "../../math/SafeMath.sol";

/**
 * @title Standard ERC7561 nft
 * @dev Note: the ERC-165 identifier for this interface is 0xc1b31357
 * @dev Implementation of the basic standard nft.
 */
contract ERC7561 is IERC7561 {

    // Token name
    string private _name;

    // Token symbol
    string private _symbol;

    mapping(uint256 tokenId => address) private _owners;

    mapping(address owner => uint256) private _balances;

    uint256 private _totalSupply;

    function totalSupply() external view returns (uint256) {
        return _totalSupply;
    }

    function balanceOf(address owner) public view  returns (uint256) {
        require (owner != address(0));
        
        return _balances[owner];
    }

    function ownerOf(uint256 tokenId) public view  returns (address) {
        return _requireOwned(tokenId);
    }


    function transferFrom(address from, address to, uint256 tokenId) public  {

        require(from == msg.sender);

        require (to != address(0) );

        address previousOwner = _update(to, tokenId);

        require(previousOwner == from);
    }


    function _ownerOf(uint256 tokenId) internal view virtual returns (address) {
        return _owners[tokenId];
    }

    function _requireOwned(uint256 tokenId) internal view returns (address) {
        address owner = _ownerOf(tokenId);
        require(owner != address(0));
            
        return owner;
    }

    function _update(address to, uint256 tokenId) internal virtual returns (address) {
        address from = _ownerOf(tokenId);

        
        // Execute the update
        if (from != address(0)) {         

            unchecked {
                _balances[from] -= 1;
            }
        }

        if (to != address(0)) {
            unchecked {
                _balances[to] += 1;
            }
        }

        _owners[tokenId] = to;

        emit Transfer(from, to, tokenId);

        return from;
    }

}
```

### Security Considerations

It should be noted that this ERC is not backward compatible with ERC-721, so there will be incompatibility with existing dapps.

### Copyright

Copyright and related rights waived via CC0.
