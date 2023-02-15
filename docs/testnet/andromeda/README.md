# Services

<figure><img src="https://raw.githubusercontent.com/kj89/testnet_manuals/main/pingpub/logos/andromeda.png" width="150" alt=""><figcaption></figcaption></figure>

Andromeda is an application platform layer that connects all  public blockchains in the Cosmos ecosystem. Through our vast  library of no-code smart contracts, users can harness the power of web3.

**Chain ID**: galileo-3 | **Latest Version Tag**: galileo-3-v1.1.0-beta1 | **Wasm**: OFF

[Website](https://www.andromedaprotocol.io) | [Discord](https://discord.gg/andromeda) | [Twitter](https://twitter.com/andromedaprot)




## Chain explorer
[https://explorer.kjnodes.com/andromeda-testnet](https://explorer.kjnodes.com/andromeda-testnet)

## Public endpoints

* api: [https://andromeda-testnet.api.kjnodes.com](https://andromeda-testnet.api.kjnodes.com)
* rpc: [https://andromeda-testnet.rpc.kjnodes.com](https://andromeda-testnet.rpc.kjnodes.com)
* grpc: [https://andromeda-testnet.grpc.kjnodes.com](https://andromeda-testnet.grpc.kjnodes.com)

## Peering

**state-sync**

```text
d5519e378247dfb61dfe90652d1fe3e2b3005a5b@andromeda-testnet.rpc.kjnodes.com:47656
```

**seed-node**

```text
3f472746f46493309650e5a033076689996c8881@andromeda-testnet.rpc.kjnodes.com:47659
```

**addrbook**
```bash
curl -Ls https://snapshots.kjnodes.com/andromeda-testnet/addrbook.json > $HOME/.andromedad/config/addrbook.json
```

**live-peers** (10)
```bash
peers="c5f6021d8da08ff53e90725c0c2a77f8d65f5e03@195.201.195.40:26656,39627f2386fe19679396314966febf9827fbed46@195.201.147.57:60656,dfa4155254cf862fbd411b9e02e26ecb00cd2436@85.10.198.171:26456,df7cf95427701d6d00797042fb8548a7f8eeeb6e@172.104.159.69:55716,72bba2142c9cada7e4b8e861fb79e8a66e345d99@95.217.236.79:50656,d5519e378247dfb61dfe90652d1fe3e2b3005a5b@65.109.68.190:47656,5b5438c8e0dbf7783c47b8cd41ca4eb8a4caa006@185.209.31.45:46656,8cac168380851851b9318a2176dca8fb690e26d2@95.216.7.169:36656,e95899eb682e517d74449dd575073daf1a3266d5@135.181.208.169:27656,247f3c2bed475978af238d97be68226c1f084180@88.99.164.158:4376"
sed -i -e "s|^persistent_peers *=.*|persistent_peers = \"$peers\"|" $HOME/.andromedad/config/config.toml
```