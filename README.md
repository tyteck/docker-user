# Avoiding permissions denied

## Building docker image
before building you have to set 2 variables.
* USER_ID and
* GROUP_ID

```bash
USER_ID=$(id -u) GROUP_ID=$(id -g) docker-compose build
```

these 2 variables are ~~used~~ expected in the Dockerfile.

```docker
ARG         USER_ID
ARG         GROUP_ID
```

once received they are used to create user in the container.

```docker
RUN         addgroup --gid $GROUP_ID dockeruser
RUN         adduser --disabled-password --gecos '' --uid $USER_ID --gid $GROUP_ID dockeruser
```

once the user is created we are now using it 
```docker
USER        dockeruser
```

## Running
As usual :
```bash
docker-compose up -d
```

## Testing

### browser
Browsing to localhost:8081 should display 
```
UID : 1000
GID : 1000
user : docker-user
```

### command-line
```
docker exec -it <CONTAINER_ID> whoami
```
should display
```
docker-user
```