# neo4j

1. Pull the image from [DockerHub > neo4j](https://hub.docker.com/_/neo4j)
   ```bash
   docker pull neo4j:community
   ```
2. Run Neo4j container (as per instructions [here](https://neo4j.com/developer/docker-run-neo4j/), add
`--env NEO4J_ACCEPT_LICENSE_AGREEMENT=y` if you're using `neo4j:enterprise` and have appropriate license)
   ```bash
   # Note winpty and extra / in the volume argument before $PWD are due to Windows + Git Bash compatibility issue
   winpty docker run --name local-neo4j -p7474:7474 -p7687:7687 -v /$PWD/neo4j-data/data:/data -v /$PWD/neo4j-data/logs:/logs -v /$PWD/neo4j-data/import:/var/lib/neo4j/import -v /$PWD/neo4j-data/plugins:/plugins --env NEO4J_AUTH=neo4j/test -d neo4j:community
   ```
