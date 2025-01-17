
# <b>  DEXagna, an Autonomous Market Maker </b> 

This DEX was created during the Solidity Encode Bootcamp as a final project. This version of the DEX is deployed on rinkeby.

DEXagna is inspired by [Solidly](https://github.com/solidlyexchange/solidly) and [Uniswap V2](https://github.com/Uniswap/v2-core).

The aim of DEXagna is to provide a solution that meets the needs of all users:
* LP
* people who swap
* protocols who want liquidity for their token

DEXagna has a specific tokenomics mechanism ($LASA) (improvement of Solidly and Velodrome). 


#  <b>  Smart Contracts</b> 

`dexagna-core` is mostly inspired by uniswap-v2-core.
`dexagna-periphery` is mostly inspired by uniswap-v2-periphery.


## <b> fees distribution</b> 
The fees do not go into the liquidity pool pair like in uniswap V2. Instead the fees from all the pools are going into a specific smart contract. 

In solidly, for each pool, the fees go inside the `BaseV1Fees` contract and people can claim the fees. Each `BaseV1Fees` receives only the fees of the specific liquidity pool to which it is linked. A new `BaseV1Fees` is created by a base pair pool (`BaseV1Pair`) everytime a base pair pool is created, and `BaseV1Pair` are created by the factory contract.

In DEXagna, the `GlobalBaseV1Fees` contract recieves all the fees from all the pools and it is created by the factory contract (and not the pair contracts). The `GlobalBaseV1Fees` contract receives the fees in the token which was used for the swap.

## <b> Fees claims and $LASA token (Version 0 for testing)</b> 

### <b> $LASA token given to Liquidity Providers </b> 
For the moment, each LP get 100,000 $LASA token. (The amount is not important for the moment because in order to claim the fees, people just need to hold $LASA). In the future, the fee claimed will be based on the amount of $LASA tokens the holder has.


### <b> claiming the fees </b> 

In version 0, only $LASA token holders can claim the amount they want of fees (they need to specify a token and an amount) thanks to `claimFeesFor` function of GlobalBaseV1Fees.


### <b>  Things to be improved </b> 
* for the moment, everyone can mint $LASA token. Need to bring some requirements into the mint (only pair pool addresses can mint).
* LPs need to get a specific amount of $LASA based on the amount of liquidity they bring
* the fee claim should be linked to the amount of tokens the person has
* Allow for weekly fee claims only

# Deployment of the smart contracts
Check the README from the two different folders in order to see how to deploy the contracts
* `/dexagna-core` 
* `/dexagna-periphery`


# Frontend
At least two frontend UIs needed:
* Swap
* Liquidity Provider details (_we need to agree on what features to add here_)


# Backend


