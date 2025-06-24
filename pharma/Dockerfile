# Use official Maven image to build the project
FROM maven:3.9.4-eclipse-temurin-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Use JDK image to run the app
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar

# Expose port Spring Boot uses
EXPOSE 8080

# Start the app
ENTRYPOINT ["java", "-jar", "app.jar"]
