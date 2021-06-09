FROM maven:latest AS builder

WORKDIR /usr/src/app
COPY . .  
RUN mvn -f . -X clean package

FROM openjdk:16-jdk-alpine3.13
COPY --from=builder /usr/src/app/target/worker-jar-with-dependencies.jar .
CMD ["java", "-jar", "./worker-jar-with-dependencies.jar"]