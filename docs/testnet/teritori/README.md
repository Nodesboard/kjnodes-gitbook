# Services

<figure><img src="https://raw.githubusercontent.com/kj89/cosmos-images/main/logos/teritori.png" width="150" alt=""><figcaption></figcaption></figure>

Teritori is a multi-chain hub designed to allow IBC and non IBC communities  to connect, trade services & NFTs, launch new projects & build further existing ones.

**Chain ID**: teritori-testnet-v3 | **Latest Version Tag**: v1.3.1 | **Wasm**: ON

[Website](https://teritori.com) | [Discord](https://discord.gg/teritori) | [Twitter](https://twitter.com/TeritoriNetwork)



Subscribe to our free [🤖 Testnet Proposal Bot](https://t.me/kjnodes_testnet_proposal_bot) to never miss upcoming proposals


## Chain explorer
[https://explorer.kjnodes.com/teritori-testnet](https://explorer.kjnodes.com/teritori-testnet)

## Public endpoints

* api: [https://teritori-testnet.api.kjnodes.com](https://teritori-testnet.api.kjnodes.com)
* rpc: [https://teritori-testnet.rpc.kjnodes.com](https://teritori-testnet.rpc.kjnodes.com)
* grpc: teritori-testnet.grpc.kjnodes.com:19090

## Peering

**state-sync**

```text
d5519e378247dfb61dfe90652d1fe3e2b3005a5b@teritori-testnet.rpc.kjnodes.com:19656
```

**seed-node**

```text
3f472746f46493309650e5a033076689996c8881@teritori-testnet.rpc.kjnodes.com:19659
```

**addrbook**
```bash
curl -Ls https://snapshots.kjnodes.com/teritori-testnet/addrbook.json > $HOME/.teritorid/config/addrbook.json
```

**live-peers** (21)
```bash
peers="a97eb7a4f3d857f1ff82265d2905fc0762a6bfd4@135.125.5.31:54256,6bc9f80a5123d62c23aadb7b5d68b740a794b0c6@207.180.194.156:36656,5ae1012f9b0f4672d8152de903d115dd2f1a3ee3@65.21.170.3:27656,303666c503cd27161529692de701f5b2d3a2f043@65.109.23.114:15956,31413c99357d0cfc48a46767ade171db2ea0205e@135.181.138.160:46656,d5519e378247dfb61dfe90652d1fe3e2b3005a5b@65.109.68.190:19656,3614bc766d73bebf6b73737b6690af60e7f0683e@65.108.206.118:46656,ec0c58dbfe67a12ea16951134e29a6566ac05add@185.217.125.98:26656,07d196ccefcadc548c6cd06cfea425f1544b1495@213.239.217.52:41656,b6640a6b6062be34a0b5eedb0524c320f31959ef@65.108.234.26:28656,e1b331c1f3cba509960c65d6c6bc9b49532bcbaa@65.109.85.170:27656,4ebfdac0d496be2407c02202e5ad6f226a11b37a@65.21.134.202:26736,427f9547e1e2f2b62b269dc4d32efa6d946e9746@65.21.200.54:32656,c195935295e3429dbd50f155b9a3540b02cbc4d3@65.109.92.240:26656,c56b132be41b247c9f8fa1f2addaca57f9946e29@75.119.159.159:44656,b33ebb4672f929dddde1365c9678a39abfd881fb@54.202.144.51:26656,bf100c1b6b44a6e96ab5691f3023cec3c27747fd@144.126.142.78:46656,b9bd31a2a68a09d324a9deaf41144ff6d0dbe260@65.108.192.123:15656,15dd94f68c450da2c3b7c60b6364e3dce6f0cbf2@185.193.66.68:26641,ec8faa221a99f5c6d8f647cd08f60f2ace0ed1e2@65.109.112.20:11044,e78cee0e46927e483212e0313a35da6cc9151ed5@65.109.28.219:15956"
sed -i -e "s|^persistent_peers *=.*|persistent_peers = \"$peers\"|" $HOME/.teritorid/config/config.toml
```
