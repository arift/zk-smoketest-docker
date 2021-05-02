# ZooKeeper Smoketest for Docker

More info on Smoketest: [https://github.com/phunt/zk-smoketest](https://github.com/phunt/zk-smoketest).

Source for this container: [https://github.com/phunt/zk-smoketest](https://github.com/phunt/zk-smoketest).

This container will allow you to run ZooKeeper Smoketest against any ZooKeeper cluster. 
Once test is completed, results will be available at localhost:80 by default. 

Provide following parameters: 
```
- CONNECT_STRING  //ZK Connect string. Provide one or more target servers separated by comma. Include ZK client ports as well. Ex: 192.168.1.101:2181,192.168.102:2181
- Z_NODE_COUNT //Default 100
- Z_NODE_SIZE //Default 100
- SERVER_PORT //Default 80
```


### Examples

You can alternatively mount `/output` path to retrieve the output file. 

Sample `docker-compoe.yml` file
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

With output volume attached
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

Serve output on a different port: 

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
