FROM adoptopenjdk:14.0.2_8-jre-hotspot-bionic

WORKDIR /app
COPY java_hotspot_grpc_sgc_bench /app
COPY proto/helloworld/helloworld.proto /app/src/main/proto/helloworld.proto

RUN /app/gradlew installDist

ENV JVM_EXECUTOR_TYPE "single"
ENV GC "-XX:+UseParallelGC"
ENV JAVA_OPTS "${GC} -XX:MinRAMPercentage=70 -XX:MaxRAMPercentage=70"

ENTRYPOINT [ "/app/build/install/examples/bin/hello-world-server" ]
