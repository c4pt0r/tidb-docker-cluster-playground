Dockerized TiDB Cluster Playground
=================

This docker image attempts to simplify the cluster setup for playing and practicing tiup cluster mode.

It contains all the tiops dependencies and code. It uses [Docker Compose](https://github.com/docker/compose) to spin up the five
containers.

To start run

````
    ./up.sh
    docker exec -it tidb-cluster-control bash
````

Run `./up.sh --help` for more info.
