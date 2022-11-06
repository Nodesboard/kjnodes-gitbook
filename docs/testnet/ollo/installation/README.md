---
description: >-
  This page contain instructions that will help you to setup a node. For the
  installation we use Ubuntu 20.04
---

# Installation

### Setup validator name

```bash
MONIKER="YOUR_MONIKER_GOES_HERE"
```

### Install dependencies

#### Update system and install build tools

```bash
sudo apt update
sudo apt install curl git jq lz4 build-essential -y
```

#### Install GO

```bash
sudo rm -rf /usr/local/go
sudo curl -Ls https://go.dev/dl/go1.19.linux-amd64.tar.gz | sudo tar -C /usr/local -xz
tee -a $HOME/.profile > /dev/null << EOF
export PATH=$PATH:/usr/local/go/bin
EOF
source $HOME/.profile
```

### Download and build binaries

```bash
cd $HOME
rm -rf ollo
git clone https://github.com/OLLO-Station/ollo.git
cd ollo

# Compile genesis version v0.0.1
git checkout v0.0.1
make build
mkdir -p $HOME/.ollo/cosmovisor/genesis/bin
mv bin/ollod $HOME/.ollo/cosmovisor/genesis/bin/

```

### Install Cosmovisor and create a service

```bash
curl -Ls https://github.com/cosmos/cosmos-sdk/releases/download/cosmovisor%2Fv1.3.0/cosmovisor-v1.3.0-linux-amd64.tar.gz | tar xz
chmod 755 cosmovisor
sudo mv cosmovisor /usr/bin/cosmovisor

sudo tee /etc/systemd/system/ollod.service > /dev/null << EOF
[Unit]
Description=ollo-testnet node service
After=network-online.target
[Service]
User=$USER
ExecStart=/usr/bin/cosmovisor run start
Restart=on-failure
RestartSec=10
LimitNOFILE=65535
Environment="DAEMON_HOME=$HOME/.ollo"
Environment="DAEMON_NAME=ollod"
Environment="UNSAFE_SKIP_BACKUP=true"
[Install]
WantedBy=multi-user.target
EOF
sudo systemctl daemon-reload
sudo systemctl enable ollod
```

### Initialize the node

```bash
ln -s $HOME/.ollo/cosmovisor/genesis $HOME/.ollo/cosmovisor/current
sudo ln -s $HOME/.ollo/cosmovisor/current/bin/ollod /usr/local/bin/ollod
ollod config chain-id ollo-testnet-1
ollod config node tcp://localhost:32657
ollod init $MONIKER --chain-id ollo-testnet-1
curl -Ls https://snapshots.kjnodes.com/ollo-testnet/genesis.json > $HOME/.ollo/config/genesis.json
curl -Ls https://snapshots.kjnodes.com/ollo-testnet/addrbook.json > $HOME/.ollo/config/addrbook.json
sed -i -e "s|^seeds *=.*|seeds = \"400f3d9e30b69e78a7fb891f60d76fa3c73f0ecc@ollo-testnet.rpc.kjnodes.com:32659\"|" $HOME/.ollo/config/config.toml
tee $HOME/.ollo/data/priv_validator_state.json > /dev/null << EOF
{
  "height": "0",
  "round": 0,
  "step": 0
}
EOF
sed -i -e "s|^minimum-gas-prices *=.*|minimum-gas-prices = \"0utollo\"|" $HOME/.ollo/config/app.toml
sed -i -e "s|^pruning *=.*|pruning = \"custom\"|" $HOME/.ollo/config/app.toml
sed -i -e "s|^pruning-keep-recent *=.*|pruning-keep-recent = \"5\"|" $HOME/.ollo/config/app.toml
sed -i -e "s|^pruning-keep-every *=.*|pruning-keep-every = \"0\"|" $HOME/.ollo/config/app.toml
sed -i -e "s|^pruning-interval *=.*|pruning-interval = \"1000\"|" $HOME/.ollo/config/app.toml

sed -i.bak -e "s%^proxy_app = \"tcp://127.0.0.1:26658\"%proxy_app = \"tcp://127.0.0.1:32658\"%; s%^laddr = \"tcp://127.0.0.1:26657\"%laddr = \"tcp://127.0.0.1:32657\"%; s%^pprof_laddr = \"localhost:6060\"%pprof_laddr = \"localhost:32060\"%; s%^laddr = \"tcp://0.0.0.0:26656\"%laddr = \"tcp://0.0.0.0:32656\"%; s%^prometheus_listen_addr = \":26660\"%prometheus_listen_addr = \":32660\"%" $HOME/.ollo/config/config.toml
sed -i.bak -e "s%^address = \"tcp://0.0.0.0:1317\"%address = \"tcp://0.0.0.0:32317\"%; s%^address = \":8080\"%address = \":32080\"%; s%^address = \"0.0.0.0:9090\"%address = \"0.0.0.0:32090\"%; s%^address = \"0.0.0.0:9091\"%address = \"0.0.0.0:32091\"%; s%^address = \"0.0.0.0:8545\"%address = \"0.0.0.0:32545\"%; s%^ws-address = \"0.0.0.0:8546\"%ws-address = \"0.0.0.0:32546\"%" $HOME/.ollo/config/app.toml
```

### Download latest chain snapshot

```bash
curl -L https://snapshots.kjnodes.com/ollo-testnet/snapshot_latest.tar.lz4 | lz4 -dc - | tar -xf - -C $HOME/.ollo
```

### Start service and check the logs

```bash
sudo systemctl start ollod && journalctl -u ollod -f --no-hostname -o cat
```