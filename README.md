# SOLANA-DISCORD-NFT-VERIFICATION

Simple app to verify Solana NFTs on a discord server. It consists of two parts which are React Web3 App and a discord bot written with DiscordJS. The react app can be used seperately without the discord bot if preferred.

# Prerequisites

## Moralis
This app is built with Moralis and its SOLANA API to handle the authentication, get the user's NFTs and to get the metadata of the NFTs to do the verification. You need to sign up to Moralis, set up a server and get your `Application ID` and `Server URL` which are totally free to do. [You can follow these instructions](https://docs.moralis.io/moralis-server/getting-started/create-a-moralis-server).

## Discord Bot
You need to create a discord application from discord's developer portal, invite your bot to your server and get the Bot's secret token. [How to get your token](https://techbriefly.com/2021/12/30/how-to-get-a-discord-bot-token/).

# Getting Started

First install the dependencies
```javascript
npm run install-all
```
then you can run the app concurrently with
```javascript
npm run dev
```
or to run the discord bot and the UI seperately you can run
```javascript
npm start
```
in both directories seperately.

Then run the following command from discord to open up an interaction for your users to verify their NFTs
```
!verifyNFT
```

# Configuration

## React Web3 App
### .env
Change the name of `.env.example` file into `.env` and fill in the fields.
```
REACT_APP_MORALIS_APP_ID=<Your Moraliss APP_ID>
REACT_APP_MORALIS_SERVER_URL=<Your Moralis Server URL>
```
### config.json
```javascript
{
    "updateAuthority": "<updateAuthority of the nft to be verified>",
    "network" : "<mainnet or devnet>"
    "discordURL": <URL of discord server> (eg. http://localhost:9090/)
}
``` 


## Discord
Change the name of `.env.example` file into `.env` and fill in the fields.
```
TOKEN=<Bot TOKEN>
APP_URL=<URL of React App> (eg. http://localhost:3000/)
CHANNEL_NAME=<Name of the discord channel where verified user's will be announced with their NFTs>
```
# Important
Currently this app uses only one updateAuthority to check if an NFT is from a certain collection. However, some collections may have more than one updateAuthority. Therefore, to be able to use this app in production if your collection requires more than one updateAuthority, you have the following options:

1) You can change a few lines of codes to compare more than one updateAuthority. You may have to gather all of those update authorities of a collection. If you are verifying your own nft collection you already have them.  
2) If you have the candyMachineID of the collection you can use [Solana-Web3.js Library](https://docs.solana.com/developing/clients/javascript-api) to get all NFTs from a certain collection with the candyMachineID. [This may help](https://stackoverflow.com/questions/70597753/how-to-find-all-nfts-minted-from-a-v2-candy-machine/70601874#70601874).

# Contribution
There may be some bugs and there are many things that could be improved and features that could be added. Please feel free to fork the repository and send pull requests or open up issues. 
