Docker running Nginx static content
===================================

Getting started.

0. When on OS X boot2docker provides a VirtualBox VM virtual machine for Docker to run on.
   Initialize and start up boot2docker with

```
boot2docker init
boot2docker up
```

Export the resulting environment variables (`DOCKER_HOST`, `DOCKER_CERT_PATH`, `DOCKER_TLS_VERIFY`).

1. Build the Docker container in the root path.

```
docker build -t foo:nginx_static .
```

2. Run the container.

```
docker run -p 80:80 foo:nginx_static
```

3. Grab the IP of the Docker host.

```
boot2docker ip
```

This should display the static html page.


You can now go on to commit the container to be re-used later. To that
end, get the container id with `docker ps` yielding, e.g. `61aa913398ca`.
Then commit.

```
docker commit -m "Add nginx serving index.html file statically." 61aa913398ca foo:nginx_static
```

This will yield a length weired ting. Finally you can stop the docker
container now.

```
docker kill 61aa913398ca
```
