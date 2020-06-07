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
        "chainId": 538969607,
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

$ geth --networkid 538969607 --rpcvhosts=* --syncmode full  --datadir path/to/datadir --cache 1024 --maxpeers 1000  --port 30305 --rpcapi net,eth,web3,personal --rpc --rpcaddr 127.0.0.1  --rpcport 30306

if you need to personal.unlockAccount or eth.sendTransaction etc, add --allow-insecure-unlock

$ geth --allow-insecure-unlock

## add peers

$ geth attach path/to/datadir/geth.ipc

> admin.addPeer("enode://00782da883ffb25a6f978d198c2f8d90f4aab32718ba8dc979fa5588c49a6dedc8930ebfe94cb31c4a399da0139cd6180882db61afb8f46e6afa007eefcac89e@47.112.235.61:30305")
> admin.addPeer("enode://905f3e4e67360e205c310b833105a520d8d81d8af649ad117bfbd33e49ce80fc066cd1ba9f0d43e4480d4432cc0198b8aa6fcfd69dd5c0e742aa37a74c3aa46c@47.112.253.125:30305")






