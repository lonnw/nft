# How to Create an NFT
## Disclaimer: Most of the content has been copied. A few areas have been edited for the custom audience

This tutorial will walk you through writing and deploying a Non Fungible (ERC721) Token smart contract using Ethereum and Inter Planetary File System (IPFS).

## Step 1: Connect to the Ethereum network
There a bunch of ways to make requests to the Ethereum blockchain, but to make things easiest, we’ll use a free account on [Alchemy](https://www.alchemy.com/), a blockchain developer platform and API that allows us to communicate with the Ethereum chain without having to run our own nodes.

In this tutorial, we'll also take advantage of Alchemy's developer tools for monitoring and analytics to understand what’s going on under the hood in our smart contract deployment.

## Step 2: Create your app (and API key)
Once you’ve created an Alchemy account, you can generate an API key by creating an app. This will allow us to make requests to the Polygon Mumbai test network

   1. Navigate to the “Create App” page in your Alchemy Dashboard by hovering over “Apps” in the nav bar and clicking “Create App”
    
   2. Name your app (we chose "poly-nft"), offer a short description, choose “Polygon” for the chain and choose “Polygon Mumbai” for your network.
    
   3. Click “Create app” and that’s it! Your app should appear in the table below.
  
## Step 3: Create an Ethereum account (address)
We need an Ethereum account to send and receive transactions. For this tutorial, we’ll use Metamask, a virtual wallet in the browser used to manage your Ethereum account address. If you want to understand more about how transactions on Ethereum work, check out [this page](https://ethereum.org/en/developers/docs/transactions/) from the Ethereum foundation.

You can download and create a Metamask account for free [here](https://metamask.io/download/). When you are creating an account, or if you already have an account, make sure to switch over to the “Goerli Test Network” in the upper right (so that we’re not dealing with real money).

## Step 4: Add ether from a Faucet
In order to deploy our smart contract to the test network, we’ll need some fake Eth. To get Eth you can go to the [Polygon faucet](https://faucet.polygon.technology/) and enter your Polygon account address, then click “Submit.” You should see MATIC in your Metamask account soon after!

## Step 6: Initialize our project
First, we’ll need to create a folder for our project. Navigate to your command line and type:
```bash
> mkdir my-nft
> cd my-nft
```
Now that we’re inside our project folder, we’ll use npm init to initialize the project. If you don’t already have npm installed, follow [these instructions](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) (we’ll also need Node.js, so download that too!).
```bash
npm init
```
It doesn’t really matter how you answer the installation questions, here is how we did it for reference:
```bash
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (afro-nft)
version: (1.0.0)
description:
entry point: (index.js)
test command:
git repository:
keywords:
author:
license: (ISC)
About to write to C:\Users\USER\Documents\polygon_projects\afro-nft\package.json:

{
  "name": "afro-nft",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


Is this OK? (yes)
```
Approve the package.json, and we’re good to go!

## Step 7: Download Hardhat
Hardhat is a development environment to compile, deploy, test, and debug your Ethereum software. It helps developers when building smart contracts and dApps locally before deploying to the live chain.

Navigate to the terminal and make sure you're inside the my-nft project folder, then run:
```bash
npm install --save-dev hardhat
```
## Step 8: Create Hardhat project
Inside our project folder run:
```bash
npx hardhat
```
You should then see a welcome message and option to select what you want to do. Select “create an empty hardhat.config.js”:
```bash
888    888                      888 888               888
888    888                      888 888               888
888    888                      888 888               888
8888888888  8888b.  888d888 .d88888 88888b.   8888b.  888888
888    888     "88b 888P"  d88" 888 888 "88b     "88b 888
888    888 .d888888 888    888  888 888  888 .d888888 888
888    888 888  888 888    Y88b 888 888  888 888  888 Y88b.
888    888 "Y888888 888     "Y88888 888  888 "Y888888  "Y888

Welcome to Hardhat v2.12.0

√ What do you want to do? · Create an empty hardhat.config.js
Config file created

Give Hardhat a star on Github if you're enjoying it!

     https://github.com/NomicFoundation/hardhat
```
This will generate a hardhat.config.js file for us which is where we’ll specify all of the set up for our project (on step 13).

## Step 9: Add project folders
