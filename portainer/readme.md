### install portainer
https://www.portainer.io/blog/portainer-your-docker-gui-for-your-ubuntu-linux-desktop
sudo docker volume create portainer_data
sudo docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
https://localhost:9000
sudo docker restart portainer

https://stackoverflow.com/questions/68767930/docker-daemon-already-running-but-still-got-cannot-connect-to-the-docker-daemon
sudo ln -s -f /Users/dathigp/.docker/run/docker.sock /var/run/docker.sock
