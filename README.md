# Using ELK for FND Insights

This repository is aiming to use ELK to get insights in Cisco IOT FND data
The ELK components are deployed in docker containers to be used.

ELK can be used on your laptop (MacOS) or a linux server.
You need to have docker installed.

First I recommend to install portainer:

```
docker run -d -p 8000:8000 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
```

This will pull the latest portainer and run portainer locally.

Access portainer UI at http://localhost:9000
You will need to setup a new password.

On the home page select the local environment
![Alt text](docs/image-1.png)

Select Stacks then Add Stack, select repository and use: 
- repository URL : https://github.com/laurentandrian/fndelk.git
- compose path: elk-stack.yml
  

![Alt text](docs/image-3.png)

Add 3 environment variables:
- ELK_VERSION : e.g. 8.6.0
- PATH_ES : local path to store ES data
- PATH_KIBANA : local path to store Kibana data


Click on deploy stack, portainer will pull the docker images and run the containers.

To access Kibana UI : http://localhost:5601

The first usage is to analyze the FND events. 
From FND UI you can extract all the events into a CSV file with following format:
```
Severity,Name,Time,Event Name,Message
```
The exported file from FND has 3 lines at the beginning, with Events, Exported date, blank line. 
Remove these line and save the CSV file.

To import the updated CSV file in ES, on Kibana UI, Home, there is link with Upload a File, click on this link.
![Alt text](docs/image.png)

Upload your file, you will see something like this:
![Alt text](docs/image-11.png)

Click on Import at bottow left.
Then add the data to a new index.

![Alt text](docs/image-12.png)

