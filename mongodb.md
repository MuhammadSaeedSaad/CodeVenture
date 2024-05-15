# Mongodb

## Install mongodb on ubuntu
1. follow instructions from the [Docs](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/)
2. if you faces the problem that `the keys are invalid` use this [solution](https://www.mongodb.com/docs/manual/reference/installation-ubuntu-community-troubleshooting/#std-label-install-ubuntu-troubleshooting).
___
## Querying
1. Quering documents with specific array elements in an array field use `$elemMatch`.
2. 
___
## enable authentication
1. configure mongodb normaly withou authenticaion
2. open the mongoshand issue the below command `use <yourdBName>` src: [Enable Auth](https://www.mongodb.com/docs/v3.4/tutorial/enable-authentication/).
3. when using the desired DB issue the command
```javascript
db.createUser(
  {
    user: "myTester",
    pwd: "xyz123",
    roles: [ { role: "readWrite", db: "test" },
             { role: "read", db: "reporting" } ]
  }
)
```
1. close mongodb and start it again but this time with the args `--auth`.
2. to authenticate mongosh use `--username <yourUsername> --password <yourPassword> --authenticationDatabase <yourDb`.
___
## creating a replica set using docker-compose
```yaml
version: '3'

services:
  mongo1:
    container_name: m1
    image: mongo
    command: mongod --replSet my-mongo-set
    ports:
      - 3001:27017
    networks:
      - eatery-network

  mongo2:
    container_name: m2
    image: mongo
    command: mongod --replSet my-mongo-set
    ports:
      - 3002:27017
    networks:
      - eatery-network
  
  mongo3:
    container_name: m3
    image: mongo
    command: mongod --replSet my-mongo-set
    ports:
      - 3003:27017
    networks:
      - eatery-network

networks:
  eatery-network:
```
___
## issues with mongodb and solutions
1. problem when `sudo systemctl status mongod` mongo doesn't start.
```bash
× mongod.service - MongoDB Database Server
     Loaded: loaded (/lib/systemd/system/mongod.service; disabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Thu 2023-08-24 13:59:34 EEST; 6s ago
       Docs: https://docs.mongodb.org/manual
    Process: 4423 ExecStart=/usr/bin/mongod --config /etc/mongod.conf (code=exited, status=14)
   Main PID: 4423 (code=exited, status=14)
        CPU: 35ms

أغس 24 13:59:34 m-virtual-machine systemd[1]: Started MongoDB Database Server.
أغس 24 13:59:34 m-virtual-machine mongod[4423]: {"t":{"$date":"2023-08-24T10:59:34.842Z"},"s":"I",  "c":"CONTROL",  "id":7484500, "ctx":"main","msg":"Environment variable MONGODB_CONFIG_OVERRIDE_NOFORK == >
أغس 24 13:59:34 m-virtual-machine systemd[1]: mongod.service: Main process exited, code=exited, status=14/n/a
أغس 24 13:59:34 m-virtual-machine systemd[1]: mongod.service: Failed with result 'exit-code'.
```
**solution**: </br>
`sudo rm -rf /tmp/mongodb-27017.sock`