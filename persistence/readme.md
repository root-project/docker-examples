## Persistence
This example show how data can be persisted outside the containers. With containers, persistent data should not be stored in the container itself. One approach is to mount a directory from the host and store the data there. Although application data is recommended to be stored in [data volumes](https://docs.docker.com/engine/admin/volumes/#more-details-about-mount-types), this example binds a `data` directory to the container and stores files in this directory. 

### Building
To build the container:
```
$ docker build -t root-persistence .
```
### Running
To run the container:
```
$ docker run --rm -v $(pwd)/data:/data -it root-persistence
```
This will run the [TDataFrame data model tutorial](https://root.cern/doc/master/tdf002__dataModel_8C.html) and save the output in ./data on the host:
``` 
docker-examples/persistence$ ls data 
tdf002_dataModel.root  tracks_n.png  tracks_pt.png  tracks_Wpt.png
```
It is also possible to run other ROOT tutorials by specifying it to root.exe:
```
$ docker run --rm -v $(pwd)/data:/data -it root-persistence \
      root.exe -q /usr/local/share/doc/root/tutorials/dataframe/tdf004_cutFlowReport.C
```

The previous command will store the output to tdf004_cutFlowReport.root under `data`.
