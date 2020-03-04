##multi-stage builds
## build
#FROM openjdk:8-jdk-alpine
#
#RUN apk add --no-cache unzip
#
#RUN wget -nv -q -O /tmp/apache-maven-3.6.3-bin.zip https://www-us.apache.org/dist/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip && \
#    unzip -o /tmp/apache-maven-3.6.3-bin.zip -d /tmp
#
#RUN mkdir /app
#
#COPY . /app
#
#WORKDIR /app
#
#RUN /tmp/apache-maven-3.6.3/bin/mvn -B -e clean test package
#
#RUN ls -ltr
#
## runtime
#FROM openjdk:8-jre-alpine
#
#RUN apk add --no-cache python py-pip sudo openssl && \
#    pip install awscli && \
#    apk --purge -v del py-pip
#
#RUN mkdir -p /app/tests && \
#    chmod -R 777 /app
#
#COPY ./docker/entrypoint.sh /app/entrypoint.sh
#
#COPY ./docker/keytool-sudo /etc/sudoers.d/keytool
#
#RUN mkdir -p /oc/local && \
#    chmod 755 /app/entrypoint.sh
#
#COPY --from=0 /app/target/mdm-api-0.0-SNAPSHOT.jar  /app/app.jar
#COPY --from=0 /app/target/surefire-reports/*.xml /app/tests/
#
#USER nobody
#
#WORKDIR /app
#
#ENTRYPOINT ["/app/entrypoint.sh"]

# runtime
##multi-stage builds
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
#RUN mv /opt/datasync/ /app/datasync/
WORKDIR /app
##
### runtime
#FROM openjdk:8-jre-alpine
#RUN apk update
#RUN chmod -R 777 /app
#
#COPY --from=0 /app/datasync/  /app/datasync/
#USER nobody
#
#WORKDIR /app
#ENTRYPOINT ["java", "-jar", "datasync.jar"]

