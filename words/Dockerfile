# FROM debian:bullseye
# RUN apt-get update && apt-get install -y maven && apt-get clean
# COPY pom.xml pom.xml
# RUN mvn verify
# COPY src src
# RUN mvn verify 
# WORKDIR /target
# CMD [ "java -Xmx8m -Xms8m -jar words.jar" ] 
# EXPOSE 8080


## Correction

# 1.
# FROM ubuntu
# RUN apt-get update 
# RUN apt-get install -y maven

# COPY . .
# RUN mvn verify

# CMD exec java -Xmx8m -Xms8m -jar words.jar

# 2
FROM maven AS builder
COPY pom.xml .
RUN mvn verify
COPY src src
RUN mvn verify

FROM openjdk:8-jre-alpine
COPY --from=builder /target /target
CMD exec java -Xmx8m -Xms8m -jar target/words.jar
