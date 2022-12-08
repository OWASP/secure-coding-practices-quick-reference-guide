## Authentication and Password Management: {#authentication-and-password-management .list-paragraph}

-   Require authentication for all pages and resources, except those
    > specifically intended to be public

-   All authentication controls must be enforced on a trusted system
    > (e.g., The server)

-   Establish and utilize standard, tested, authentication services
    > whenever possible

-   Use a centralized implementation for all authentication controls,
    > including libraries that call external authentication services

-   Segregate authentication logic from the resource being requested and
    > use redirection to and from the centralized authentication control

-   All authentication controls should fail securely

-   All administrative and account management functions must be at least
    > as secure as the primary authentication mechanism

-   If your application manages a credential store, it should ensure
    > that only cryptographically strong one-way salted hashes of
    > passwords are stored and that the table/file that stores the
    > passwords and keys is write-able only by the application. (Do not
    > use the MD5 algorithm if it can be avoided)

-   Password hashing must be implemented on a trusted system (e.g., The
    > server).

-   Validate the authentication data only on completion of all data
    > input, especially for [*sequential
    > authentication*](#Sequential_Authentication) implementations

-   Authentication failure responses should not indicate which part of
    > the authentication data was incorrect. For example, instead of
    > \"Invalid username\" or \"Invalid password\", just use \"Invalid
    > username and/or password\" for both. Error responses must be truly
    > identical in both display and source code

-   Utilize authentication for connections to external systems that
    > involve sensitive information or functions

-   Authentication credentials for accessing services external to the
    > application should be encrypted and stored in a protected location
    > on a trusted system (e.g., The server). The source code is NOT a
    > secure location

-   Use only HTTP POST requests to transmit authentication credentials

-   Only send non-temporary passwords over an encrypted connection or as
    > encrypted data, such as in an encrypted email. Temporary passwords
    > associated with email resets may be an exception

-   Enforce password complexity requirements established by policy or
    > regulation. Authentication credentials should be sufficient to
    > withstand attacks that are typical of the threats in the deployed
    > environment. (e.g., requiring the use of alphabetic as well as
    > numeric and/or special characters)

-   Enforce password length requirements established by policy or
    > regulation. Eight characters is commonly used, but 16 is better or
    > consider the use of multi-word pass phrases

-   Password entry should be obscured on the user\'s screen. (e.g., on
    > web forms use the input type \"password\")

-   Enforce account disabling after an established number of invalid
    > login attempts (e.g., five attempts is common). The account must
    > be disabled for a period of time sufficient to discourage brute
    > force guessing of credentials, but not so long as to allow for a
    > denial-of-service attack to be performed

-   Password reset and changing operations require the same level of
    > controls as account creation and authentication.

-   Password reset questions should support sufficiently random answers.
    > (e.g., \"favorite book\" is a bad question because "The Bible" is
    > a very common answer)

-   If using email based resets, only send email to a pre-registered
    > address with a temporary link/password

-   Temporary passwords and links should have a short expiration time

-   Enforce the changing of temporary passwords on the next use

-   Notify users when a password reset occurs

-   Prevent password re-use

-   Passwords should be at least one day old before they can be changed,
    > to prevent attacks on password re-use

-   Enforce password changes based on requirements established in policy
    > or regulation. Critical systems may require more frequent changes.
    > The time between resets must be administratively controlled

-   Disable \"remember me\" functionality for password fields

-   The last use (successful or unsuccessful) of a user account should
    > be reported to the user at their next successful login

-   Implement monitoring to identify attacks against multiple user
    > accounts, utilizing the same password. This attack pattern is used
    > to bypass standard lockouts, when user IDs can be harvested or
    > guessed

-   Change all vendor-supplied default passwords and user IDs or disable
    > the associated accounts

-   Re-authenticate users prior to performing critical operations

-   Use [*Multi-Factor Authentication*](#Multi_Factor_Authentication)
    > for highly sensitive or high value transactional accounts

-   If using third party code for authentication, inspect the code
    > carefully to ensure it is not affected by any malicious code
