## Hello-world
This example shows how to create an image containing a simple macro printing a hello world in ROOT. It demonstrates how to extend the dockerfile on a basic level for distribution.

### Building
To build the container:
```
$ docker build -t root-hello-world .
```
### Running
To run the container:
```
$ docker run --rm -it root-hello-world
```
This will run the command specified with the CMD directive in the Dockerfile (`root.exe -q hello.C`).
It is also possible to specify the entire command to run in ROOT:
```
$ docker run --rm -it root-hello-world root.exe hello.C
```
This will run hello.C and leave the user in the ROOT prompt.
Another possibility is to open a bash shell inside the hello-world image:
```
$ docker run --rm -it root-hello-world bash
```
