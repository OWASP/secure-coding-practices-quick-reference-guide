## Memory Management: {#memory-management .list-paragraph}

-   Utilize input and output control for un-trusted data

-   Double check that the buffer is as large as specified

-   When using functions that accept a number of bytes to copy, such as
    > strncpy(), be aware that if the destination buffer size is equal
    > to the source buffer size, it may not NULL-terminate the string

-   Check buffer boundaries if calling the function in a loop and make
    > sure there is no danger of writing past the allocated space

-   Truncate all input strings to a reasonable length before passing
    > them to the copy and concatenation functions

-   Specifically close resources, don't rely on garbage collection.
    > (e.g., connection objects, file handles, etc.)

-   Use non-executable stacks when available

-   Avoid the use of known vulnerable functions (e.g., printf, strcat,
    > strcpy etc.)

-   Properly free allocated memory upon the completion of functions and
    > at all exit points
