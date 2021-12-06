# Sacred Coin Protocol V 0.1.0

## Table of Contents
* [Introduction](#1-introduction)
* [Readme Aim](#2-readme-aim)
* [How to Build a Sacred Coin](#3-how-to-build-a-sacred-coin)
* [How to Retrieve the Guidelines of a Sacred Coin](#4-how-to-retrieve-the-guidelines-of-a-sacred-coin)
* [Conclusion](#5-conclusion)



## 1. Introduction

A protocol to build an ERC20 token that allows for the creation of guidelines, 
or recommendations on how to use the coin that are intended for the those 
who interact with it.

## 2. Readme Aim
This readme is intended to provide a simple example of how to use the
main contract of the protocol, SacredCoin.sol, and how to interact with the
guidelines of the token once it is created.

For more information on the philosophy behind the protocol, visit
[the website](https://sacredcoinprotocol.com).

Additional information about the structure of the SacredCoin contract
can be found inside the contract itself.

## 3. How to build a Sacred Coin

Let's take the simplest example of a token built using the OpenZeppelin library,
and make it a sacred coin by adding some guidelines.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.2;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

//Check that this is right:
import "@sacred-coin-protocol/contracts/SacredCoin.sol"

contract MyToken is SacredCoin, ERC20 {
constructor() ERC20("MyToken", "MTK") {

createGuideline(
"Inform yourself on the Sacred Coin Protocol",
"Every person that interacts with this coin should seek to gain 
an in-depth understanding of the Sacred Coin Protocol")

createGuideline(
"Build the simplest version of a Sacred Coin",
"Every person that interacts with this coin should seek to build
a simple Sacred Coin that they think would do good for the world,
in order to learn more about how the Sacred Coin Protocol works."
}
}
```

And that's it! As you can see, building a sacred coin is as simple as:

1. Identifying the token as a SacredCoin as well as an ERC20 contract.
2. Calling the createGuideline function, and passing two strings - 
the first string is the guideline summary, and the second is the guideline 
itself.

## 4. How to retrieve the guidelines of a Sacred Coin

Once the token contract is deployed on the blockchain, a sacred coin's 
guidelines will  be available for anyone to retrieve in a number of ways:

### 4.1. By calling the returnSingleGuideline function with the index of the guideline you would like to return.

They are 0 indexed, and are in the order they were entered when they coin was constructed.
For example, calling returnSingleGuideline[0] will return the first guideline in MyToken as an array of two strings:

```
0: string: Inform yourself on the Sacred Coin Protocol.
1: string: Every person that interacts with this coin should seek to gain an in-depth understanding of the Sacred Coin Protocol.
```

### 4.2. By calling the returnAllGuidelines function.

Calling the returnAllGuidelines function will return an array of tuples,
each tuple containing a summary-guideline pair.

```
tuple(string,string)[]: Think of something to be grateful for.,Every time you buy, sell or otherwise use the coin, take a second to think of something that you are grateful for. It could be your family, your friends, the neighborhood you are living in or your pet tortoise. Ideally, you should think about something different that you're grateful for every time you use the coin.
```

This is the one that I've used for retrieving the guidelines of the 
[Gratitude Coin](https://sacredcoinprotocol.com/coins/gratitude_coin) for example,
in order to display it on its website, since it is very convenient to iterate over.

### 4.3. By calling the guidelines array

This is similar to 4.1. Guidelines are 0 indexed here as well, of course. The difference is that
this returns an object, rather than an array, and therefore have the "guideline" and the "summary" as keys.

### 4.4. Which method of retrieving the guidelines from the above should I use?

That depends entirely on your use case. The reason for having multiple ways of retrieving
the guidelines is so that you can choose the option that best fits your project.
There is no right way of doing it, and all of them are equally valid.

# 5. Conclusion
I hope that this short example gives you everything that you need to create your own
Sacred Coin.

If you have any questions or concerns, do not hesitate to contact me.
You can do so via [Discord](https://discord.gg/m3cNXWshRK).
