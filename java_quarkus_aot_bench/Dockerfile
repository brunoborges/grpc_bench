FROM oracle/graalvm-ce:20.1.0-java11-ol8 as rel

WORKDIR /app
COPY java_quarkus_maven_bench /app
COPY proto/helloworld/helloworld.proto /app/src/main/proto/helloworld.proto
ENV LANG='en_US.UTF-8' LANGUAGE='en_US:en'
RUN gu install native-image
RUN chmod u+x /app/mvnw \
    && /app/mvnw package -Pnative

EXPOSE 8080
EXPOSE 9000

CMD ["/app/target/java-quarkus-grpc-bench-0.1-runner", "-Dquarkus.http.host=0.0.0.0"]
