## setup
If you haven't already created the network, run
sudo docker network create --attachable -d bridge development-network

If starting dockerfile build over after image deletion 
sudo docker builder prune 

To create the container run
sudo docker compose up -d 
and on initial launch run passwd to change the password.

If you decide to attach container to vpn network uncomment network_mode and rename according to the client container name used for the vpn_client
