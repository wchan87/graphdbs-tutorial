# blazegraph

[Blazegraph](https://blazegraph.com/) was acquired by Amazon and is allegedly what [Amazon Neptune](https://aws.amazon.com/neptune/)
is built on top of. The Docker image that is being used for this tutorial was created by another organization, [LYRASIS](https://www.lyrasis.org/Pages/Main.aspx).
> Blazegraph is a triplestore and graph database, which is used in the Wikidata SPARQL endpoint.

Alternatively, download the relevant jar from [here](https://github.com/blazegraph/database/releases/latest) and follow the
[Quick Start guide](https://github.com/blazegraph/database/wiki/Quick_Start).

## lyrasis/blazegraph

1. Pull the image from [DockerHub > lyrasis/blazegraph](https://hub.docker.com/r/lyrasis/blazegraph)
    ```bash
    docker pull lyrasis/blazegraph:2.1.5
    ```
2. Run the container and access the UI via http://localhost:8080/bigdata/#splash
   ```bash
   # Note winpty and extra / in the volume argument before $PWD are due to Windows + Git Bash compatibility issue
   winpty docker run --name local-blazegraph -d -p8080:8080 -v /$PWD/blazegraph-data/data:/data lyrasis/blazegraph:2.1.5
   ```

[comment]: # (TODO figure out where the data is stored for the container)
