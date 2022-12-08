## General Coding Practices: {#general-coding-practices .list-paragraph}

-   Use tested and approved managed code rather than creating new
    > unmanaged code for common tasks

-   Utilize task specific built-in APIs to conduct operating system
    > tasks. Do not allow the application to issue commands directly to
    > the Operating System, especially through the use of application
    > initiated command shells

-   Use checksums or hashes to verify the integrity of interpreted code,
    > libraries, executables, and configuration files

-   Utilize locking to prevent multiple simultaneous requests or use a
    > synchronization mechanism to prevent race conditions

-   Protect shared variables and resources from inappropriate concurrent
    > access

-   Explicitly initialize all your variables and other data stores,
    > either during declaration or just before the first usage

-   In cases where the application must run with elevated privileges,
    > raise privileges as late as possible, and drop them as soon as
    > possible

-   Avoid calculation errors by understanding your programming
    > language\'s underlying representation and how it interacts with
    > numeric calculation. Pay close attention to byte size
    > discrepancies, precision, signed/unsigned distinctions,
    > truncation, conversion and casting between types, \"not-a-number\"
    > calculations, and how your language handles numbers that are too
    > large or too small for its underlying representation

-   Do not pass user supplied data to any dynamic execution function

-   Restrict users from generating new code or altering existing code

-   Review all secondary applications, third party code and libraries to
    > determine business necessity and validate safe functionality, as
    > these can introduce new vulnerabilities

-   Implement safe updating. If the application will utilize automatic
    > updates, then use cryptographic signatures for your code and
    > ensure your download clients verify those signatures. Use
    > encrypted channels to transfer the code from the host server
