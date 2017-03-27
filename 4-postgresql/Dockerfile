FROM openjdk:8-jre

WORKDIR /flyway

ENV FLYWAY_VERSION 4.1.2

RUN curl -L https://repo1.maven.org/maven2/org/flywaydb/flyway-commandline/${FLYWAY_VERSION}/flyway-commandline-${FLYWAY_VERSION}.tar.gz -o flyway-commandline-${FLYWAY_VERSION}.tar.gz \
  && tar -xzf flyway-commandline-${FLYWAY_VERSION}.tar.gz --strip-components=1 \
  && rm flyway-commandline-${FLYWAY_VERSION}.tar.gz \
  && ln -s /flyway/flyway /usr/local/bin/flyway

ENV POSTGRESQL_DRIVER_VERSION 7.2

RUN wget https://repo1.maven.org/maven2/postgresql/postgresql/${POSTGRESQL_DRIVER_VERSION}/postgresql-${POSTGRESQL_DRIVER_VERSION}.jar \
  && mv postgresql-${POSTGRESQL_DRIVER_VERSION}.jar drivers

ENTRYPOINT ["flyway"]
CMD ["--help"]
