FROM adoptopenjdk:14.0.2_8-jre-hotspot-bionic

WORKDIR /app
COPY java_quarkus_maven_bench /app
COPY proto/helloworld/helloworld.proto /app/src/main/proto/helloworld.proto
ENV LANG='en_US.UTF-8' LANGUAGE='en_US:en'
RUN /app/mvnw package

# Configure the JAVA_OPTIONS, you can add -XshowSettings:vm to also display the heap size.
ENV JAVA_OPTIONS="-Dquarkus.http.host=0.0.0.0 -Djava.util.logging.manager=org.jboss.logmanager.LogManager"

EXPOSE 8080
EXPOSE 9000

ENTRYPOINT [ "java", "-jar", "/app/target/java-quarkus-grpc-bench-0.1-runner.jar" ]