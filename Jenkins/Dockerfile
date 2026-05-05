# Use Java 11 as the base runtime environment
FROM openjdk:11-jdk

# Metadata information for the image
LABEL maintainer="Sai Shabarish"
LABEL environment="Dev"

# Define a directory inside the container for application files
ENV APP_DIR=/opt/jenkins

# Create the application directory
RUN mkdir -p ${APP_DIR}

# Set the working directory for subsequent instructions
WORKDIR ${APP_DIR}

# Fetch the Jenkins WAR file and place it in the working directory
ADD https://ftp.yz.yamagata-u.ac.jp/pub/misc/jenkins/war/2.397/jenkins.war jenkins.war

# Jenkins listens on port 8080
EXPOSE 8080

# Define the main executable for the container
ENTRYPOINT ["java", "-jar", "jenkins.war"]
