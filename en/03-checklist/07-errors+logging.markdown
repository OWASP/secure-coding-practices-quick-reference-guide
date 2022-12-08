## Error Handling and Logging: {#error-handling-and-logging .list-paragraph}

-   Do not disclose sensitive information in error responses, including
    > system details, session identifiers or account information

-   Use error handlers that do not display debugging or stack trace
    > information

-   Implement generic error messages and use custom error pages

-   The application should handle application errors and not rely on the
    > server configuration

-   Properly free allocated memory when error conditions occur

-   Error handling logic associated with security controls should deny
    > access by default

-   All logging controls should be implemented on a trusted system
    > (e.g., The server)

-   Logging controls should support both success and failure of
    > specified security events

-   Ensure logs contain important [*log event data*](#Log_Event_Data)

-   Ensure log entries that include un-trusted data will not execute as
    > code in the intended log viewing interface or software

-   Restrict access to logs to only authorized individuals

-   Utilize a master routine for all logging operations

-   Do not store sensitive information in logs, including unnecessary
    > system details, session identifiers or passwords

-   Ensure that a mechanism exists to conduct log analysis

-   Log all input validation failures

-   Log all authentication attempts, especially failures

-   Log all access control failures

-   Log all apparent tampering events, including unexpected changes to
    > state data

-   Log attempts to connect with invalid or expired session tokens

-   Log all system exceptions

-   Log all administrative functions, including changes to the security
    > configuration settings

-   Log all backend TLS connection failures

-   Log cryptographic module failures

-   Use a cryptographic hash function to validate log entry integrity
