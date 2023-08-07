# Docker

## Commands

1. run (create + start) a container (get image file and make a container of it)
```Powershell
docker run <imageName>
```

2. list containers
```powershell
# running
docker ps
# all containers including stopped ones
docker ps --all
```

3. create a container from an image
```powershell
docker create <imageName>
```

4. start a created container
```powershell
docker start -a <containerID>
# -a to attach an watch for output and display it.
```

5. starting and exited container
```powershell
docker start <containerID>
# cannont provide and override command as the first one cannot be changed
```

6. clear out all stopped containers
```powershell
docker system prune
```

7. retrieving logs of a container
```powershell
docker logs <containerID>
```
8. stopping containers
```powershell
# SIGTERM will wait 10 secs or less for gracefull stopping
docker stop <containerID>

# SIGKILL stopping instantly
docker kill <containerID>
```

9. execute additional command inside a container
```powershell
# -it = -i -t .. -i for attaching to the STDIN of the process -t for teletyping and formatting .. without it the prompt will be returned instantly to the container
docker exec -it <containerID> <command>
```

10. 





