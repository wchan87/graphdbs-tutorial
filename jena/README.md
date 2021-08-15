# jena

[Apache Jena](https://jena.apache.org/) is "a free and open source Java framework for building Semantic Web and Linked
Data applications".

## Apache Jena riot

`riot` (RDF I/O technology) command line tools that parses/writes various RDS formats. Refer to the following links for
more information on usage of `riot`:
* [Apache Jena documentation > command line tools](https://jena.apache.org/documentation/io/#command-line-tools)
* [Apache Jena documentation > Tools](https://jena.apache.org/documentation/tools/index.html)

### stain/jena

Source code for the `stain/jena` image can be found on [GitHub > stain/jena-docker > jenta-docker/jena](https://github.com/stain/jena-docker/tree/master/jena)

1. Pull the image from [DockerHub > stain/jena](https://hub.docker.com/r/stain/jena)
    ```bash
    docker pull stain/jena
    ```

[comment]: # (TODO add instructions on how riot and other tools could be leveraged)

## Apache Jena Fuseki

[Apache Jena Fuseki](https://jena.apache.org/documentation/fuseki2/) can be accessed as an UI or web application (see
REST API documentation [here](https://jena.apache.org/documentation/fuseki2/fuseki-server-protocol.html)).
It can also be run within a Docker container, see `jena-fuseki-docker` section or as an embedded server from a Java
application.

> Apache Jena Fuseki is a SPARQL server. It can run as a operating system service, as a Java web application (WAR file), and as a standalone server.
> 
> Fuseki comes in in two forms, a single system “webapp”, combined with a UI for admin and query, and as “main”, a server suitable to run as part of a larger deployment, including with Docker or running embedded. Both forms use the same core protocol engine and same configuration file format.
>
> Fuseki provides the SPARQL 1.1 protocols for query and update as well as the SPARQL Graph Store protocol.
>
> Fuseki is tightly integrated with TDB to provide a robust, transactional persistent storage layer, and incorporates Jena text query.

### stain/jena-fuseki

Source code for the `stain/jena-fuseki` image can be found on [GitHub > stain/jena-docker > jenta-docker/jena-fuseki](https://github.com/stain/jena-docker/tree/master/jena-fuseki)

1. Pull the image from [DockerHub > stain/jena-fuseki](https://hub.docker.com/r/stain/jena-fuseki)
    ```bash
    docker pull stain/jena-fuseki
    ```
2. Create the volume, `stain-fuseki`
   ```bash
   docker volume create stain-fuseki
   ```
3. Run the image with the named volume from previous step
    ```bash
    docker run --name stain-fuseki -d -p 3030:3030 -v stain-fuseki:/fuseki -e ADMIN_PASSWORD=admin -e TDB=2 stain/jena-fuseki
    ```
4. Open the http://localhost:3030/ and use the credentials, `admin:admin` to login

### jena-fuseki-docker

Based on the [instructions](https://jena.apache.org/documentation/fuseki2/fuseki-docker.html) from Apache Jena
documentation, we can build Docker image to run SPARQL server

1. Download the archive file
   ```bash
   curl https://repo1.maven.org/maven2/org/apache/jena/jena-fuseki-docker/4.1.0/jena-fuseki-docker-4.1.0.zip -o jena-fuseki-docker-4.1.0.zip
   ```
2. Unzip the archive file
   ```bash
   unzip jena-fuseki-docker-4.1.0.zip
   ```
3. Build the Docker image
   ```bash
   cd jena-fuseki-docker-4.1.0
   docker-compose build --build-arg JENA_VERSION=4.1.0
   ```
4. Cleanup the downloaded artifacts
   ```bash
   cd ..
   rm -fr jena-fuseki-docker-4.1.0
   rm jena-fuseki-docker-4.1.0.zip
   ```
5. Run the Docker container from built image
   * In-Memory and updatable on http://localhost:3030/ds
   ```bash
   docker run -i --rm -p "3030:3030" --name in-mem-fuseki -t fuseki --mem /ds
   ```
   * Updatable and mounted TBD2 database on http://localhost:3030/ds
   ```bash
   mkdir -p databases/DB2
   docker run -i --rm -p "3030:3030" --mount type=bind,src=$PWD/databases,dst=/fuseki/databases --name mount-fuseki -t fuseki --tdb2 --update --loc databases/DB2 /ds
   ```
