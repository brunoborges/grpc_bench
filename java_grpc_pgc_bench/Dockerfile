FROM adoptopenjdk:14.0.2_8-jre-hotspot-bionic

WORKDIR /app
COPY java_grpc_bench /app
COPY proto/helloworld/helloworld.proto /app/src/main/proto/helloworld.proto

RUN /app/gradlew installDist

ENV GRPC_SERVER_CPUS "2"
ENV PGC "-XX:+UseParallelGC -XX:ParallelGCThreads=${GRPC_SERVER_CPUS}"
ENV JAVA_OPTS "${PGC} -XX:MinRAMPercentage=70 -XX:MaxRAMPercentage=70"

ENTRYPOINT [ "/app/build/install/examples/bin/hello-world-server" ]

