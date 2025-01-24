---
description: Catch the latest block faster by using our daily snapshots.
---

# Snapshot

<figure><img src="https://raw.githubusercontent.com/kj89/cosmos-images/main/logos/jackal.png" width="150" alt=""><figcaption></figcaption></figure>

{% hint style='info' %}
Snapshots allows a new node to join the network by recovering application state from a backup file. 
Snapshot contains compressed copy of chain data directory. To keep backup files as small as plausible, 
snapshot server is periodically beeing state-synced.
{% endhint %}

Snapshots are taken automatically every 6 hours starting at **00:45 UTC**

**pruning**: 100/0/19 | **indexer**: null | **version tag**: bouncybulldog

| BLOCK             | AGE             | DOWNLOAD                                                                                            |
| ----------------- | --------------- | --------------------------------------------------------------------------------------------------- |
| 2174292 | 5 hours | [snapshot (2.0 GB)](https://snapshots.kjnodes.com/jackal/snapshot\_latest.tar.lz4) |

## Instructions

### Stop the service and reset the data

```bash
sudo systemctl stop canined
cp $HOME/.canine/data/priv_validator_state.json $HOME/.canine/priv_validator_state.json.backup
rm -rf $HOME/.canine/data
```

### Download latest snapshot

```bash
curl -L https://snapshots.kjnodes.com/jackal/snapshot_latest.tar.lz4 | tar -Ilz4 -xf - -C $HOME/.canine
mv $HOME/.canine/priv_validator_state.json.backup $HOME/.canine/data/priv_validator_state.json
```

### Restart the service and check the log

```bash
sudo systemctl start canined && sudo journalctl -u canined -f --no-hostname -o cat
```
