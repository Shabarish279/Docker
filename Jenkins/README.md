# Jenkins Dockerfile

This repository contains a Dockerfile that demonstrates how to run Jenkins inside a Docker container using OpenJDK 11. The setup avoids installing and configuring Jenkins directly on a virtual machine by running it as a containerized service instead.

---

## Overview

This Dockerfile:

* Uses OpenJDK 11 as the Java runtime environment
* Downloads and runs Jenkins using the WAR file
* Exposes Jenkins on port 8080
* Uses ENTRYPOINT to ensure Jenkins starts automatically
* Is intended for learning and demonstration purposes

---

## Dockerfile Components

### 1. Base Image

* Uses `openjdk:11-jdk`
* Provides the required Java environment for running Jenkins

---

### 2. Image Metadata

* Adds labels to describe the image
* Specifies maintainer and environment information

---

### 3. Environment Configuration

* Defines an application directory inside the container
* Uses an environment variable to manage paths cleanly

---

### 4. Application Setup

* Creates the Jenkins application directory
* Sets the working directory
* Downloads the Jenkins WAR file into the container

---

### 5. Network Configuration

* Exposes port `8080`
* Allows Jenkins to be accessed from a browser

---

### 6. Container Startup

* Uses ENTRYPOINT to define the main process
* Ensures Jenkins always starts when the container runs

---

### 7. How to Build

Make sure you are in the directory containing the Dockerfile, then run:

```bash
docker build -t jenkins-dockerfile .

---

### 8. How to Run the Container

Start the Jenkins container using the following command:

```bash
docker run -p 8080:8080 jenkins-dockerfile
``

Once the container starts, access Jenkins in a web browser at:
http://localhost:8080
