FROM maven:3.8.1-openjdk-11 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy only the POM file to the working directory
COPY pom.xml .

# Download the project dependencies
RUN mvn dependency:go-offline

# Copy the source code to the working directory
COPY src ./src

# Build the application (skipping tests)
RUN mvn package -DskipTests
# Expose port 8080 for the Spring Boot application
EXPOSE 8080

# Set the entrypoint command to run the Spring Boot application
ENTRYPOINT ["java", "-jar", "/app/target/spring-petclinic-2.1.0.war"]
