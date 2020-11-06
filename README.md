# Voting app Using Redis and Flask [Techbleat Final Project ]

A simple voting app that uses Redis for a data store and a Python Flask app for the frontend.

- 
- Build  Docker image
- Publish image to Docker hub
- Deploy image as container on blue|green enviornment 
- 

## Prerequisites

To run the app, you need docker, web serer and redis cluster


## About the Project 

The project  is meant to cement what has been taught in the module

You should create a build server to manage application and infrastructure pipeline. Jenkins should be used for the pipeline.
Use Continous Integration mechanism as much as possible
Set up Prometheus to manage infrastructure and application monitoring and alerting 
All application should run on Docker 
Use Amazon  EC2 as node
 


## About the App

The application is a voting app , written in Python Flask.

### Resources
The environment variables `REDIS`, `REDIS_PORT`  and `REDIS_PWD` are required for the app.

The Flask app uses these environment variables to connect to the Redis cache container. See the following in [`frontend/app/main.py`](frontend/app/main.py):

```python
redis_server =   os.environ['REDIS']
redis_port =     os.environ['REDIS_PORT']
redis_password = os.environ['REDIS_PWD']

```

### Building the app

This is only to serve as a guide . Please research or check with the developer.

```
docker build . -t shegoj/techbleatapp
docker login 
docker push  shegoj/techbleatapp
```
run app on target node as 
```
docker run -d -p 5001:80 -e REDIS=192.168.1.162 -e REDIS_PORT=6379  -e REDIS_PWD=redis --name blue-app shegoj/techbleatapp
```

run redis [ single nodes ] as 

```
docker run -d -p 6379:6379   -e REDIS_PASSWORD=redis --name redis redis /bin/sh -c 'redis-server --appendonly yes --requirepass ${REDIS_PASSWORD}'
```
