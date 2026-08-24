# SQL Injection Testing

## Objective

The objective of this test was to determine whether user-controlled input could alter the intended SQL query behaviour within the DVWA SQL Injection module

All testing was performed locally against DVWA, an intentionally vulnerable application, in a controlled lab environment

## Test Configuration

The DVWA SQL Injection module was configured to the Low security level

A normal query had already been performed using a valid user ID to establish expected behaviour

The baseline test returned a single user record

## Controlled Test

A controlled SQL injection input was submitted through the User ID field:

```text
1' OR '1'='1
```

The purpose of this test was to determine whether the supplied input could alter the logic of the SQL query

## Result

Unlike the baseline test, which returned only one user record, the controlled test caused the application to return multiple user records

The returned records included multiple users from the DVWA database

This demonstrated that the application accepted input that changed the intended query behaviour

## Analysis

The difference between the baseline result and the controlled test result indicated that the application was vulnerable to SQL injection at the Low security level

The application should have treated the supplied value strictly as data. Instead, the input influenced the logic used to retrieve database records

## Security Impact

If a similar vulnerability existed in a real-world application, an attacker could potentially manipulate database queries and gain access to information beyond the intended scope of the request

The impact of SQL injection can include:

* Unauthorized access to database records
* Exposure of sensitive information
* Modification or deletion of data, depending on database permissions
* Authentication bypass in vulnerable implementations

The exact impact depends on the application's design and the permissions assigned to the database account

## Outcome

The controlled test successfully demonstrated SQL injection behaviour within the intentionally vulnerable DVWA application

The Low security configuration returned multiple records, compared with the single record returned during baseline testing
