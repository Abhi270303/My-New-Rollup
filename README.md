# Arbitrum Nitro Rollup Contracts

This is the package with the smart contract code that powers Arbitrum Nitro and Espresso integration.
It includes the rollup and fraud proof smart contracts, as well as interfaces for interacting with precompiles.



## Deploy contracts to Sepolia

### 1. Compile contracts

Compile these contracts locally by running

```bash
git clone https://github.com/offchainlabs/nitro-contracts
cd nitro-contracts
yarn install
yarn build
yarn build:forge
```

### 2. Setup environment variables and config files

Copy `.env.sample.goerli` to `.env` and fill in the values. Add an [Etherscan api key](https://docs.etherscan.io/getting-started/viewing-api-usage-statistics), [Infura api key](https://docs.infura.io/dashboard/create-api) and a private key which has some funds on sepolia.
This private key will be used to deploy the rollup. We have already deployed a `ROLLUP_CREATOR_ADDRESS` which has all the associated espresso contracts initialized.

If you want to deploy your own rollup creator, you can leave the `ROLLUP_CREATOR_ADDRESS` empty and follow the steps on step 3.

If you want to use the already deployed `RollupCreator`, you can update the `ROLLUP_CREATOR_ADDRESS` with the address of the deployed rollup creator [here](espresso-deployments/sepolia.json) and follow the steps on step 4 to create the rollup.

### 3. Deploy Rollup Creator and initialize the espresso contracts

Run the following command to deploy the rollup creator and initialize the espresso contracts.

`npx hardhat run scripts/deployment.ts --network sepolia`

This will deploy the rollup creator and initialize the espresso contracts.

## Shell Output

```
Deploying contracts with maxDataSize: 104857
env var ESPRESSO_LIGHT_CLIENT_ADDRESS not set, it needs to be set to deploy the RollupCreator for the espresso integration
* New Bridge created at address: 0x6A68F6B80C559BF22CBc69A28F4155c8483B6806 
Successfully submitted source code for contract
src/bridge/Bridge.sol:Bridge at 0x6A68F6B80C559BF22CBc69A28F4155c8483B6806
for verification on the block explorer. Waiting for verification result...

Successfully verified contract Bridge on the block explorer.
https://sepolia.arbiscan.io/address/0x6A68F6B80C559BF22CBc69A28F4155c8483B6806#code

Verified contract Bridge successfully.
* New SequencerInbox created at address: 0x743146fB366295a70F8F88A34077A7F4cF9a755c 104857 0x0000000000000000000000000000000000000000 false
Successfully submitted source code for contract
src/bridge/SequencerInbox.sol:SequencerInbox at 0x743146fB366295a70F8F88A34077A7F4cF9a755c
for verification on the block explorer. Waiting for verification result...

Successfully verified contract SequencerInbox on the block explorer.
https://sepolia.arbiscan.io/address/0x743146fB366295a70F8F88A34077A7F4cF9a755c#code

Verified contract SequencerInbox successfully.
* New Inbox created at address: 0xF60C918658DEb3C85A313F69eC99AA5475cb4AF9 104857
Successfully submitted source code for contract
src/bridge/Inbox.sol:Inbox at 0xF60C918658DEb3C85A313F69eC99AA5475cb4AF9
for verification on the block explorer. Waiting for verification result...

Successfully verified contract Inbox on the block explorer.
https://sepolia.arbiscan.io/address/0xF60C918658DEb3C85A313F69eC99AA5475cb4AF9#code

Verified contract Inbox successfully.
* New RollupEventInbox created at address: 0x8B5367b515Bd80e36EF710f41ebEb504EC2d3072 
Successfully submitted source code for contract
src/rollup/RollupEventInbox.sol:RollupEventInbox at 0x8B5367b515Bd80e36EF710f41ebEb504EC2d3072
for verification on the block explorer. Waiting for verification result...

Successfully verified contract RollupEventInbox on the block explorer.
https://sepolia.arbiscan.io/address/0x8B5367b515Bd80e36EF710f41ebEb504EC2d3072#code

Verified contract RollupEventInbox successfully.
* New Outbox created at address: 0x205AB04bc591F65f674C6171557Eb492c597Caf3 
Successfully submitted source code for contract
src/bridge/Outbox.sol:Outbox at 0x205AB04bc591F65f674C6171557Eb492c597Caf3
for verification on the block explorer. Waiting for verification result...

Successfully verified contract Outbox on the block explorer.
https://sepolia.arbiscan.io/address/0x205AB04bc591F65f674C6171557Eb492c597Caf3#code

Verified contract Outbox successfully.
* New ERC20Bridge created at address: 0xa728ae448017e57aec95e2b254f22fCe90475c6D 
Successfully submitted source code for contract
src/bridge/ERC20Bridge.sol:ERC20Bridge at 0xa728ae448017e57aec95e2b254f22fCe90475c6D
for verification on the block explorer. Waiting for verification result...

Successfully verified contract ERC20Bridge on the block explorer.
https://sepolia.arbiscan.io/address/0xa728ae448017e57aec95e2b254f22fCe90475c6D#code

Verified contract ERC20Bridge successfully.
* New SequencerInbox created at address: 0x1281b185C76F16977C1e9e133cC0aaE8D69c2173 104857 0x0000000000000000000000000000000000000000 true
Successfully submitted source code for contract
src/bridge/SequencerInbox.sol:SequencerInbox at 0x1281b185C76F16977C1e9e133cC0aaE8D69c2173
for verification on the block explorer. Waiting for verification result...

Successfully verified contract SequencerInbox on the block explorer.
https://sepolia.arbiscan.io/address/0x1281b185C76F16977C1e9e133cC0aaE8D69c2173#code

Verified contract SequencerInbox successfully.
* New ERC20Inbox created at address: 0xD3f719a5758cF629d8B17cf11841b573F0972C8b 104857
Successfully submitted source code for contract
src/bridge/ERC20Inbox.sol:ERC20Inbox at 0xD3f719a5758cF629d8B17cf11841b573F0972C8b
for verification on the block explorer. Waiting for verification result...

Successfully verified contract ERC20Inbox on the block explorer.
https://sepolia.arbiscan.io/address/0xD3f719a5758cF629d8B17cf11841b573F0972C8b#code

Verified contract ERC20Inbox successfully.
* New ERC20RollupEventInbox created at address: 0x2A4b4e38e069356f8a595D20b3B32c03C61F3908 
Successfully submitted source code for contract
src/rollup/ERC20RollupEventInbox.sol:ERC20RollupEventInbox at 0x2A4b4e38e069356f8a595D20b3B32c03C61F3908
for verification on the block explorer. Waiting for verification result...

Successfully verified contract ERC20RollupEventInbox on the block explorer.
https://sepolia.arbiscan.io/address/0x2A4b4e38e069356f8a595D20b3B32c03C61F3908#code

Verified contract ERC20RollupEventInbox successfully.
* New ERC20Outbox created at address: 0x54a0Fb9104274Fc3fAF8fE4c6788442d8997C28C 
Successfully submitted source code for contract
src/bridge/ERC20Outbox.sol:ERC20Outbox at 0x54a0Fb9104274Fc3fAF8fE4c6788442d8997C28C
for verification on the block explorer. Waiting for verification result...

Successfully verified contract ERC20Outbox on the block explorer.
https://sepolia.arbiscan.io/address/0x54a0Fb9104274Fc3fAF8fE4c6788442d8997C28C#code

Verified contract ERC20Outbox successfully.
* New BridgeCreator created at address: 0x27aa8707eFDe6d3Aa22CDFA4E3a3247176cAbbD8 0x6A68F6B80C559BF22CBc69A28F4155c8483B6806,0x743146fB366295a70F8F88A34077A7F4cF9a755c,0xF60C918658DEb3C85A313F69eC99AA5475cb4AF9,0x8B5367b515Bd80e36EF710f41ebEb504EC2d3072,0x205AB04bc591F65f674C6171557Eb492c597Caf3 0xa728ae448017e57aec95e2b254f22fCe90475c6D,0x1281b185C76F16977C1e9e133cC0aaE8D69c2173,0xD3f719a5758cF629d8B17cf11841b573F0972C8b,0x2A4b4e38e069356f8a595D20b3B32c03C61F3908,0x54a0Fb9104274Fc3fAF8fE4c6788442d8997C28C
Successfully submitted source code for contract
src/rollup/BridgeCreator.sol:BridgeCreator at 0x27aa8707eFDe6d3Aa22CDFA4E3a3247176cAbbD8
for verification on the block explorer. Waiting for verification result...

Contract BridgeCreator is already verified.
network block skew detected; skipping block events (emitted=133693486 blockNumber133694495)
* New OneStepProver0 created at address: 0x59B8852d9a0528F9c7530B0A7269aaa8561F9083 
Successfully submitted source code for contract
src/osp/OneStepProver0.sol:OneStepProver0 at 0x59B8852d9a0528F9c7530B0A7269aaa8561F9083
for verification on the block explorer. Waiting for verification result...

Contract OneStepProver0 is already verified.
* New OneStepProverMemory created at address: 0xB651EA181a0326F7E7d5DED19bBD197368521DC5 
Successfully submitted source code for contract
src/osp/OneStepProverMemory.sol:OneStepProverMemory at 0xB651EA181a0326F7E7d5DED19bBD197368521DC5
for verification on the block explorer. Waiting for verification result...

Contract OneStepProverMemory is already verified.
* New OneStepProverMath created at address: 0xA889f0E369661B01fD2648bE05291123E775670A 
Successfully submitted source code for contract
src/osp/OneStepProverMath.sol:OneStepProverMath at 0xA889f0E369661B01fD2648bE05291123E775670A
for verification on the block explorer. Waiting for verification result...

Contract OneStepProverMath is already verified.
* New OneStepProverHostIo created at address: 0x4090470fC4296B3e8f4e2DFE2D3F53E3cf2b7332 
Successfully submitted source code for contract
src/osp/OneStepProverHostIo.sol:OneStepProverHostIo at 0x4090470fC4296B3e8f4e2DFE2D3F53E3cf2b7332
for verification on the block explorer. Waiting for verification result...

Contract OneStepProverHostIo is already verified.
network block skew detected; skipping block events (emitted=133695033 blockNumber133696648)
* New OneStepProofEntry created at address: 0xD1f140baD1593a6713580A912D17869e891742a9 0x59B8852d9a0528F9c7530B0A7269aaa8561F9083 0xB651EA181a0326F7E7d5DED19bBD197368521DC5 0xA889f0E369661B01fD2648bE05291123E775670A 0x4090470fC4296B3e8f4e2DFE2D3F53E3cf2b7332
Successfully submitted source code for contract
src/osp/OneStepProofEntry.sol:OneStepProofEntry at 0xD1f140baD1593a6713580A912D17869e891742a9
for verification on the block explorer. Waiting for verification result...

Contract OneStepProofEntry is already verified.
* New ChallengeManager created at address: 0xE7a344C3f0B316d7BA6E9895bECA0E61FDFC95dA 
Verification for ChallengeManager failed with the following error: More than one contract was found to match the deployed bytecode.
Please use the contract parameter with one of the following contracts:
  * src/challenge/ChallengeManager.sol:ChallengeManager
  * src/mocks/SingleExecutionChallenge.sol:SingleExecutionChallenge

For example:

hardhat verify --contract contracts/Example.sol:ExampleContract <other args>

If you are running the verify subtask from within Hardhat instead:

await run("verify:verify", {
<other args>,
contract: "contracts/Example.sol:ExampleContract"
};
* New RollupAdminLogic created at address: 0x7eF7d114e7CBEBFc7454FA77B4DE731b4992655d 
Successfully submitted source code for contract
src/rollup/RollupAdminLogic.sol:RollupAdminLogic at 0x7eF7d114e7CBEBFc7454FA77B4DE731b4992655d
for verification on the block explorer. Waiting for verification result...

Successfully verified contract RollupAdminLogic on the block explorer.
https://sepolia.arbiscan.io/address/0x7eF7d114e7CBEBFc7454FA77B4DE731b4992655d#code

Verified contract RollupAdminLogic successfully.
* New RollupUserLogic created at address: 0x8Dd26f3dBa7b7Eb5583c7613493512447145ae2D 
Successfully submitted source code for contract
src/rollup/RollupUserLogic.sol:RollupUserLogic at 0x8Dd26f3dBa7b7Eb5583c7613493512447145ae2D
for verification on the block explorer. Waiting for verification result...

Successfully verified contract RollupUserLogic on the block explorer.
https://sepolia.arbiscan.io/address/0x8Dd26f3dBa7b7Eb5583c7613493512447145ae2D#code

Verified contract RollupUserLogic successfully.
network block skew detected; skipping block events (emitted=133697595 blockNumber133698715)
* New ValidatorUtils created at address: 0x957911718F5ebaca652eD4EB83Bfe88f76Ee8408 
Successfully submitted source code for contract
src/rollup/ValidatorUtils.sol:ValidatorUtils at 0x957911718F5ebaca652eD4EB83Bfe88f76Ee8408
for verification on the block explorer. Waiting for verification result...

Contract ValidatorUtils is already verified.
* New ValidatorWalletCreator created at address: 0xee237ee13034E11FF44211b31ecA8C27618B5017 
Successfully submitted source code for contract
src/rollup/ValidatorWalletCreator.sol:ValidatorWalletCreator at 0xee237ee13034E11FF44211b31ecA8C27618B5017
for verification on the block explorer. Waiting for verification result...

Contract ValidatorWalletCreator is already verified.
* New RollupCreator created at address: 0xD4f9d691427F63945293627Fc068828492555892 
Successfully submitted source code for contract
src/rollup/RollupCreator.sol:RollupCreator at 0xD4f9d691427F63945293627Fc068828492555892
for verification on the block explorer. Waiting for verification result...

Contract RollupCreator is already verified.
network block skew detected; skipping block events (emitted=133699278 blockNumber133700283)
* New DeployHelper created at address: 0x8fBD2163636375D2d1C3Bae3DCf16102aE89172f 
Successfully submitted source code for contract
src/rollup/DeployHelper.sol:DeployHelper at 0x8fBD2163636375D2d1C3Bae3DCf16102aE89172f
for verification on the block explorer. Waiting for verification result...

Contract DeployHelper is already verified.
* New RollupProxy created at address: 0x1603C080be99c003E3e3D77a6860236d8ad3Ce09 
Successfully submitted source code for contract
src/rollup/RollupProxy.sol:RollupProxy at 0x1603C080be99c003E3e3D77a6860236d8ad3Ce09
for verification on the block explorer. Waiting for verification result...

Contract RollupProxy is already verified.
Contract addresses are saved in the deployments folder
Waiting for the Template to be set on the Rollup Creator
Template is set on the Rollup Creator
```

### 4. Create the rollup

Change the `config.ts.example` to `config.ts` and update the config specific to your rollup. Then run the following command to create the rollup if you haven't already done so.

`npx hardhat run scripts/createEthRollup.ts --network sepolia`

## Shell Output

```
Calling createRollup to generate a new rollup ...
Congratulations! 🎉🎉🎉 All DONE! Here's your addresses:
RollupProxy Contract created at address: 0xc9A884B4F5440fc00730A52ab48a8e0Db8b30784
Wait a minute before starting the contract verification
Attempting to verify Rollup contract at address 0xc9A884B4F5440fc00730A52ab48a8e0Db8b30784...
Successfully submitted source code for contract
src/rollup/RollupProxy.sol:RollupProxy at 0xc9A884B4F5440fc00730A52ab48a8e0Db8b30784
for verification on the block explorer. Waiting for verification result...

Contract RollupProxy is already verified.
Inbox (proxy) Contract created at address: 0x0EB750129705fAfec85B0b1BF17B3c8bA3504602
Outbox (proxy) Contract created at address: 0xe0ab3B11A815694D10cEF72b2C83e69DA40b970b
rollupEventInbox (proxy) Contract created at address: 0x9A5d9529EA514aA6e2906d805A830e276D7a8CC8
challengeManager (proxy) Contract created at address: 0x3e055dA6a69a7568E764f10Ef27e1D778D251540
AdminProxy Contract created at address: 0xC283b1D0f97F118E9E226955BC1aAcbD5362D915
SequencerInbox (proxy) created at address: 0xeb27AAA4352E4389dA4f8794dE2B4A8d40513171
Bridge (proxy) Contract created at address: 0x7350E74Fa151f62e08107B21E332788e3B953c63
ValidatorUtils Contract created at address: 0x957911718F5ebaca652eD4EB83Bfe88f76Ee8408
ValidatorWalletCreator Contract created at address: 0xee237ee13034E11FF44211b31ecA8C27618B5017
All deployed at block number: 133701818
```

## Deployed contract addresses

Deployed contract addresses can be found in the [espress-deployments folder](./espresso-deployments/).

## License

Nitro is currently licensed under a [Business Source License](./LICENSE.md), similar to our friends at Uniswap and Aave, with an "Additional Use Grant" to ensure that everyone can have full comfort using and running nodes on all public Arbitrum chains.

The Additional Use Grant also permits the deployment of the Nitro software, in a permissionless fashion and without cost, as a new blockchain provided that the chain settles to either Arbitrum One or Arbitrum Nova.

For those that prefer to deploy the Nitro software either directly on Ethereum (i.e. an L2) or have it settle to another Layer-2 on top of Ethereum, the [Arbitrum Expansion Program (the "AEP")](https://docs.arbitrum.foundation/assets/files/Arbitrum%20Expansion%20Program%20Jan182024-4f08b0c2cb476a55dc153380fa3e64b0.pdf) was recently established. The AEP allows for the permissionless deployment in the aforementioned fashion provided that 10% of net revenue is contributed back to the Arbitrum community in accordance with the requirements of the AEP.
