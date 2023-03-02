# fndelk

This repository is aiming to use ELK to get insights in Cisco IOT FND data
The ELK components are deployed in docker containers to be used.



First I recommend to install portainer:

docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce