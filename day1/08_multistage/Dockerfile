FROM gradle:4.10.2-jdk8 as builder
USER root
RUN mkdir -p /app
WORKDIR /app
COPY build.gradle ./
ADD src ./src
RUN gradle build
ENTRYPOINT [ "java", "-jar", "./gs-spring-boot-docker-0.1.0.jar"]