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
