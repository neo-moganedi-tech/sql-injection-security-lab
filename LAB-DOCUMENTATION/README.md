# SQL Injection Security Lab
Overview:

This project documents a hands-on SQL injection security lab conducted in an isolated local environment using Docker and Damn Vulnerable Web Application (DVWA)

The lab demonstrates how insecure handling of user input can affect SQL query behaviour, resulting in unintended database records being returned. The vulnerability was tested in DVWA at different security levels to compare vulnerable and more restrictive behaviour

The purpose of the lab was to gain practical experience in:

- Deploying an intentionally vulnerable web application
- Establishing normal application behaviour
- Demonstrating SQL injection in a controlled environment
- Comparing application behaviour at different security levels
- Analysing the underlying implementation
- Understanding secure SQL query practices

# Lab Environment

The lab was built on a Windows host using:

- Windows
- Windows Subsystem for Linux 2 (WSL 2)
- Docker Desktop
- DVWA (Damn Vulnerable Web Application)
- Apache/PHP
- MySQL/MariaDB
- Web browser

DVWA was deployed as a Docker container and accessed locally through:

http://127.0.0.1:8080

The container was bound to the local loopback interface to keep the intentionally vulnerable application accessible only from the local machine

# Lab Objectives

The objectives of this lab were to:

- Configure a local environment capable of running an intentionally vulnerable web application
- Deploy DVWA using Docker
- Establish a normal database query baseline
- Demonstrate SQL injection in a controlled environment
- Observe the impact of altered SQL query logic
- Compare the behaviour of the application at Low and High security levels
- Inspect the High-security implementation
- Identify secure development practices that would provide stronger protection against SQL injection
- Testing Summary
- Normal Query Behaviour

A normal user ID was submitted to establish expected application behaviour

The application returned a single corresponding user record

# SQL Injection at Low Security

The SQL Injection module was tested at the Low security level using controlled lab input designed to alter the intended query logic

The application returned multiple user records instead of the single expected record, demonstrating the SQL injection vulnerability

# High Security Comparison

The DVWA security level was changed to High and the same test was repeated

The test did not produce the same multiple record result observed at the Low security level. The High security implementation was also inspected to better understand the change in application behaviour

# Key Findings

The lab demonstrated that:

- Directly incorporating untrusted input into SQL queries can allow query logic to be manipulated
- A normal application input produced the expected single-record result
- The controlled SQL injection test at Low security caused multiple records to be returned
- Changing the application's security configuration altered the behaviour of the same test
- The High-security implementation changed the input flow by using a session variable
- The inspected High security source still dynamically constructed an SQL query, meaning parameterized queries would provide a stronger remediation

# Recommended Remediation

A stronger defence against SQL injection includes:

- Using parameterized queries or prepared statements
- Avoiding direct interpolation of untrusted input into SQL statements
- Applying server side input validation
- Using least-privilege database accounts
- Preventing detailed database errors from being exposed to users
- Conducting regular security testing and code reviews
