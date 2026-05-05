# Jenkins Dockerfile

This repository contains a Dockerfile that demonstrates how Jenkins can be run inside a Docker container using OpenJDK 11. The purpose of this setup is to show how Jenkins can be containerized so that it can be started quickly without installing or configuring it directly on a virtual machine.

The Dockerfile uses OpenJDK 11 as the base image, which provides the required Java runtime for Jenkins. Metadata labels are added to describe the image and its intended usage. An environment variable is defined to represent the directory inside the container where Jenkins files are stored. This directory is created and set as the working directory for subsequent operations.

The Jenkins WAR file is downloaded into the container and executed directly. Port 8080 is exposed, which is the default port on which Jenkins listens. The Dockerfile uses ENTRYPOINT to ensure that Jenkins is always started automatically whenever the container runs.

To build the Docker image, run the following command from the directory containing the Dockerfile:

docker build -t jenkins-dockerfile .

Once the image is built, start the container using:

docker run -p 8080:8080 jenkins-dockerfile

After the container starts, Jenkins can be accessed in a web browser at:

http://localhost:8080

This setup is intended for learning and demonstration purposes. Jenkins data is not persisted between container restarts, and no volumes are configured. The Dockerfile focuses on simplicity and clarity to demonstrate basic Docker concepts.

Overall, this example shows how Docker can be used to package and run Jenkins in a portable and consistent manner without manual installation on a server or virtual machine.
