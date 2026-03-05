FROM maven:3.8.6-openjdk-11 AS build
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline -B
COPY src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:11
VOLUME /tmp
WORKDIR /app
COPY --from=build /app/target/demo-0.0.1.jar app.jar
EXPOSE 8081
ENTRYPOINT ["java", "-jar", "/app/app.jar"]
