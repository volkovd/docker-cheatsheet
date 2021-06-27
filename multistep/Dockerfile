#Step 1: Install Jhipster in node.js image and generate application
FROM node:14-alpine as generate
WORKDIR '/app'
COPY application.jh .
RUN npm install -g generator-jhipster
RUN jhipster jdl --skip-prompts --no-insight application.jh
RUN npm install

#Step 2: Build application generated in previous step
FROM maven:3.8.1-jdk-11-slim as build
WORKDIR '/app'
COPY --from=generate /app /app
RUN mvn dependency:go-offline -B
RUN mvn package -Pdev,webapp

#Step 3: Deploy Application in JRE image
FROM adoptopenjdk/openjdk11:jre-11.0.11_9-alpine
WORKDIR '/app'
COPY --from=build /app/target/jh-demo-app-0.0.1-SNAPSHOT.jar /app
cmd ["java", "-jar", "jh-demo-app-0.0.1-SNAPSHOT.jar"]

