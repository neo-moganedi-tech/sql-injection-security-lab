# Evidence

This folder contains screenshots captured during the SQL Injection Security Lab

The evidence supports the environment setup, deployment of DVWA, baseline testing, SQL injection demonstration, security comparison, and verification of the running container

## Screenshot Index

### 01 — WSL 2 Configuration

**File:** `01-wsl2-configuration.png`

Shows that Windows Subsystem for Linux was configured with WSL 2 as the default version, preparing the system for the Docker Desktop backend

---

### 02 — Docker Engine Running

**File:** `02-docker-engine-running.png`

Shows Docker Desktop running successfully after the WSL 2 environment was configured

---

### 03 — DVWA Login Page

**File:** `03-dvwa-login-page.png`

Shows that the Damn Vulnerable Web Application (DVWA) was successfully deployed and accessible through the local environment

---

### 04 — Normal Query Baseline

**File:** `04-normal-query-baseline.png`

Shows the expected application behaviour when a valid User ID was submitted

The application returned a single corresponding user record, establishing a baseline before vulnerability testing

---

### 05 — SQL Injection Vulnerability Demonstrated

**File:** `05-sql-injection-vulnerability-demonstrated.png`

Shows the result of the controlled SQL injection test performed at the DVWA Low security level

Unlike the baseline test, multiple user records were returned, demonstrating that the supplied input altered the intended database query behaviour

---

### 06 — High Security Injection Test

**File:** `06-high-security-injection-test.png`

Shows the result of repeating the controlled test after changing DVWA to the High security level

The same test did not produce the multiple-record result observed during the Low security test

---

### 07 — DVWA Container Running

**File:** `07-dvwa-container-running.png`

Shows the DVWA Docker container running and bound to `127.0.0.1:8080`

This verifies that the intentionally vulnerable application was hosted locally within the lab environment

## Evidence Summary

The screenshots collectively demonstrate:

* WSL 2 configuration
* Docker Desktop running
* Successful DVWA deployment
* Normal application behaviour
* SQL injection behaviour at Low security
* Comparison with High security behaviour
* Verification of the running local Docker container

