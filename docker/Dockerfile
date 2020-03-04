#multi-stage builds
## build
FROM openjdk:8-jre-alpine


RUN apk update && apk add bash expect
RUN mkdir -p /app/CDataSync && chmod -R 777 /app
COPY ./CDataSync /app/CDataSync
RUN ls -al /app/CDataSync
RUN test -f /app/CDataSync/setup.jar
RUN test -f /app/CDataSync/datasync.war
COPY ./docker/setup_cdata_sync.sh /app/setup_cdata_sync.sh
RUN chmod 775 /app/setup_cdata_sync.sh
RUN /app/setup_cdata_sync.sh
RUN mv /opt/datasync/ /app/datasync/
WORKDIR /app
#
## runtime
FROM openjdk:8-jre-alpine
RUN apk update && apk add bash
RUN mkdir /app
COPY --from=0 /app/datasync/  /app/datasync/
RUN chmod -R 777 /app
RUN ls -al /app/datasync

VOLUME /app/datasync/db

WORKDIR /app
#For debugging
#CMD tail -f /dev/null
ENTRYPOINT ["java", "-jar", "/app/datasync/datasync.jar"]

