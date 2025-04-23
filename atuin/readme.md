### Atuin server
https://docs.atuin.sh/self-hosting/docker/
Run this in the directory
sudo docker compose up -d 

Add in the service
sudo cp atuin-server.service /etc/systemd/system/

start and enable
sudo systemctl enable --now atuin-server

check status
sudo systemctl status atuin-server

Run the following command to move the server config over 
sudo cp server.toml config
sudo systemctl restart atuin-server


### Atuin client 
Run 
curl --proto '=https' --tlsv1.2 -LsSf https://setup.atuin.sh | sh
cp config.toml ~/.config/atuin/
atuin register -u dathigpe -e david@davidthigpen.com
atuin key
atuin sync

#### Bind ctrl-r but not up arrow
eval "$(atuin init bash --disable-up-arrow)"

#### Bind up-arrow but not ctrl-r
eval "$(atuin init bash --disable-ctrl-r)"

#### no bind
export ATUIN_NOBIND="true"

#### Bind reset
eval "$(atuin init bash)"
