### Install Instructions
Use Option 1

https://superset.apache.org/docs/installation/docker-compose

#### Setup after install

## Swap
Digital Ocean doesn't create swap space. Use this to make a 1GB swap: https://linuxize.com/post/how-to-add-swap-space-on-ubuntu-22-04/

##### Map in the data environment to the docker-compose.yml
x-superset-volumes:
  - /home/clark/source/callcenter/data/dw:/opt/dw 

##### Launch build environment
```
# To start
$ docker compose -f docker-compose-image-tag.yml up -d

# To stop: 
$ docker compose -f docker-compose-image-tag.yml down

```

To execute commands in docker after launching the non-dev environment 
```
$ docker exec -it superset_app bash
```

### Map

### DuckDB install (inside docker bash)
https://medium.com/free-or-open-source-software/how-to-connect-apache-superset-with-duckdb-memory-355da43aa410

```
root@5c52fe612108:/app# pip install duckdb duckdb-engine
```

New Connection: duckdb:///:memory:

### Export/Import Dashboards (inside docker bash)
To export
```
# cd ../opt/dw/bi
# superset export-dashboards
```

To import the demo, use the Superset GUI to import the zip file at: https://github.com/jclark017/callcenter/callcenter/data/dw/bi/dashboard_export.zip

### Deploy on digital ocean droplet
```
# on server
> apt install docker.io
> mkdir source
> cd source/
> mkdir callcenter
> gh repo clone https://github.com/jclark017/callcenter.git
> mkdir superset
> gh repo clone https://github.com/jclark017/superset.git

## install docker
> https://medium.com/@piyushkashyap045/comprehensive-guide-installing-docker-and-docker-compose-on-windows-linux-and-macos-a022cf82ac0b

# on local
> sudo sshfs -o allow_other,default_permissions root@174.138.83.200:/root/source /mnt/callcenter
> sudo rsync -a source/callcenter/data/dw/ /mnt/callcenter/callcenter/data/dw
> sudo rsync -a source/callcenter/data/chromadb/ /mnt/callcenter/callcenter/chromadb
```

Browser: https://174.138.83.200:8088/superset/


###
Access: http://174.138.83.200:8088/superset/dashboard/1/?native_filters_key=165bZFvHig68MkxW5OFRGVihewd78MCDK18YYhOjaktPhYzMAlHPMI1YBmYADXH5

