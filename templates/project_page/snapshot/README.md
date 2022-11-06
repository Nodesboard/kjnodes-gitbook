---
description: >-
  This page contains the latest snapshot to help validators rapidly recover node
  functionality.
---

# Snapshot

| BLOCK             | AGE             | DOWNLOAD                                                                         | SIZE             |
| ----------------- | --------------- | -------------------------------------------------------------------------------- | ---------------- |
| ${SNAPSHOT_BLOCK} | ${SNAPSHOT_AGE} | [snapshot](https://snapshots.kjnodes.com/${CHAIN_NAME}/snapshot\_latest.tar.lz4) | ${SNAPSHOT_SIZE} |

### Stop the service and reset the data

```bash
sudo systemctl stop ${CHAIN_APP}
cp $HOME/${CHAIN_DIR}/data/priv_validator_state.json $HOME/${CHAIN_DIR}/priv_validator_state.json.backup
rm -rf $HOME/${CHAIN_DIR}/data
```

### Download the latest snapshot

```bash
curl -L https://snapshots.kjnodes.com/${CHAIN_NAME}/snapshot_latest.tar.lz4 | lz4 -dc - | tar -xf - -C $HOME/${CHAIN_DIR}
mv $HOME/${CHAIN_DIR}/priv_validator_state.json.backup $HOME/${CHAIN_DIR}/data/priv_validator_state.json
```

### Restart the service and check the log

```bash
sudo systemctl start ${CHAIN_APP} && journalctl -u ${CHAIN_APP} -f --no-hostname -o cat
```