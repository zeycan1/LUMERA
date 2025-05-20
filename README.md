![image](https://github.com/user-attachments/assets/53c14741-463c-462a-bcbe-2e6b0347e40f)

# LUMERA

## API: https://lumera-testnet-api.zeycanode.com/
## RPC: https://lumera-testnet-rpc.zeycanode.com/

## 💻 System Requirements
| Components | Minimum Requirements |
| ------------ | ------------ |
| CPU |	4|
| RAM	| 8+ GB |
| Storage	| 400 GB SSD |# LUMERA

## 1️⃣ Install Required Packages
```
sudo apt update && sudo apt upgrade -y
sudo apt install curl git wget htop tmux build-essential jq make lz4 gcc unzip -y
```
## Go Installation
```
ver="1.22.5"
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz"
rm "go$ver.linux-amd64.tar.gz"
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> ~/.bash_profile
source ~/.bash_profile
go version
```
## Port 
```
echo "export LUM_PORT="28"" >> $HOME/.bash_profile
source $HOME/.bash_profile
```
## Binary
```
cd $HOME
curl -LO https://github.com/LumeraProtocol/lumera/releases/download/v1.0.1/lumera_v1.0.1_linux_amd64.tar.gz
tar -xvf lumera_v1.0.1_linux_amd64.tar.gz
rm lumera_v1.0.1_linux_amd64.tar.gz
rm install.sh
mv libwasmvm.x86_64.so /usr/lib/
chmod +x lumerad
mv lumerad $HOME/go/bin/
```
## Initialize lumerad
```
lumerad init "MONIKER" --chain-id lumera-testnet-1
```
## Genesis
```
https://snapshot.rpcdot.com/lumera/genesis.json
```
## Addrbook
```
https://snapshot.zeycanode.com/lumera/addrbook.json
```
## Peers And Gas
```
peers="$(curl -sS https://lumera-testnet-rpc.rpcdot.com:443/net_info | jq -r '.result.peers[] | "\(.node_info.id)@\(.remote_ip):\(.node_info.listen_addr)"' | awk -F ':' '{print $1":"$(NF)}' | sed -z 's|\n|,|g;s|.$||')"
sed -i.bak -e "s/^persistent_peers *=.*/persistent_peers = \"$peers\"/" $HOME/.lumera/config/config.toml
```
```
sed -i.bak -e "s/^minimum-gas-prices *=.*/minimum-gas-prices = \"0.025ulume\"/" $HOME/.lumera/config/app.toml
```
## Pruning and Indexer
```
sed -i -e "s/^pruning *=.*/pruning = \"custom\"/" $HOME/.lumera/config/app.toml
sed -i -e "s/^pruning-keep-recent *=.*/pruning-keep-recent = \"100\"/" $HOME/.lumera/config/app.toml
sed -i 's|^indexer *=.*|indexer = "null"|' $HOME/.lumera/config/config.toml
```
## Port
```
sed -i.bak -e "s%:26658%:${LUM_PORT}658%g;
s%:26657%:${LUM_PORT}657%g;
s%:6060%:${LUM_PORT}060%g;
s%:26656%:${LUM_PORT}656%g;
s%^external_address = \"\"%external_address = \"$(wget -qO- eth0.me):${LUM_PORT}656\"%;
s%:26660%:${LUM_PORT}660%g" $HOME/.lumera/config/config.toml
```
```
sed -i.bak -e "s%:1317%:${LUM_PORT}317%g;
s%:8080%:${LUM_PORT}080%g;
s%:9090%:${LUM_PORT}090%g;
s%:9091%:${LUM_PORT}091%g;
s%:8545%:${LUM_PORT}545%g;
s%:8546%:${LUM_PORT}546%g;
s%:6065%:${LUM_PORT}065%g" $HOME/.lumera/config/app.toml
```
## Service
```
sudo tee /etc/systemd/system/lumerad.service > /dev/null <<EOF
[Unit]
Description=lumera
After=network-online.target

[Service]
User=$USER
ExecStart=$(which lumerad) start
Restart=on-failure
RestartSec=3
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
EOF
```
## Service Start
```
sudo systemctl daemon-reload
sudo systemctl enable lumerad
sudo systemctl restart lumerad
sudo journalctl -u lumerad -f -o cat
```
## Wallet Add
```
lumerad keys add wallet
```
## Wallet Recover
```
lumerad keys add wallet --recover
```
## Pubkey
```
lumerad tendermint show-validator
```
## Validator Crate
```
nano $HOME/.lumera/validator.json
```
```
{
  "pubkey":  ,
  "amount": "1000000ulume",
  "moniker": "YourMoniker",
  "identity": "KeybaseID",
  "website": "https://web.com",
  "security": "yourmail@gmail.com",
  "details": "Mini Details",
  "commission-rate": "0.05",
  "commission-max-rate": "0.2",
  "commission-max-change-rate": "0.05",
  "min-self-delegation": "1"
}
```
CTRL X , CTRL Y 
## Crate
```
lumerad tx staking create-validator $HOME/.lumera/validator.json \
--from wallet \
--chain-id lumera-testnet-1 \
--gas-prices=0.025ulume \
--gas-adjustment=1.5 \
--gas=auto
```
## Delegate to Yourself
```
lumerad tx staking delegate $(lumerad keys show $LUMERA_WALLET --bech val -a) 1000000ulume --from $LUMERA_WALLET --chain-id lumera-testnet-1 --gas-prices=0.025ulume --gas-adjustment=1.5 --gas=auto -y 
```
## Complete deletion
```
cd $HOME
sudo systemctl stop lumerad
sudo systemctl disable lumerad
sudo rm -rf /etc/systemd/system/lumerad.service
sudo systemctl daemon-reload
sudo rm -f /usr/local/bin/lumerad
sudo rm -f $(which lumerad)
sudo rm -rf $HOME/.lumera
sed -i "/LUMERA_PORT_/d" $HOME/.bash_profile
sed -i "/LUMERA_WALLET_/d" $HOME/.bash_profile
```




