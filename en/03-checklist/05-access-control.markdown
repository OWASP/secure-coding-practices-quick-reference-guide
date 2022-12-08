## Access Control: {#access-control .list-paragraph}

-   Use only trusted system objects, e.g. server side session objects,
    > for making access authorization decisions

-   Use a single site-wide component to check access authorization. This
    > includes libraries that call external authorization services

-   Access controls should fail securely

-   Deny all access if the application cannot access its security
    > configuration information

-   Enforce authorization controls on every request, including those
    > made by server side scripts, \"includes\" and requests from rich
    > client-side technologies like AJAX and Flash

-   Segregate privileged logic from other application code

-   Restrict access to files or other resources, including those outside
    > the application\'s direct control, to only authorized users

-   Restrict access to protected URLs to only authorized users

-   Restrict access to protected functions to only authorized users

-   Restrict direct object references to only authorized users

-   Restrict access to services to only authorized users

-   Restrict access to application data to only authorized users

-   Restrict access to user and data attributes and policy information
    > used by access controls

-   Restrict access security-relevant configuration information to only
    > authorized users

-   Server side implementation and presentation layer representations of
    > access control rules must match

-   If [*state data*](#State_Data) must be stored on the client, use
    > encryption and integrity checking on the server side to catch
    > state tampering.

-   Enforce application logic flows to comply with business rules

-   Limit the number of transactions a single user or device can perform
    > in a given period of time. The transactions/time should be above
    > the actual business requirement, but low enough to deter automated
    > attacks

-   Use the \"referer\" header as a supplemental check only, it should
    > never be the sole authorization check, as it is can be spoofed

-   If long authenticated sessions are allowed, periodically re-validate
    > a user's authorization to ensure that their privileges have not
    > changed and if they have, log the user out and force them to
    > re-authenticate

-   Implement account auditing and enforce the disabling of unused
    > accounts (e.g., After no more than 30 days from the expiration of
    > an account's password.)

-   The application must support disabling of accounts and terminating
    > sessions when authorization ceases (e.g., Changes to role,
    > employment status, business process, etc*.*)

-   Service accounts or accounts supporting connections to or from
    > external systems should have the least privilege possible

-   Create an Access Control Policy to document an application\'s
    > business rules, data types and access authorization criteria
    > and/or processes so that access can be properly provisioned and
    > controlled. This includes identifying access requirements for both
    > the data and system resources
