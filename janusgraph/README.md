# JanusGraph

[JanusGraph](https://janusgraph.org/) is a fork of [TitanDB](https://titan.thinkaurelius.com/) which was acquired by
DataStax around 2015-2016.

> JanusGraph is an open source, distributed graph database under The Linux Foundation. JanusGraph is available under the Apache License 2.0. The project is supported by IBM, Google, Hortonworks and Grakn Labs.
> 
> JanusGraph supports various storage backends (Apache Cassandra, Apache HBase, Google Cloud Bigtable, Oracle BerkeleyDB, Scylla). Scalability of JanusGraph depends on the underlying technologies, which are used with JanusGraph. For example, by using Apache Cassandra as a storage backend scaling to multiple datacenters is provided out of the box. 

Instructions are derived from [Getting Started guide](https://docs.janusgraph.org/getting-started/installation/)

1. Pull the image from [DockerHub > janusgraph/janusgraph](https://hub.docker.com/r/janusgraph/janusgraph)
    ```bash
    docker pull janusgraph/janusgraph
    ```
2. Run the container
    ```bash
    docker run --name local-janusgraph -p 8182:8182 -d janusgraph/janusgraph
    ```
3. TBD

[comment]: # (TODO switch from default Oracle Berkeley DB Java Edition to ScyllaDB)
[comment]: # (https://www.scylladb.com/)
[comment]: # (https://hub.docker.com/r/scylladb/scylla)
