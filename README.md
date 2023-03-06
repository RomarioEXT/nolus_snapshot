# Nolus snapshot 

This is nolus-rila chain snapshot, autoupdating everyday


Stop node service, save priv validator state and remove data
```
sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
mkdir $HOME/.nolus/data
```
Download snapshot and unpack to data folder, move back you priv validator state and start service

```
wget -O - http://65.108.104.167/nolus/nolus-rila_latest.tar | tar xf - -C $HOME/.nolus/data
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
sudo systemctl start nolusd && sudo journalctl -u nolusd -f --no-hostname -o cat
```
