# Lab Environment

## Overview

The SQL Injection Security Lab was conducted in a controlled local environment using Docker and Damn Vulnerable Web Application (DVWA)

The purpose of the environment was to provide an isolated platform for safely demonstrating SQL injection behaviour without interacting with external or unauthorized systems

## Host System

The lab was performed on a Windows host system

Windows Subsystem for Linux 2 (WSL 2) was configured to provide the virtualization environment required by Docker Desktop

## Docker Environment

Docker Desktop was used to deploy and run DVWA as a container

The DVWA image was downloaded and started locally using Docker

The running container was verified using:

```powershell
docker ps
```

The container was bound to:

```text
127.0.0.1:8080
```

This configuration limited access to the local machine

## Vulnerable Application

Damn Vulnerable Web Application (DVWA) was used as the intentionally vulnerable application

DVWA provides a controlled environment for learning about common web application vulnerabilities, including SQL injection

The application was accessed locally through:

```text
http://127.0.0.1:8080
```

After deployment, the DVWA database was initialized and the application was configured for controlled security testing

## Environment Components

The lab environment consisted of:

* Windows host operating system
* Windows Subsystem for Linux 2
* Docker Desktop
* DVWA Docker container
* Apache/PHP web application environment
* MySQL/MariaDB database
* Web browser for application testing

## Isolation

The vulnerable application was intentionally kept within the local lab environment

The Docker container was configured to bind the web application to the loopback interface, preventing access from other devices on the local network

## Outcome

The environment was successfully configured and DVWA was accessible locally, providing the platform used for the SQL injection testing performed in this project
