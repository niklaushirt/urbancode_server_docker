# UrbanCode Deploy server on Docker

##First build the java base image:

```
cd ibm-java
docker build -t "ibm-java" .
```

##Then build the UrbanCode Deploy server image

```
cd urbancode-deploy
docker build -t "docker_ucd" .
```

##Starting the container

```
docker run -d -p 8080:8080 -p 8443:8443 --name=ucd-r docker_ucd
```
