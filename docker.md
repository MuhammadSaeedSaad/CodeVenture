# Docker
# Basics
## Isolation
1. background
   1. `chroot` (root jail) in linux.
   2. `ulimit` for assiging quota from memory to every user.
   3. `nice/renice` and assiging cpu power for proccesses.


## docker-cli Commands

1. run (create + start) a container (get image file and make a container of it)
```bash
docker run <imageName>

# to override the default command
docker run <imageName> <command>
```

2. list containers
```bash
# running
docker ps
# all containers including stopped ones
docker ps --all
```

3. create a container from an image
```bash
docker create <imageName>
```

4. start a created container
```bash
docker start -a <containerID>
# -a to attach an watch for output and display it.
```

5. starting and exited container
```bash
docker start <containerID>
# cannont provide and override command as the first one cannot be changed
```

6. clear out all stopped containers
```bash
docker system prune
```

7. retrieving logs of a container
```bash
docker logs <containerID>
```
8. stopping containers
```bash
# SIGTERM will wait 10 secs or less for gracefull stopping
docker stop <containerID>

# SIGKILL stopping instantly
docker kill <containerID>
```

9. execute additional command inside a container
```bash
# -it = -i -t .. -i for attaching to the STDIN of the process -t for teletyping and formatting .. without it the prompt will be returned instantly to the container
docker exec -it <containerID> <command>
```

10. get shell access to the container
```bash
# command processors: bash, bash, zsh and sh
docker exec -it <containerID> <command processor>
```

11. starting container with a shell
```bash
docker run <imageName> <command processor>
```
___
## building a custom image
1. create the ``Dockerfile``.
2. hand it to the docker CLI
```bash
docker build <buildcontext>

# tagging the image to use its name instead of imageID
docker build -t <dockerID>/<repoOrProjectName>:<version> <buildContext>
# example
docker build -t mohamed/redis:latest .
# if no version numper specified the latest will be used by default
docker run mohamed/redis
```

3. building an image from a container
```bash
docker commit -c 'CMD ["redis-server"]' <containerID>
```
___
## docker-compose commands

```bash
# run the images from docker-compose.yml and build them if not yet
docker-compose up

# rebuild the images (ex: if we edited a file)
docker-compose up --build

# launch in background
# Note: equivalent to "docker run -d <imageName>"
docker-compose up -d

# stop the containers
docker-compose down
```




