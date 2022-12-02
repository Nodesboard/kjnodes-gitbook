# Services

<figure><img src="https://raw.githubusercontent.com/kj89/testnet_manuals/main/pingpub/logos/jackal.png" width="150" alt=""><figcaption></figcaption></figure>

The Jackal Protocol is a fast, scalable, and secure blockchain that empowers  individuals, developers, and enterprises to increase their data privacy and  cybersecurity posture without sacrificing ease of use. This protocol strives  to offer world-class applications to protect the planet's most important data–your data.

**Chain ID**: lupulella-2 | **Latest Version Tag**: v1.2.0-alpha.4 | **Wasm**: ON

Website: [https://jackalprotocol.com](https://jackalprotocol.com)


## Public endpoints

* rpc: [https://jackal-testnet.rpc.kjnodes.com](https://jackal-testnet.rpc.kjnodes.com)
* api: [https://jackal-testnet.api.kjnodes.com](https://jackal-testnet.api.kjnodes.com)

## Peering

**state-sync**

```
d5519e378247dfb61dfe90652d1fe3e2b3005a5b@jackal-testnet.rpc.kjnodes.com:37656
```

**seed-node**

```
3f472746f46493309650e5a033076689996c8881@jackal-testnet.rpc.kjnodes.com:37659
```

**addrbook**
```
curl -Ls https://snapshots.kjnodes.com/jackal-testnet/addrbook.json > $HOME/.canine/config/addrbook.json
```

**live-peers** (6)
```
peers="d5519e378247dfb61dfe90652d1fe3e2b3005a5b@65.109.68.190:37656,9b2bbd5121265ebbf9003341e8a2e0abdbc24b67@46.228.199.8:26656,5eedbfbe64b942f4ab54db3842acf3bfab034c24@161.97.74.88:46656,09d9127972ded9e22f9f11833ed7fcfa149cf1fa@65.109.92.240:19126,0394449cab5a29f24dd4f37683d3b7622f27c0fc@65.108.206.118:61156,94b63fddfc78230f51aeb7ac34b9fb86bd042a77@95.217.89.23:30567"
sed -i 's|^persistent_peers *=.*|persistent_peers = "'$peers'"|' $HOME/.canine/config/config.toml
```
