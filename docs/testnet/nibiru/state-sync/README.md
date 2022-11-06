---
description: This page contain instructions to rapidly state sync your validator node
---

# State sync

### Basic information

#### RPC endpoint:

```bash
https://nibiru-testnet.rpc.kjnodes.com:443
```

#### Peer:

```bash
d9bfa29e0cf9c4ce0cc9c26d98e5d97228f93b0b@nibiru-testnet.rpc.kjnodes.com:39656
```

### Stop the service and reset the data

```bash
sudo systemctl stop nibid
cp $HOME/.nibid/data/priv_validator_state.json $HOME/.nibid/priv_validator_state.json.backup
nibid tendermint unsafe-reset-all --home $HOME/.nibid
```

### Get and configure the state sync information

```bash
STATE_SYNC_RPC=https://nibiru-testnet.rpc.kjnodes.com:443
STATE_SYNC_PEER=d9bfa29e0cf9c4ce0cc9c26d98e5d97228f93b0b@nibiru-testnet.rpc.kjnodes.com:39656
LATEST_HEIGHT=$(curl -s $STATE_SYNC_RPC/block | jq -r .result.block.header.height)
SYNC_BLOCK_HEIGHT=$(($LATEST_HEIGHT - 2000))
SYNC_BLOCK_HASH=$(curl -s "$STATE_SYNC_RPC/block?height=$SYNC_BLOCK_HEIGHT" | jq -r .result.block_id.hash)

sed -i.bak -e "s|^enable *=.*|enable = true|" $HOME/.nibid/config/config.toml
sed -i.bak -e "s|^rpc_servers *=.*|rpc_servers = \"$STATE_SYNC_RPC,$STATE_SYNC_RPC\"|" \
  $HOME/.nibid/config/config.toml
sed -i.bak -e "s|^trust_height *=.*|trust_height = $SYNC_BLOCK_HEIGHT|" \
  $HOME/.nibid/config/config.toml
sed -i.bak -e "s|^trust_hash *=.*|trust_hash = \"$SYNC_BLOCK_HASH\"|" \
  $HOME/.nibid/config/config.toml
sed -i.bak -e "s|^persistent_peers *=.*|persistent_peers = \"$STATE_SYNC_PEER\"|" \
  $HOME/.nibid/config/config.toml
mv $HOME/.nibid/priv_validator_state.json.backup $HOME/.nibid/data/priv_validator_state.json
```

### Restart the service and check the log

```bash
sudo systemctl start nibid && journalctl -u nibid -f --no-hostname -o cat
```