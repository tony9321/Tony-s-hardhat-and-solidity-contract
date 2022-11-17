# this is a project I coded and the journey i learned to code Solidity smart contract, hardhat, JS, and it can be deploy on local node or testnet like rinkeby

Advanced Sample Hardhat Project

This project demonstrates an advanced Hardhat use case, integrating other tools commonly used alongside Hardhat in the ecosystem.

The project comes with a sample contract, a test for that contract, a sample script that deploys that contract, and an example of a task implementation, which simply lists the available accounts. It also comes with a variety of other tools, preconfigured to work with the project code.

Requirements:
git
You'll know you did it right if you can run git --version and you see a response like git version x.x.x
Nodejs
You'll know you've installed nodejs right if you can run:
node --versionand get an output like: vx.x.x
Yarn instead of npm
You'll know you've installed yarn right if you can run:
yarn --version And get an output like: x.x.x
You might need to install it with npm
If you're familiar with npx and npm instead of yarn, you can use npx for execution and npm for installing dependencies.

Run:
```
yarn add --dev @nomicfoundation/hardhat-toolbox @nomicfoundation/hardhat-network-helpers @nomicfoundation/hardhat-chai-matchers @nomiclabs/hardhat-ethers @nomiclabs/hardhat-etherscan chai ethers hardhat-gas-reporter solidity-coverage @typechain/hardhat typechain @typechain/ethers-v5 @ethersproject/abi @ethersproject/providers
```

Then:
```
yarn test
```

Try running some of the following tasks:

```shell
npx hardhat accounts
npx hardhat compile
npx hardhat clean
npx hardhat test
npx hardhat node
npx hardhat help
REPORT_GAS=true npx hardhat test
npx hardhat coverage
npx hardhat run scripts/deploy.js
node scripts/deploy.js
npx eslint '**/*.js'
npx eslint '**/*.js' --fix
npx prettier '**/*.{json,sol,md}' --check
npx prettier '**/*.{json,sol,md}' --write
npx solhint 'contracts/**/*.sol'
npx solhint 'contracts/**/*.sol' --fix
```

# Etherscan verification

To try out Etherscan verification, you first need to deploy a contract to an Ethereum network that's supported by Etherscan, such as Ropsten.

In this project, copy the .env.example file to a file named .env, and then edit it to fill in the details. Enter your Etherscan API key, your Ropsten node URL (eg from Alchemy), and the private key of the account which will send the deployment transaction. With a valid .env file in place, first deploy your contract:

```shell
hardhat run --network ropsten scripts/deploy.js
```

Then, copy the deployment address and paste it in to replace `DEPLOYED_CONTRACT_ADDRESS` in this command:

```shell
npx hardhat verify --network ropsten DEPLOYED_CONTRACT_ADDRESS "Hello, Hardhat!"
```

Usage
If you run npx hardhat --help you'll get an output of all the tasks you can run.

Deploying Contracts
```
npm run deploy
```
This will deploy your contracts to a local network. Additionally, if on a local network, it will deploy mock Chainlink contracts for you to interact with. If you'd like to interact with your deployed contracts, skip down to Interacting with Deployed Contracts.

Run a Local Network
One of the best ways to test and interact with smart contracts is with a local network. To run a local network with all your contracts in it, run the following:
```
npx hardhat node
```
You'll get a local blockchain, private keys, contracts deployed (from the deployment folder scripts), and an endpoint to potentially add to an EVM wallet.

Using a Testnet or Live Network (like Mainnet or Polygon)
In your hardhat.config.js you'll see section like:
```
module.exports = {
  defaultNetwork: "hardhat",
  networks: {
 ```
This section of the file is where you define which networks you want to interact with. You can read more about that whole file in the hardhat documentation.

To interact with a live or test network, you'll need:

An rpc URL
A Private Key
ETH & LINK token (either testnet or real)
Let's look at an example of setting these up using the Goerli testnet.

Test
Tests are located in the test directory, and are split between unit tests and staging/testnet tests. Unit tests should only be run on local environments, and staging tests should only run on live environments.

To run unit tests:
```
npx hardhat test
```
or
```
npm run test
```
or
```
yarn test
```

Performance optimizations
Since all tests are written in a way to be independent from each other, you can save time by running them in parallel. Make sure that AUTO_FUND=false inside .env file. There are some limitations with parallel testing, read more about them here

To run tests in parallel:
```
npx hardhat test --parallel
```
or
```
npm run test --parallel
```
Interacting with Deployed Contracts
After deploying your contracts, the deployment output will give you the contract addresses as they are deployed. You can then use these contract addresses in conjunction with Hardhat tasks to perform operations on each contract.

Chainlink Price Feeds
The Price Feeds consumer contract has one task, to read the latest price of a specified price feed contract
```
npx hardhat read-price-feed --contract insert-contract-address-here --network network
```
Request & Receive Data
The APIConsumer contract has two tasks, one to request external data based on a set of parameters, and one to check to see what the result of the data request is. This contract needs to be funded with link first:
```
npx hardhat fund-link --contract insert-contract-address-here --network network
```
Once it's funded, you can request external data by passing in a number of parameters to the request-data task. The contract parameter is mandatory, the rest are optional
```
npx hardhat request-data --contract insert-contract-address-here --network network
```
Once you have successfully made a request for external data, you can see the result via the read-data task
```
npx hardhat read-data --contract insert-contract-address-here --network network
```
[key]:https://hardhat.org/getting-started/
