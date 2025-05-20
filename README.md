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
echo "export LUM_PORT="26"" >> $HOME/.bash_profile
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
https://snapshot.rpcdot.com/lumera/genesis.json (https://github.com/LumeraProtocol/lumera-networks)
```
## Addrbook
```
https://snapshot.zeycanode.com/lumera/addrbook.json
```
## Peers And Gas
```
SEEDS=""
PEERS="84d98f2821fa97952c8446d9afb8d959a1ea0069@49.12.87.14:30756,5e8af106ab8273479eaf76c81ceef6fcd0a42555@152.53.110.139:63656,a2cac656019665fcd03d3039fee5940e77a035c4@37.27.239.10:26656,0df5af293889fa827d14dade600daa11f548fbd6@95.217.152.99:26656,13fe76b868a6dc601b4603c4f3c0febe9b17008c@65.21.67.40:36656,7554830c281f5a6cefd0355d71d828ef49a8f987@149.50.101.137:11456,c3dafe86535b32c245cba669b4b9085ac1bce883@195.88.71.111:26656,8a24daaac44fad0bf9bcc27ee1f91b24a32a7f51@154.91.1.115:26656,c03fce64f173d50a6b98309658d43bb3fa09ae17@65.109.120.211:36656,8d7557e2e4e8c5d3b409663764d9fdc22d2c3449@44.204.100.172:26656,dd7ee8d06bfcd4e7a89e8e6f7bdb46467c9a589b@209.126.12.242:13656,2fe5e18e23c24accacfa9fada0f2683b9721cb0c@95.217.77.229:30756,4ee99f2039eee00535e2197f77cfd23f61803cc0@66.129.102.28:26656,85c44e89370a614aa9df951ab348c937b2bf6094@184.107.110.139:59700,54bb17ce612313b941ec6aee00413d6a08032e69@64.203.83.66:26656,49e22975a1d6c5204072f25eb71c01faf54b4b92@88.99.149.170:17656,b36a48196e9eef37d01716868dfe41938617bd6f@65.109.88.22:26666,7f0c7ae8eae8108cc8ed6dbc66efd16f9676bac9@3.218.250.158:26656,4ce2b8dea40cbf867bde32c17a24b19b26c981a3@65.21.220.178:26656,10a50e7a88561b22a8d1f6f0fb0b8e54412229ab@44.198.60.93:26656,dafc81d3a24a2a96f8da1f3ce7bd0b83601726ec@160.250.106.37:30756,ee7b29ce2ef3c7d18a58dc96ab9e6516755bfa0f@65.108.131.104:30756,020caf16885970199588fcfa44c49eedc5e97421@88.198.52.46:30756,1d1ec60e886f1fc84b8c7628305f70231b15f240@195.26.252.175:13656,f9d6abcabd2aeb417205d461ce6138473cf58619@62.169.16.57:16656,3e00e110111612ac9c3d93b6ba75796c82a7bd1d@141.94.141.165:26856,0f85ddad45882ba2f770de01308dafcc833abe81@94.130.23.254:30756,7c37a7eb1292b432a8f98ba40d32cb3dd4b3beeb@164.132.247.253:56416,7afeb06db4edc7e7a6c018909876808408c4d1d7@148.113.165.128:56416,4902d5db03ad6754e287ffdd051a5507a595927a@3.236.181.141:26656,bbe74b3b02fdd08ff2197fac8a2cffaa630e9de7@195.26.250.45:13656,7dab84e313053596727f5c5a83115ea29cde25b4@207.244.245.246:13656,21eed186f6c61dc7adf5abb50527e256fb196750@152.53.230.81:19656,688739e887a58efc0238047325138639df764d10@207.244.233.242:13656,bec7c80448377704965b54c16bfd11654ef0a3a7@207.244.239.234:26656,d6238afe24aa289094556668914efb4fc3e74ba2@195.26.250.90:13656,e248a757ac9b5f449d1a15f243b61c8a1598e37a@154.38.175.225:13656,b04edc1b7a10b1a4e4c60811f57d0a89d1c86c2e@65.109.52.200:26656,ada9b1c31d2ac183ddcfcf7378ed408cd056391a@65.21.29.250:3690,aca01eb0132926da40310622f5629c8be1feb304@95.216.7.84:11456,97bfa489b34bf5b125dc40667623b45350b7dba4@136.60.129.34:26656,6aef903032e088bdd77e3629508caac373fe96b3@209.126.12.85:13656,655e83ae60def1a4f435bc31e759562d419c18ac@195.26.251.0:26656,60e8746bcfbc4fc3b31d226eb01cf18375769c6c@68.183.226.185:26656,c01a9ef6bc84302db2107ccee7dd3908f68a8304@65.109.113.233:30756,46459d4fc4ac4c4bdf440a0d9ff4097e2557f3eb@62.169.16.79:13656,ad0b77cb312cd848b3debe7fbef677ef480beb75@116.202.210.177:22656,c2ae41bf57e1a5b56229846b1b113d46f3206bf3@44.193.206.52:26656,93d774235e67d1ec5f613f284fb0a200a0822252@136.243.59.103:31656,67bc89ef54a0f7c75d8f0759929937b88aa6c49a@152.53.245.124:12656,9ae8787e6519141369b8858f6c240336767c1f7c@95.217.76.186:26656,c96e213f718967bd0a00f3d9f61485d28b02cba6@82.55.151.234:26656,39e73a3566f9e9751aed23d56a40945b9daedb26@65.109.18.91:52656,046d22414c39347932c978a5c7f5c2ad02876ac0@195.26.253.188:10656,9ed3e540ca5ff2d57a58cd9b62128a48f0fe01c3@65.109.59.22:30756,a202e00ce44a9f9764cfe647b6a87b78aae665d6@145.239.9.196:36656"
sed -i -e "s/^seeds *=.*/seeds = \"$SEEDS\"/; s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" $HOME/.lumera/config/config.toml
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




