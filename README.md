# Personal Tokens's Smart Contracts [![Build Status](https://travis-ci.org/PersonalTokens/solidity.svg?branch=master)](https://travis-ci.org/PersonalTokens/solidity)

This repository hosts source code of on-chain part of [Personal Tokens](https://personaltokens.io).
All smart contracts are located in the contracts folder.
Snapshots of [OpenZeppelin](https://github.com/OpenZeppelin/openzeppelin-solidity) dependencies are located in OpenZeppelin subdirectory.

## Development

Requirements:

 * [Node.js](https://nodejs.org/en/)
 * [git](https://git-scm.com/download/)

Setup:

 1. install truffle: `npm install -g truffle`
 2. clone the repository: `git clone https://github.com/PersonalTokens/solidity.git`
 3. change into the root directory: `cd solidity`
 4. install all Node.js requirements from package.json: `npm install`

### Migrating and testing with truffle develop

 * run: `truffle develop`
 * compile: `compile`
 * migrate: `migrate`
 * run tests: `test`

## Contracts

### Contract `PersonalToken`

ERC20 compatible token contract, see [wiki for documentation](https://theethereum.wiki/w/index.php/ERC20_Token_Standard).

### Contract `Treasurer`

Contract responsible for paying out tokens kept by `TreasurerWallet`.

#### Events

` event Withdrawal(address token, address to, uint256 value, bytes signature)`

#### Methods

`function withdraw(ERC20Basic _token, address _to, uint256 _value, uint _timestamp, bytes _signature) public onlyValidSignatureAndData(_signature)`

### Contract `TreasurerWallet`

Contract for keeping tokens.

#### Events

`event Withdrawal(address token, address to, uint256 value)`

#### Modifiers

`modifier onlyTreasurer()`

#### Methods

`function setTreasurer(address _treasurer) public onlyOwner`

`function migrate(address _wallet, ERC20Basic[] _tokens) public onlyOwner`

`function withdraw(ERC20Basic _token, address _to, uint256 _value) public onlyTreasurer`

#### Public Variables

`address public treasurer;`

## About Personal Tokens

[Personal Tokens](https://personaltokens.io) is a platform where you can easily verify and tokenize yourself. We are building an infrastructure for the new emerging economy based on privately issued tokens backed with real people. Using an incentive structure build into tokens we incentivise people to build the value of their own tokens.
We are aiming to build a robust and decentralized platform as possible. Our goal is to deliver as many tools as tokenized people need and to make the token economy as user friendly as possible.

## License

    Copyright (c) 2018 Trifinity.io

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.