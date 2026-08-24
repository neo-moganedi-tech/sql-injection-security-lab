# Security Comparison

## Objective

This section compares the behaviour of the DVWA SQL Injection module at the Low and High security levels

The purpose was to observe how changes in the application's implementation affected the result of the same controlled SQL injection test

## Low Security Behaviour

At the Low security level, the SQL Injection module accepted user input directly through the User ID field

A normal test using User ID `1` returned a single record.

A controlled SQL injection test was then performed using:

```text
1' OR '1'='1
```

Unlike the baseline test, this input caused the application to return multiple user records

This demonstrated that the supplied input was able to alter the intended database query behaviour

## High Security Behaviour

The DVWA security level was changed to High

At this level, the User ID was no longer entered directly on the main SQL Injection page. Instead, DVWA used a separate input window and stored the value in a session variable

The same controlled test input was submitted and the result was compared with the Low security behaviour

The application did not return the multiple user records observed during the Low security test. Instead, only the expected user record was returned

## Source Code Observation

The High security implementation was inspected to understand the change in behaviour

The application retrieved the ID from a session variable before constructing the SQL query:

```php
$id = $_SESSION['id'];
```

The query was still dynamically constructed using that value:

```php
$query = "SELECT first_name, last_name FROM users WHERE user_id = '$id' LIMIT 1;";
```

This is an important distinction: the observed High-security behaviour prevented the specific test from producing the same multiple-record result, but the implementation shown does not demonstrate parameterized queries

## Comparison

| Test                   | Low Security                  | High Security                   |
| ---------------------- | ----------------------------- | ------------------------------- |
| Normal ID `1`          | Returned one record           | Returned one record             |
| Controlled test input  | Returned multiple records     | Did not return multiple records |
| Input handling         | Direct User ID input          | Session-based input flow        |
| SQL query construction | Vulnerable behaviour observed | Dynamic SQL still present       |

## Key Finding

The comparison showed that changing the application's security level changed the result of the controlled test

However, preventing one specific test from succeeding is not the same as implementing a complete remediation

A stronger defence against SQL injection would use parameterized queries or prepared statements so that user-controlled values are handled as data rather than being incorporated directly into SQL query syntax

## Outcome

The Low vs High comparison successfully demonstrated how changes in application input handling can affect observed SQL injection behaviour

The source review also highlighted the importance of examining the underlying implementation rather than assuming that a security setting fully eliminates a vulnerability
