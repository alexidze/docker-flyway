FROM openjdk:8-jre-alpine

RUN apk --no-cache add openssl

WORKDIR /flyway

ENV FLYWAY_VERSION 4.1.2

RUN wget https://repo1.maven.org/maven2/org/flywaydb/flyway-commandline/${FLYWAY_VERSION}/flyway-commandline-${FLYWAY_VERSION}.tar.gz \
  && tar -xzf flyway-commandline-${FLYWAY_VERSION}.tar.gz \
  && mv flyway-${FLYWAY_VERSION}/* . \
  && rm flyway-commandline-${FLYWAY_VERSION}.tar.gz \
  && sed -i 's/bash/sh/' /flyway/flyway \
  && ln -s /flyway/flyway /usr/local/bin/flyway

ENV MYSQL_DRIVER_VERSION 5.1.41

RUN wget https://repo1.maven.org/maven2/mysql/mysql-connector-java/${MYSQL_DRIVER_VERSION}/mysql-connector-java-${MYSQL_DRIVER_VERSION}.jar \
  && mv mysql-connector-java-${MYSQL_DRIVER_VERSION}.jar drivers

ENTRYPOINT ["flyway"]
CMD ["--help"]
