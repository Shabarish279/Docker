# ---------- STAGE 1: Build ----------
FROM maven:3.9.6-eclipse-temurin-17 AS build

WORKDIR /app

# Copy pom.xml and download dependencies
COPY pom.xml .
RUN mvn dependency:go-offline

# Copy source code and build JAR
COPY src ./src
RUN mvn clean package -DskipTests

# ---------- STAGE 2: Run ----------
FROM eclipse-temurin:17-jre

WORKDIR /app

# Copy only the final JAR from build stage
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
