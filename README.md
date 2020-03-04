# CDATA Sync Docker
The goal of this projec is to dockerize the application named, "CDATA Sync"
## Vendor Application Description
CData Sync allows you to move data from 200+ supported sources to a destination of your choice. CData Sync supports moving data to relational databases (SQL Server, Oracle, PostgreSQL, etc.), cloud data warehouses (Amazon Redshift, Snowflake, Google Big Query, etc.), and other big data systems (Amazon S3, Azure Data Lake, Kafka, etc.).
## Vendor Documentation
* http://cdn.cdata.com/help/ASE/sync/

## Steps to Run container
1. Download the java edition from CDATA from https://www.cdata.com/sync/download/
1. Copy the files datasync.war and setup.jar from download into this project folder as CDataSync/datasync.war and CDataSync/setup.jar
1. docker-compose -f docker-compose.yml build
1. docker-compose up

## Common Docker Commands
### Build Docker Container
`docker-compose -f docker-compose.yml build`

### Run Docker Container Locally
This will run the application and when the terminal close, the container will be removed

`docker run -it -p 127.0.0.1:8181:8181 --rm localhost/cdata-sync:latest`

### List local containers
`docker ps -a`

### SSH into local docker container
`docker exec -it <container-id>`

### Additional Docker Commands
#### Run Docker Container Locally with Entrypoint
`docker run -it --rm --entrypoint "sh" localhost/cdata-sync:latest`

#### Copy file from docker contatiner to local host
`docker cp <container-id>:/file/path/within/container /host/path/target`

### Tools
The tools folder is a place to save tools which need to be tracked, but are not used by the docker build process.

autoexpect
* Generate an Expect script from watching a session
* Not available in apk-get repo
* http://expect.sourceforge.net/example/autoexpect.man.html
* http://kiranshashi-cygwin.blogspot.com/2015/02/installing-autoexpect-on-linux-cygwin.html