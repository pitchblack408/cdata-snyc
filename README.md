
docker-compose -f docker-compose.yml build
1. docker run -it --rm --entrypoint "sh" localhost/cdata-sync:latest
OR
1. docker run -it --rm localhost/cdata-sync:latest
1. docker ps -a
1. docker exec -it <container-name>

docker cp <containerId>:/file/path/within/container /host/path/target

docker cp 616f62f4b2c3:/app/script.exp .