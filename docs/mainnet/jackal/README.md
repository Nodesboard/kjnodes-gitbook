# Services

<figure><img src="https://raw.githubusercontent.com/kj89/testnet_manuals/main/pingpub/logos/jackal.png" width="150" alt=""><figcaption></figcaption></figure>

The Jackal Protocol is a fast, scalable, and secure blockchain that empowers  individuals, developers, and enterprises to increase their data privacy and  cybersecurity posture without sacrificing ease of use. This protocol strives  to offer world-class applications to protect the planet's most important data–your data.

**Chain ID**: jackal-1 | **Latest Version Tag**: v1.1.2-hotfix | **Wasm**: ON

[Website](https://jackalprotocol.com) | [Discord](https://discord.com/invite/5GKym3p6rj) | [Twitter](https://twitter.com/Jackal_Protocol)

## Restake

[Restake with kjnodes](https://restake.app/jackal/jklvaloper1tr3wm3mdkz0tda6t7vavqnn7fe2g4un0f67xmt) (every day at 08:00, 20:00)
## Public endpoints

* rpc: [https://jackal.rpc.kjnodes.com](https://jackal.rpc.kjnodes.com)
* api: [https://jackal.api.kjnodes.com](https://jackal.api.kjnodes.com)

## Peering

**state-sync**

```
d9bfa29e0cf9c4ce0cc9c26d98e5d97228f93b0b@jackal.rpc.kjnodes.com:37656
```

**seed-node**

```
400f3d9e30b69e78a7fb891f60d76fa3c73f0ecc@jackal.rpc.kjnodes.com:37659
```

**addrbook**
```
curl -Ls https://snapshots.kjnodes.com/jackal/addrbook.json > $HOME/.canine/config/addrbook.json
```

**live-peers** (10)
```
peers="68205c025ec65bf4d4183691d19d15b0a72221ec@65.108.42.185:26656,e5a142be860ee9b2f5c71d813e39fceb12cbd218@78.46.78.83:26686,0985977a794b298e7ef990fe344d572c60c453b1@172.105.72.158:26656,d9abd1dd5bf7c57461f0476c61e28bac879430a2@141.94.109.71:10556,108652f503665772ad024d9d2129a9f4fa9ffe9b@176.9.98.24:30536,a2afb42b65da7013eca54778ce01dfb877c2a82a@154.12.227.132:37656,d9bfa29e0cf9c4ce0cc9c26d98e5d97228f93b0b@65.109.88.38:37656,7751d16cfa48da0a5bea6f40e9bcc386b4c76c50@51.89.7.184:26638,7574e0ab179fc6cc47ac89284f4641790218540e@18.163.165.245:26626,173c43436e2287f3660c344a5fd2386da4a61968@65.109.92.241:11126"
sed -i 's|^persistent_peers *=.*|persistent_peers = "'$peers'"|' $HOME/.canine/config/config.toml
```
