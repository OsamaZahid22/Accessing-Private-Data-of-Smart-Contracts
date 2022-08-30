# Accessing Private Data From Smart Contracts

When building a smart contract we have to  visibility modifiers like public, private, etc. we may think that if you want some variable's value to be readable by the public you need to declare it public, and that private variables cannot be read by anyone but the smart contract itself. But, Ethereum is a public blockchain. So what does private data even mean?

## What does private mean?

Function (and variable) visibility modifiers only affect the visibility of the function - and do not prevent access to their values. We know that public functions are those which can be called both externally by users and smart contracts, and also by the smart contract itself.

Similarly, internal functions are those which can only be called by the smart contract itself, and outside users and smart contracts cannot call those functions. external functions are the opposite, where they can only be called by external users and smart contracts, but not the smart contract that has the function itself.

private, similarly, just affects who can call that function. private and internal behave mostly similarly, except the fact that internal functions are also callable by derived contracts, whereas private functions are not.

So for example, if Contract A has a function f() which is marked internal, a second Contract B which inherits Contract A like

``` bash
contract B is A {
  ...
}
```
can still call f().

However, if Contract A has a function g() which is marked private, Contract B cannot call g() even if it inherits from A.

The same is true for variables, as variables are basically just functions. private variables can only be accessed and modified by the smart contract itself, not even derived contracts. However, this does not mean that external parties cannot read the value.


## Code Overview
A simple contract, along with a Hardhat Test, to demonstrate this. Our contract will attempt to store data in private variables hoping that nobody will be able to read it's value.

The contract will take in password and username in its contructor and will store them in private variables.User will somehow be able to access those private variables.

## Resource Article
[cryptomarketpool](https://cryptomarketpool.com/access-private-data-on-the-eth-blockchain/)
