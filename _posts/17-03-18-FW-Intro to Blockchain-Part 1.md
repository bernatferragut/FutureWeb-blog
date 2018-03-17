---
layout: post
title: "FW - Intro to Blockchain - Part 1"
description: "How to create a Blockchain with JS - Foundation"
date: 2018-03-15
tags: [design, future web, creative coding, cryptos]
comments: true
share: true
---

![blockchain-1](https://user-images.githubusercontent.com/17754060/37556920-454c3c50-29d3-11e8-9566-a8c09920351d.jpg)

# How to Build your own BlockChain with Javascript

> This Article will be technical. I will comment the code explaining each of the parts as well as I can. Follow the steps and enjoy the creation of a simple blockchain. Let's lay a good foundation, let's code, let's create a blockchain.

## BlockChain creation - Foundation

> 1. Load the npm library crypto-js where we can find all the encryption functions, like the sha256

```javascript
const SHA256 = require('crypto-js/sha256');
```

> 2. Create a BLOCK with the following properties: Index, timeStamp, data, previousHash and hash.

```javascript
class Block {
    constructor(index, timeStamp, data, previousHash='') {
        this.index = index;
        this.timeStamp = timeStamp;
        this.data = data;
        this.previousHash = previousHash;
        this.hash = this.calculateHash();
    }
    // We use sha256 to encrypt the whole Block
    calculateHash() {
        return SHA256(this.index + this.timeStamp + this.previousHash + JSON.stringify(this.data)).toString();
    }
}
```

> 3. Create a CHAIN or a list of BLOCKS

```javascript
class BlockChain {
    constructor(){
        this.chain = [this.createGenesisBlock()];
    }
    // We must define the first block or genesis Block
    createGenesisBlock() {
        return new Block(0, "03/03/2018", 'Genesis Block', '0');
    }

    getLatestBlock() {
        return 'The latest Block created is: ' + this.chain[this.chain.length-1];
    }

    addBlock(newBlock) {
        // We link the new Block hash with the lates Block to create a chain
        newBlock.previousHash = this.getLatestBlock().hash;
        newBlock.hash = newBlock.calculateHash();
        this.chain.push(newBlock);
    }
    // We validate the chain
    isChainValid() {
        for(let i=1; i < this.chain.length; i++) {
            const currentBlock = this.chain[i];
            const previousBlock = this.chain[i-1];
            if(currentBlock.hash !== currentBlock.calculateHash()) {
                return false;
            }
            if(currentBlock.previousHash !== previousBlock.hash) {
                return false;
            }
            return true;
        }
    }
}
```

> 4. We test the chain creating a new Blockchain and trying to hack it

```javascript
let bernieCoin = new BlockChain();
bernieCoin.addBlock(new Block(1, '03/03/2018', { amount: 4 }));
bernieCoin.addBlock(new Block(2, '04/03/2018', { amount: 9 }));

// Hacking the data
bernieCoin.chain[1].data = {amount: 10};
console.log('is bernieCoin valid? => ' + isChainValid());
return false
// Hack the hash
bernieCoin.chain[1].hash = bernieCoin.calculateHash();
console.log('is bernieCoin valid? => ' + isChainValid());
return false
console.log(JSON.stringify(bernieCoin, null, 2));
```

> 5. And the JSON version of the created BRLOCKCHAIN

```javascript
{
  "chain": [
    {
      "index": 0,
      "timeStamp": "03/03/2018",
      "data": "Genesis Block",
      "previousHash": "0",
      "hash": "85f48d2a2607aeb3001bbd7eacdaf2f0ac4ed0f174abcd6fbcd3baedf55f53b0"
    },
    {
      "index": 1,
      "timeStamp": "03/03/2018",
      "data": {
        "amount": 4
      },
      "hash": "418d3eecfc757e05b9cfc40ffd7cee9fd6e07157e9a30e8ad5d3b4f6f298f89f"
    },
    {
      "index": 2,
      "timeStamp": "04/03/2018",
      "data": {
        "amount": 9
      },
      "hash": "dab874818dd386cdbfba1ba9b34f0303a63143a02273ec93f4c00fd68aa7ca5f"
    }
  ]
}
```

## GITHUB REPO

> [GITHUB Repo: BLOCKCHAIN-part1](https://github.com/bernatferragut/BlockChain)
