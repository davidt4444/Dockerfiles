If starting dockerfile build over after image deletion 
sudo docker builder prune 

sudo docker compose up -d 


Copy or move over the following files from the vpn server (The names are referenced in client.conf, so change references if needed)
sudo cp ~/vpn/ca.crt ./config
sudo cp ~/vpn/myclient1.crt ./config
sudo cp ~/vpn/myclient1.key ./config
sudo cp ~/vpn/ta.key ./config

Change my-server-1 to the remote server address in client.conf, then
sudo cp client.conf ./config

Attach to the container and run 
openvpn --config /config/client.conf

