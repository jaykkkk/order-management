FROM eclipse-temurin:25-jdk-alpine

WORKDIR /app

# Copy Maven wrapper and dependencies
COPY pom.xml .
COPY mvnw .
COPY .mvn .mvn
RUN chmod +x mvnw
RUN ./mvnw dependency:go-offline -B

# Copy source and build the project
COPY src ./src
RUN ./mvnw package -DskipTests

# Expose the Eureka default port
EXPOSE 8761

# Run the Eureka server JAR
CMD ["java", "-jar", "target/discovery-server-0.0.1-SNAPSHOT.jar"]
