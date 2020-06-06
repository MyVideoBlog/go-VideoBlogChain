## Go Ethereum

Official Golang implementation of the Ethereum protocol.

[![API Reference](
https://camo.githubusercontent.com/915b7be44ada53c290eb157634330494ebe3e30a/68747470733a2f2f676f646f632e6f72672f6769746875622e636f6d2f676f6c616e672f6764646f3f7374617475732e737667
)](https://godoc.org/github.com/ethereum/go-ethereum)
[![Go Report Card](https://goreportcard.com/badge/github.com/ethereum/go-ethereum)](https://goreportcard.com/report/github.com/ethereum/go-ethereum)
[![Travis](https://travis-ci.org/ethereum/go-ethereum.svg?branch=master)](https://travis-ci.org/ethereum/go-ethereum)
[![Discord](https://img.shields.io/badge/discord-join%20chat-blue.svg)](https://discord.gg/nthXNEv)

Automated builds are available for stable releases and the unstable master branch. Binary
archives are published at https://geth.ethereum.org/downloads/.

## Building the source

For prerequisites and detailed build instructions please read the [Installation Instructions](https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum) on the wiki.

Building `geth` requires both a Go (version 1.13 or later) and a C compiler. You can install
them using your favourite package manager. Once the dependencies are installed, run

```shell
make geth
```

or, to build the full suite of utilities:

```shell
make all
```




## genesis.json

```json
{
    "config": {
        "chainId": 538969378,
        "homesteadBlock": 0,
        "daoForkBlock": 0,
        "daoForkSupport": false,
        "eip150Block": 0,
        "eip155Block": 0,
        "eip158Block": 0,
        "byzantiumBlock": 0,
        "constantinopleBlock": 0,
        "petersburgBlock": 0,
        "ethash": {}
    },
    "nonce": "0x0000000000000042",
    "timestamp": "0x0",
    "extraData": "0x11bbe8db4e347b4e8c937c1c8370e4b5ed33adb3db69cbdb7a38e1e50b1b82fa",
    "gasLimit": "0x989680",
    "difficulty": "0x100000",
	"mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
	"coinbase": "0x0000000000000000000000000000000000000000",
	"parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
	"signature": "0xd8776c53bea76d14983a61b8c170fb6fdf020996a32d32f56082db210d6abe904c1c6e1fe98b215566f364aa5defcb996ac31d5386f4142c5b774d8de4e9016800",
    "alloc": {
        "834d078f39a8799e5c8611843befd8538ddb049c": {
            "balance": "0x8af7623fb67bf000000000"
        }
    }
}
```
## Running `geth`

With the genesis state defined in the above JSON file, you'll need to initialize every geth node with it prior to starting it up to ensure all blockchain parameters are correctly set:

$ geth --datadir path/to/datadir init path/to/genesis.json

$ geth --networkid 538969378 --rpcvhosts=* --syncmode full  --datadir path/to/datadir --cache 1024 --maxpeers 1000  --port 30303 --rpcapi net,eth,web3,personal --rpc --rpcaddr 127.0.0.1  --rpcport 30304

if you need to personal.unlockAccount or eth.sendTransaction etc, add --allow-insecure-unlock

$ geth --allow-insecure-unlock

## add peers

$ geth attach path/to/datadir/geth.ipc

> admin.addPeer("enode://879bbe45613aadc2946c4bc868e648f7452364ec855b95d6da37d76c8a33975345607fbf6a8c63e60269f4c51dd0c7a64ebef1d4decb4ae32ec672b770ced8bb@47.112.235.61:30305")
> admin.addPeer("enode://0d37054dddfa4073507370e3f0389a439dd7b47d708fcac85c9de0a97f66d430babd9ccd8da05bae1a71be7c31dbcf4df6303f06d208ecb54574cb845b2006ea@47.112.253.125:30305")






