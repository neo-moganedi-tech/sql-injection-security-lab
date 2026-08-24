# Baseline Testing

## Objective

Before testing for SQL injection, normal application behaviour was established

The purpose of this baseline test was to confirm how the SQL Injection module responded to valid input under normal conditions

## Test Configuration

DVWA was configured and accessible through the local Docker environment

The SQL Injection module was set to the Low security level for the initial testing phase

## Test Performed

A valid user ID was submitted:

```text
1
```

## Expected Behaviour

The application was expected to return the user record associated with the submitted ID

## Result

The application returned a single user record:

* ID: `1`
* First Name: `admin`
* Surname: `admin`

This confirmed that the application was functioning normally and established a known-good baseline before vulnerability testing

## Significance

Establishing normal behaviour made it possible to compare the application's response when controlled SQL injection input was later introduced

The difference between the normal single-record result and the multiple-record result observed during vulnerability testing provided evidence that the input altered the intended database query behaviour

## Outcome

The baseline test was successful

The application returned only the expected record for the submitted user ID, providing a reference point for the subsequent SQL injection test
