# Findings and Lessons Learned

## Summary of Findings

This lab demonstrated how SQL injection can occur when application input influences the logic of a database query

A normal query using User ID `1` returned a single expected user record

When the SQL Injection module was tested at the Low security level using controlled input, the application returned multiple user records. This demonstrated that the supplied input was able to alter the intended query behaviour

Testing the same input at the High security level did not produce the same multiple record result

## Key Security Findings

### 1. User Input Can Affect SQL Query Logic

The Low-security test demonstrated the risk of allowing untrusted input to influence a database query

Application input should be treated as data rather than executable query syntax

### 2. Baseline Testing Is Important

Establishing normal behaviour before testing made the vulnerability easier to identify

The normal query returned one expected record, providing a clear comparison with the multiple records returned during the SQL injection test

### 3. Security Controls Should Be Analysed, Not Assumed

The High security setting changed the application's behaviour and prevented the specific controlled test from producing the same result

However, source code inspection showed that the SQL query was still dynamically constructed using a value obtained from a session variable

This demonstrated that a security control should not be considered a complete remediation without examining how the underlying application handles data

### 4. Parameterized Queries Provide Stronger Protection

The strongest lesson from the lab was the importance of parameterized queries or prepared statements

These approaches separate SQL query structure from user-supplied data, reducing the risk that input can alter query logic

Additional controls should include:

* Server-side input validation
* Least-privilege database accounts
* Secure error handling
* Regular security testing
* Code reviews

## Technical Skills Demonstrated

This project involved practical experience with:

* Windows and WSL 2 configuration
* Docker Desktop
* Container deployment
* Local application hosting
* Web application security testing
* SQL injection analysis
* Baseline and comparative testing
* Source code inspection
* Security remediation analysis
* Technical documentation

## Conclusion

The lab successfully demonstrated SQL injection behaviour within an intentionally vulnerable application in a controlled local environment

The comparison between Low and High security levels showed how changes to application behaviour can affect the outcome of security testing. Source code inspection further demonstrated the importance of understanding the underlying implementation instead of relying solely on observed results

The primary remediation recommendation is to use parameterized queries or prepared statements and apply additional defence-in-depth controls around database access and input handling

## Lessons Learned

This lab reinforced the importance of:

* Testing applications in controlled environments
* Establishing a known good baseline before security testing
* Comparing vulnerable and more restrictive implementations
* Validating the effectiveness of security controls
* Reviewing source code where possible
* Applying secure coding practices rather than relying on input handling alone

All testing in this project was performed locally against DVWA, an intentionally vulnerable application designed for security training
