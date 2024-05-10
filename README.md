# Ink! XVM SDK

This repository contains examples contracts using XVM to call EVM from ink! needed to use XVM from WASM contracts.
It contains an implementation of XVM chain-extension to use in your contracts.
As well as ink! contracts SDK that implements XVM chain-extension to be used as is.

## Reference: 
This repo code is copied initially from the repos below
https://github.com/realtakahashi/ink-xvm-sdk
https://github.com/AstarNetwork/ink-xvm-sdk

## Steps
#### 1. Download a Substrate node with both EVM and Ink contract pallet
e.g. Astar https://github.com/AstarNetwork/Astar/releases
Then run it: `./astar-collator  --dev --tmp`

https://docs.astar.network/docs/build/environment/local-network/
Configure Metamask to use:
Name: Astar
URL: http://127.0.0.1:9944
ChainID: 4369 Astar
Currency Symbol: ASTL

#### 2. Deploy the Storage EVM Solidity contract via Remix connecting to the local node from step1: 
The Storage contract is located at `./solidity/Storage.sol`

#### Install `Cargo contract` inside a repo without rust toolchain:
`cargo install --version 3.2.0 cargo-contract`
`cargo contract --version`
... cargo contract version is 3.2.0, good for my Wasm Ink! 4.3.0 version

#### Compile wrapper wasm contract:
`cargo contract build --manifest-path PATH_TO_XVM_FOLDER/Cargo.toml`
... this should succeed with the following:
  - store_xvm.contract (code + metadata)
  - store_xvm.wasm (the contract's code)
  - store_xvm.json (the contract's metadata)

#### Use https://ui.use.ink/ to deploy the compiled wasm with the already deployed Solidity contract address from above

Then I got `Contract Reverted! DispatchError: DecodingFailed Input passed to a contract API function failed to decode as expected type...`


#### Reference: 
https://substrate.stackexchange.com/questions/11435/xvm-ink-wasm-to-evm-contract-reverted-decoding-failed

https://medium.com/astar-network/cross-virtual-machine-creating-a-portal-to-the-future-of-smart-contracts-a96c6d2f79b8

https://theastarbulletin.news/how-to-implement-a-contract-using-xvm-1c94d2072c30

https://docs.astar.network/docs/learn/interoperability/xvm/#interfaces

Code are copied from https://github.com/realtakahashi/ink-xvm-sdk and https://github.com/AstarNetwork/ink-xvm-sdk