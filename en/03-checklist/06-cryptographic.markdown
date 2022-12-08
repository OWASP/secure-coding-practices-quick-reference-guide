## Cryptographic Practices: {#cryptographic-practices .list-paragraph}

-   All cryptographic functions used to protect secrets from the
    > application user must be implemented on a trusted system (e.g.,
    > The server)

-   Protect master secrets from unauthorized access

-   Cryptographic modules should fail securely

-   All random numbers, random file names, random GUIDs, and random
    > strings should be generated using the cryptographic module's
    > approved random number generator when these random values are
    > intended to be un-guessable

-   Cryptographic modules used by the application should be compliant to
    > FIPS 140-2 or an equivalent standard. (See
    > <http://csrc.nist.gov/groups/STM/cmvp/validation.html>)

-   Establish and utilize a policy and process for how cryptographic
    > keys will be managed

