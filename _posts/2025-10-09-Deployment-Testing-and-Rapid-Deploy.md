---
layout: post
title: Application Containers
longtitle: Docker & Podman - Application Containers
tags:
- containers
- containerization
- docker
- podman
date: 2025-10-09
---

# Docker

**Docker** is a platform designed to make it easier to create, deploy, and run applications by using containers .

A **container** is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries, and settings.

## Key Concepts

### Isolation

Containers isolate the application from its environment and ensure it runs uniformly regardless of where it's deployed (e.g., on a developer's laptop, a company's server, or in the cloud). This solves the common problem of "it works on my machine!"

### Images

A Docker image is a read-only template with instructions for creating a Docker container.

### Containers

A Docker container is a runnable instance of an image.


Essentially, Docker packages an application and its dependencies into a standardized unit for software development.

## Installation

[https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/)

## Usage

### Use a Pre-Built Image

Find the containerized application that you need at [https://hub.docker.com/search](https://hub.docker.com/search) and pull a copy.

```shell
docker pull image/name
```

Once `docker pull` succeeds, you need to prepare a `docker-compose.yml` file to be able to run `docker compose up -d`

```shell
docker compose up -d 
```

> ##### Info
>
> Read the terminal output carefully. Docker will generally tell you how to access the application using a browser.
>
{: .block-info}
---

### Use a Git `docker-compose.yml`

It is also common that the application development team provides a `docker-compose.yml` from their source repository in order for others to be able to quickly run and test their application.

For our example, we will use the Wazuh project's github repository to retrieve a `docker compose file` from github.


[Wazuh]({% link _posts/2025-10-09-Wazuh-SIEM.md %})

---

# Podman

**Podman** (short for Pod Manager) is an open-source, Linux-native container engine designed to manage containers and container images under the Open Container Initiative (OCI) standards.

It is often seen as a direct alternative to Docker, but with a key architectural difference.

## Key Features

### Daemonless Architecture

Unlike Docker, Podman does not rely on a persistent, central background service (daemon) to run containers. Each container is started directly as a child process of the podman command, which simplifies the architecture and can reduce resource overhead.

### Rootless Containers

A major security feature is its default support for running containers as a non-root user. This significantly reduces security risks by minimizing the privileges a compromised container has on the host system.

### Docker Compatibility

Podman's Command Line Interface (CLI) is highly compatible with Docker's, allowing users to switch easily—often by simply aliasing the docker command to podman.

### Pod Management

Podman natively includes the concept of Pods (a group of one or more containers that share resources like a network namespace), which directly aligns with the architecture used by Kubernetes. This makes it an excellent tool for local development and testing before deploying to a Kubernetes cluster.

## Installation

[https://podman.io/docs/installation](https://podman.io/docs/installation)

---

> ##### Info
> 
> Application containers allow for quick assessments about a tool or web application that we need to run. Once a container has been configured to specifications needed, it can also be deployed to a production setup.
>
>
{: .block-tip}


