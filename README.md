# Kaiburr CI/CD Pipeline

This repository contains the **CI/CD pipeline** for the Kaiburr backend application.

The pipeline is built using **GitHub Actions** and performs **automatic build and Docker image creation** whenever there is a push to the `main` branch.

---

## Workflow Overview

The CI/CD pipeline includes the following **main steps**:

1. **Set up job** – Initializes the GitHub Actions runner environment.
2. **Checkout repository** – Pulls the latest backend code (`kaiburr-backend`) from GitHub.
3. **Set up JDK 21** – Installs Java 21 to compile the Maven project.
4. **Build with Maven** – Compiles the Java backend and generates a JAR file.
5. **Build Docker image** – Builds a Docker image from the backend folder.
6. **Upload JAR artifact** – Uploads the generated JAR file as an artifact for later download or deployment.
7. **Post-steps** – GitHub automatically runs cleanup steps like `post-build Docker image`, `post-setup JDK`, `post-checkout repository`, and finalizes the job.

> **Note:** The post-steps are handled automatically and do not need separate screenshots.

---

## How to Use

- The pipeline is **automatically triggered** on push to `main`.
- The JAR artifact can be downloaded from the workflow run **Actions tab** on GitHub.
- Docker image is built **locally on the runner**, not pushed to Docker Hub.  

---

## Notes

- The pipeline can be extended to:
  - Push Docker images to a registry (Docker Hub, GHCR)
  - Run automated tests before building
  - Deploy to Kubernetes after successful build
