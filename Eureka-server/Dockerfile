FROM maven:3.8.5-openjdk-17-slim AS eurekaBackendBuild
WORKDIR /root/src/backend
COPY . .
RUN mvn package  -DskipTests

FROM openjdk:17 AS eurekaBackendRuntime
WORKDIR /app
COPY --from=eurekaBackendBuild /root/src/backend/target/eureka-exe.jar ./
EXPOSE 8761
CMD java -jar eureka-exe.jar
