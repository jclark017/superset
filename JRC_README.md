### Install Instructions
Use Option 1

https://superset.apache.org/docs/installation/docker-compose

#### Setup after install

##### Map in the data environment to the docker-compose.yml
x-superset-volumes:
  - /home/clark/source/callcenter/data/dw:/opt/dw 
##### Launch build environment
```
sudo docker compose -f docker-compose-image-tag.yml up
```

After launching the non-dev environment 

The default container name that you want in the non-dev environment is "superset_app"

```
$ docker exec -it superset_app bash
```

I'm not sure when or where this change was made, but the docker-init.sh script is now at /app/docker/docker-init.sh.
```
root@5c52fe612108:/app# docker/docker-init.sh
```

### Map

### DuckDB install (inside docker bash)
https://medium.com/free-or-open-source-software/how-to-connect-apache-superset-with-duckdb-memory-355da43aa410

```
root@5c52fe612108:/app# pip install duckdb duckdb-engine
```

New Connection: duckdb:///:memory:

### Export/Import Dashboards (inside docker bash)
```
# cd ../opt/dw/bi
# superset export-dashboards
```