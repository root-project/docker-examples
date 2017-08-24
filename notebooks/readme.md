## Notebooks
ROOT can also start with Jupyter notebooks [using the --notebook flag](https://root.cern.ch/how/how-create-rootbook). This example shows how to craete a Docker file that will act as a ROOT Jupyter web service listening on port 8888. 

### Building
To build the container:
```
$ docker build -t root-notebooks .
```
### Running
To run the container:
```
$ docker run --name root-notebooks -it root-notebooks
```

This will start the container listening on port 8888. Using the `--name root-notebooks` also makes it only possible to spawn one container of this image. Take note of the printed URL in the console. Instead entering http://localhost:8888/?token=secrettoken, localhost needs to be replaced by the IP address of the container. This can be found by opening a new terminal and find the newly spawned contained through `docker inspect root-notebook`:
``` 
$ docker inspect root-notebooks | grep IPAddress
            "SecondaryIPAddresses": null,
            "IPAddress": "172.17.0.2",
                    "IPAddress": "172.17.0.2",
```

The IP address will differ depending on how many containers the host is running and/or which operating system it is running. Windows containers will always have a fixed IP address of 10.0.75.2.

After exiting the container through Ctrl+C, the root-notebooks container can be spawned again by running:
``` 
$ docker start root-notebook
```

### Note about persistence
This tutorial does not focus on keeping the data in the docker container. It is therefore suggested to store the data having to be persistent either in a mounted directory or in a data volume. See the persistence example for more information.