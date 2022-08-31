# Configurable listing port in nodejs container

This repo contains a hello world nodejs project to demonstrate howto use a Configurable listing port. This can be used to expose multiple instances of a container on the same host.



# Usage

Build the image

```
docker build . -t mwillemsma/node-app
```

Push the image

```
docker push mwillemsma/node-app:latest
```


Run a container instance on port tcp/8020

```
docker run --name node -e PORT=8020 -p 8020:8020 mwillemsma/node-app:latest
Running on http://0.0.0.0:8020
```


```
docker run --name node2 -e PORT=8030 -p 8030:8030 mwillemsma/node-app:latest
Running on http://0.0.0.0:8030
```


Test

```
curl localhost:8020
Hello World%                     

curl localhost:8030
Hello World%                          
```


Cleanup


```
docker rm node node2 -f
```
