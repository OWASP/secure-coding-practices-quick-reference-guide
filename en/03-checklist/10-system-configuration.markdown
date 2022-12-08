## System Configuration: {#system-configuration .list-paragraph}

-   Ensure servers, frameworks and system components are running the
    > latest approved version

-   Ensure servers, frameworks and system components have all patches
    > issued for the version in use

-   Turn off directory listings

-   Restrict the web server, process and service accounts to the least
    > privileges possible

-   When exceptions occur, fail securely

-   Remove all unnecessary functionality and files

-   Remove test code or any functionality not intended for production,
    > prior to deployment

-   Prevent disclosure of your directory structure in the robots.txt
    > file by placing directories not intended for public indexing into
    > an isolated parent directory. Then \"Disallow\" that entire parent
    > directory in the robots.txt file rather than Disallowing each
    > individual directory

-   Define which HTTP methods, Get or Post, the application will support
    > and whether it will be handled differently in different pages in
    > the application

-   Disable unnecessary HTTP methods, such as WebDAV extensions. If an
    > extended HTTP method that supports file handling is required,
    > utilize a well-vetted authentication mechanism

-   If the web server handles both HTTP 1.0 and 1.1, ensure that both
    > are configured in a similar manor or insure that you understand
    > any difference that may exist (e.g. handling of extended HTTP
    > methods)

-   Remove unnecessary information from HTTP response headers related to
    > the OS, web-server version and application frameworks

-   The security configuration store for the application should be able
    > to be output in human readable form to support auditing

-   Implement an asset management system and register system components
    > and software in it

-   Isolate development environments from the production network and
    > provide access only to authorized development and test groups.
    > Development environments are often configured less securely than
    > production environments and attackers may use this difference to
    > discover shared weaknesses or as an avenue for exploitation

-   Implement a software change control system to manage and record
    > changes to the code both in development and production

