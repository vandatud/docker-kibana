# VANDA - Kibana Container

_This image is only intended for being part of the VANDA Deap Learning Stack!_ 

Runs [Kibana 5.2.0](https://www.elastic.co/guide/en/kibana/5.2/index.html) on top of the [debian/jessie](https://hub.docker.com/_/debian/) with Debian Jessie as base system.

## Dockerfile

[`vandatud/kibana` Dockerfile](https://github.com/vandatud/docker-kibana/blob/master/Dockerfile)

## How to rebuild an extended image

After pulling this repository and changing the Dockerfile first build the new image locally to test it.
Optionally specify the repository and tag at which to save the new image if the build succeeds.
```
$ docker build -t vandatud/kibana:1.0.1 -t vandatud/kibana:latest -f /path/to/Dockerfile
```

If this Git repository is pushing back to the server, DockerHub will automatically build this image.
For manually push the locally build to the DockerHub use the docker cli.

```
$ docker login
```

```
$ docker push vandatud/kibana:0.0.1
```

## How to use this image

Run a new container instance without

```
$ docker run -d -t -p 5601:5601 --name vanda-kibana_inst --link vanda-elasticsearch_inst vandatud/kibana:latest
```

or with an interactive bash session for inspecting the image.

```
$ docker run --rm -t -i -p 5601:5601 --name vanda-elasticsearch_inst vandatud/kibana:latest -- bash -l
```

```
$ docker ps
CONTAINER ID        IMAGE                           COMMAND             CREATED                  STATUS              PORTS                                              NAMES
c8f421d459ce        vandatud/kibana:1.0.3           "kibana"            Less than a second ago   Up 2 minutes        0.0.0.0:5601->5601/tcp                             vanda-kibana_inst
e46a689d75a8        vandatud/elasticsearch:latest   "elasticsearch"     About an hour ago        Up 57 minutes       0.0.0.0:32782->9200/tcp, 0.0.0.0:32781->9300/tcp   vanda-elasticsearch_inst
```

Once the container is running you can open the web interface under the attached host port (i.e. [localhost:5601](http://localhost:5601))
