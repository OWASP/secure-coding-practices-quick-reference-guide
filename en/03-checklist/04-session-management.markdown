## Session Management: {#session-management .list-paragraph}

-   Use the server or framework's session management controls. The
    > application should only recognize these session identifiers as
    > valid

-   Session identifier creation must always be done on a trusted system
    > (e.g., The server)

-   Session management controls should use well vetted algorithms that
    > ensure sufficiently random session identifiers

-   Set the domain and path for cookies containing authenticated session
    > identifiers to an appropriately restricted value for the site

-   Logout functionality should fully terminate the associated session
    > or connection

-   Logout functionality should be available from all pages protected by
    > authorization

-   Establish a session inactivity timeout that is as short as possible,
    > based on balancing risk and business functional requirements. In
    > most cases it should be no more than several hours

-   Disallow persistent logins and enforce periodic session
    > terminations, even when the session is active. Especially for
    > applications supporting rich network connections or connecting to
    > critical systems. Termination times should support business
    > requirements and the user should receive sufficient notification
    > to mitigate negative impacts

-   If a session was established before login, close that session and
    > establish a new session after a successful login

-   Generate a new session identifier on any re-authentication

-   Do not allow concurrent logins with the same user ID

-   Do not expose session identifiers in URLs, error messages or logs.
    > Session identifiers should only be located in the HTTP cookie
    > header. For example, do not pass session identifiers as GET
    > parameters

-   Protect server side session data from unauthorized access, by other
    > users of the server, by implementing appropriate access controls
    > on the server

-   Generate a new session identifier and deactivate the old one
    > periodically. (This can mitigate certain session hijacking
    > scenarios where the original identifier was compromised)

-   Generate a new session identifier if the connection security changes
    > from HTTP to HTTPS, as can occur during authentication. Within an
    > application, it is recommended to consistently utilize HTTPS
    > rather than switching between HTTP to HTTPS.

-   Supplement standard session management for sensitive server-side
    > operations, like account management, by utilizing per-session
    > strong random tokens or parameters. This method can be used to
    > prevent [*Cross Site Request
    > Forgery*](#Cross_Site_Request_Forgery) attacks

-   Supplement standard session management for highly sensitive or
    > critical operations by utilizing per-request, as opposed to
    > per-session, strong random tokens or parameters

-   Set the \"secure\" attribute for cookies transmitted over an TLS
    > connection

-   Set cookies with the HttpOnly attribute, unless you specifically
    > require client-side scripts within your application to read or set
    > a cookie\'s value
