# CDATA Sync Docker
The goal of this projec is to dockerize the application named, "CDATA Sync"
## Vendor Application Description
CData Sync allows you to move data from 200+ supported sources to a destination of your choice. CData Sync supports moving data to relational databases (SQL Server, Oracle, PostgreSQL, etc.), cloud data warehouses (Amazon Redshift, Snowflake, Google Big Query, etc.), and other big data systems (Amazon S3, Azure Data Lake, Kafka, etc.).
## Vendor Documentation
* http://cdn.cdata.com/help/ASE/sync/
## Common Docker Commands
### Build Docker Container
`docker-compose -f docker-compose.yml build`
### Run Docker Container Locally
`docker run -it --rm localhost/cdata-sync:latest`
### List local containers
`docker ps -a`
### SSH into local docker container
`docker exec -it <container-id>`
### Additional Docker Commands
#### Run Docker Container Locally with Entrypoint
`docker run -it --rm --entrypoint "sh" localhost/cdata-sync:latest`
#### Copy file from docker contatiner to local host
`docker cp <container-id>:/file/path/within/container /host/path/target`