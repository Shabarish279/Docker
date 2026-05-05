# Multi‑Stage Dockerfile (Java Application)

This repository contains a multi‑stage Dockerfile that demonstrates how to build and run a Java application efficiently using Docker. The setup separates the **build environment** from the **runtime environment**, resulting in a smaller, cleaner, and more secure container image.

---

## Overview

This Dockerfile:

- Uses a **multi‑stage build**
- Builds a Java application using **Maven**
- Runs the application using a lightweight **JRE image**
- Copies only the final JAR into the runtime image
- Exposes the application on port 8080
- Is intended for learning and best‑practice demonstrations

---

## What Is a Multi‑Stage Build?

A multi‑stage Docker build allows you to:

- Use one stage to **compile/build** the application
- Use another stage to **run** the application
- Exclude unnecessary build tools from the final image

This results in:
- Smaller image size
- Faster deployments
- Improved security

---

## Dockerfile Components

### 1. Build Stage (Stage 1)

- Uses a Maven image with JDK
- Downloads dependencies
- Compiles the source code
- Produces a runnable JAR file

This stage includes:
- Maven
- Source code
- Build cache

> These are **not included** in the final image.

---

### 2. Runtime Stage (Stage 2)

- Uses a lightweight JRE image
- Copies only the built JAR from the build stage
- Runs the application

This stage includes:
- JRE
- Application JAR only

---

### 3. Application Startup

- Uses `ENTRYPOINT` to run the JAR
- Ensures the application starts automatically when the container runs

---

### 4. Network Configuration

- Exposes port `8080`
- Allows access to the application from a browser or API client

---

## 7. How to Build the Image

Make sure you are in the directory containing the Dockerfile, then run:

```bash
docker build -t multi-stage-java-app .
```

---

## 8. How to Run the Container

Make sure you are in the directory containing the Dockerfile, then run:

```bash
docker run -p 8080:8080 jenkins-dockerfile
```
Once the container starts, access Jenkins in a web browser at:
http://localhost:8080
