# Docker Build Maven Stage
FROM maven:3-jdk-8-alpine AS build
# Copy folder in docker
WORKDIR /opt/app
COPY ./ /opt/app
RUN mvn clean install -DskipTests
# Run spring boot in Docker
FROM openjdk:8-jdk-alpine
COPY --from=build /opt/app/target/*.jar ecom-entity.jar
ENTRYPOINT ["java","-jar","/ecom-entity.jar"]