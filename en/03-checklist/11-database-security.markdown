## Database Security: {#database-security .list-paragraph}

-   Use strongly typed [*parameterized queries*](#Parameterized_Queries)

-   Utilize input validation and output encoding and be sure to address
    > meta characters. If these fail, do not run the database command

-   Ensure that variables are strongly typed

-   The application should use the lowest possible level of privilege
    > when accessing the database

-   Use secure credentials for database access

-   Connection strings should not be hard coded within the application.
    > Connection strings should be stored in a separate configuration
    > file on a trusted system and they should be encrypted.

-   Use stored procedures to abstract data access and allow for the
    > removal of permissions to the base tables in the database

-   Close the connection as soon as possible

-   Remove or change all default database administrative passwords.
    > Utilize strong passwords/phrases or implement multi-factor
    > authentication

-   Turn off all unnecessary database functionality (e.g., unnecessary
    > stored procedures or services, utility packages, install only the
    > minimum set of features and options required (surface area
    > reduction))

-   Remove unnecessary default vendor content (e.g., sample schemas)

-   Disable any default accounts that are not required to support
    > business requirements

-   The application should connect to the database with different
    > credentials for every trust distinction (e.g., user, read-only
    > user, guest, administrators)
