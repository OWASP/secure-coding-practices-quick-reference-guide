## Data Protection: {#data-protection .list-paragraph}

-   Implement least privilege, restrict users to only the functionality,
    > data and system information that is required to perform their
    > tasks

-   Protect all cached or temporary copies of sensitive data stored on
    > the server from unauthorized access and purge those temporary
    > working files a soon as they are no longer required.

-   Encrypt highly sensitive stored information, like authentication
    > verification data, even on the server side. Always use well vetted
    > algorithms, see \"Cryptographic Practices\" for additional
    > guidance

-   Protect server-side source-code from being downloaded by a user

-   Do not store passwords, connection strings or other sensitive
    > information in clear text or in any non-cryptographically secure
    > manner on the client side. This includes embedding in insecure
    > formats like: MS viewstate, Adobe flash or compiled code

-   Remove comments in user accessible production code that may reveal
    > backend system or other sensitive information

-   Remove unnecessary application and system documentation as this can
    > reveal useful information to attackers

-   Do not include sensitive information in HTTP GET request parameters

-   Disable auto complete features on forms expected to contain
    > sensitive information, including authentication

-   Disable client side caching on pages containing sensitive
    > information. Cache-Control: no-store, may be used in conjunction
    > with the HTTP header control \"Pragma: no-cache\", which is less
    > effective, but is HTTP/1.0 backward compatible

-   The application should support the removal of sensitive data when
    > that data is no longer required. (e.g. personal information or
    > certain financial data)

-   Implement appropriate access controls for sensitive data stored on
    > the server. This includes cached data, temporary files and data
    > that should be accessible only by specific system users
