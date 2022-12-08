## Communication Security: {#communication-security .list-paragraph}

-   Implement encryption for the transmission of all sensitive
    > information. This should include TLS for protecting the connection
    > and may be supplemented by discrete encryption of sensitive files
    > or non-HTTP based connections

-   TLS certificates should be valid and have the correct domain name,
    > not be expired, and be installed with intermediate certificates
    > when required

-   Failed TLS connections should not fall back to an insecure
    > connection

-   Utilize TLS connections for all content requiring authenticated
    > access and for all other sensitive information

-   Utilize TLS for connections to external systems that involve
    > sensitive information or functions

-   Utilize a single standard TLS implementation that is configured
    > appropriately

-   Specify character encodings for all connections

-   Filter parameters containing sensitive information from the HTTP
    > referer, when linking to external sites
