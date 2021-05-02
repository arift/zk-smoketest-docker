# ZooKeeper Smoketest for Docker

More info on Smoketest: [https://github.com/phunt/zk-smoketest](https://github.com/phunt/zk-smoketest).

Source for this container: [https://github.com/arift/zk-smoketest-docker](https://github.com/arift/zk-smoketest-docker).

This container will allow you to run ZooKeeper Smoketest against any ZooKeeper cluster. 
Once test is completed, results will be available at localhost:80 by default. 

Provide following parameters: 
```
- CONNECT_STRING  //ZK Connect string. Provide one or more target servers separated by comma. Include ZK client ports as well. Ex: 192.168.1.101:2181,192.168.102:2181
- Z_NODE_COUNT //Default 100
- Z_NODE_SIZE //Default 100
- SERVER_PORT //Default 80
```
To start this container from command line with minimal arguments, type: 
```
$ docker run -d -e CONNECT_STRING=zknode.example.com:2181 atopcu/zk-smoketest
```

### Running this image with docker-compose
```
version: "3.7"

services:
  app:
    image: atopcu/zk-smoketest:latest
    environment:
      - CONNECT_STRING=zknode1.example.com:2181,zknode2.example.com:2181,zknode3.example.com:2181
      - Z_NODE_COUNT=10
      - Z_NODE_SIZE=10
```

You can alternatively mount `/output` path to save the output file to a directory.
```
version: "3.7"

services:
  app:
    image: atopcu/zk-smoketest:latest
    environment:
      - CONNECT_STRING=zknode1.example.com:2181,zknode2.example.com:2181,zknode3.example.com:2181
      - Z_NODE_COUNT=10
      - Z_NODE_SIZE=10
    volumes:
      - /local/path/to/output:/output
```

Output file can also be accessed by the static web server that starts once the smoketest is over. 

```
version: "3.7"

services:
  app:
    image: atopcu/zk-smoketest:latest
    environment:
      - CONNECT_STRING=zknode1.example.com:2181,zknode2.example.com:2181,zknode3.example.com:2181
      - Z_NODE_COUNT=1000
      - Z_NODE_SIZE=100
      - SERVER_PORT=8080
```
