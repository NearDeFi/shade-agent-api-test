# Shade Agent API Test

This repo is the most simple example of a docker app that can test the Shade Agent API docker image and CLI tool.

## Installation

```
yarn
```

Create `.env.development.local` in root.

## Env Vars

Note:

-   Proxy Contract == local development e.g. yarn dev/start and testing against shade-agent-api running on your machine (NOT A TEE)
-   Sandbox Contract == remote deployment to Phala Cloud, running in a TEE

```bash
# get this from cargo-near or near-cli-rs
NEAR_ACCOUNT_ID=...
NEAR_SEED_PHRASE="..." # will need quotes around seed phrase
# ac-proxy is running locally so you can use yarn dev/start and test your app against the locally running shade agent api
NEXT_PUBLIC_contractId=ac-proxy.[NEAR_ACCOUNT_ID (from above)]
# including this will give you a fixed account every time, remove for production use as each TEE should boot with a new ephemeral NEAR account ID
ENTROPY=foobar
# do not change the api codehash, this is the shade-agent-api
API_CODEHASH=1ca34018bc387177d648376db7f86e09ee650421df0513d77ed5fe90d0e87b4d
# SANDBOX: this will update automatically each time you deploy to Phala with a new image of your app pushed to docker hub
APP_CODEHASH=e25f360bca7ebc6822536d9af2ce926582277e54f37e8c0855bccbf74aac1731
# SANDBOX: what is the docker tag of your app? used for sandbox deployments on Phala
DOCKER_TAG=mattdlockyer/shade-agent-api-test
# SANDBOX: you will need your own Phala API KEY
PHALA_API_KEY=...
```

## Running

```bash
# in Terminal 1
shade-agent-js
# in Terminal 2
yarn start
```

## Test the Endpoints

-   http://localhost:3000/api/address
-   http://localhost:3000/api/test-sign
