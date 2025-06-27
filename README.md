# docker-runner-win-container

Reference  doc:
https://arc.net/l/quote/edhaglqe

Need to use docker Desktop and windows containers

## Build the image

Check for latest releases https://github.com/actions/runner/releases


docker build --build-arg RUNNER_VERSION=2.325.0 --tag docker-github-runner-win .


## Run the Docker Image - Docker Desktop (Windows)
#Run container from image:
```
docker run -e GH_TOKEN='myPatToken' -e GH_OWNER='orgName' -e GH_REPOSITORY='repoName' -d image-name
```



### stop runner
docker stop $(docker ps -aq) && docker rm $(docker ps -aq)

### Cleanup
```
.\scripts\Cleanup-Runners.ps1 -owner "orgName" -repo "repoName" -pat "myPatToken"
```
## use docker compose
```
docker-compose build
```
## Run and scale the Docker Image - Docker Compose (Windows)

What's nice about using docker-compose is that we can easily scale the amount of runners we want to use simply by running the following command:
```
docker-compose up --scale runner=3 -d
```
Because all of our configuration and details are kept in environment variables and the docker-compose 'YAML' file, we don't really have to run long docker commands as we did earlier, and we simply scale the amount of runners we want by specifying the '--scale' parameter.

> NOTE: The '--scale runner=3 -d' parameter is based on the docker compose file, 'services:' setting, which in our case is called 'runner':

### To scale down to one runner, we can simply rerun the command as follow:
```
docker-compose up --scale runner=1 -d
```

To stop and remove all running containers simply run:
```
docker-compose stop
docker rm $(docker ps -aq)
```