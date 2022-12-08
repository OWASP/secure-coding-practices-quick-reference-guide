## Input Validation: {#input-validation .list-paragraph}

-   Conduct all data validation on a trusted system (e.g., The server)

-   Identify all data sources and classify them into trusted and
    > untrusted. Validate all data from untrusted sources (e.g.,
    > Databases, file streams, etc.)

-   There should be a centralized input validation routine for the
    > application

-   Specify proper character sets, such as UTF-8, for all sources of
    > input

-   Encode data to a common character set before validating
    > ([*Canonicalize*](#Canonicalize))

-   All validation failures should result in input rejection

-   Determine if the system supports UTF-8 extended character sets and
    > if so, validate after UTF-8 decoding is completed

-   Validate all client provided data before processing, including all
    > parameters, URLs and HTTP header content (e.g. Cookie names and
    > values). Be sure to include automated post backs from JavaScript,
    > Flash or other embedded code

-   Verify that header values in both requests and responses contain
    > only ASCII characters

-   Validate data from redirects (An attacker may submit malicious
    > content directly to the target of the redirect, thus circumventing
    > application logic and any validation performed before the
    > redirect)

-   Validate for expected data types

-   Validate data range

-   Validate data length

-   Validate all input against a \"white\" list of allowed characters,
    > whenever possible

-   If any potentially [*hazardous characters*](#Hazardous_Character)
    > must be allowed as input, be sure that you implement additional
    > controls like output encoding, secure task specific APIs and
    > accounting for the utilization of that data throughout the
    > application . Examples of common hazardous characters include:

> \< \> \" \' % ( ) & + \\ \\\' \\\"

-   If your standard validation routine cannot address the following
    > inputs, then they should be checked discretely

    -   Check for null bytes (%00)

    -   Check for new line characters (%0d, %0a, \\r, \\n)

    -   Check for "dot-dot-slash\" (../ or ..\\) path alterations
        > characters. In cases where UTF-8 extended character set
        > encoding is supported, address alternate representation like:
        > %c0%ae%c0%ae/

> (Utilize [*canonicalization*](#Canonicalize) to address double
> encoding or other forms of obfuscation attacks)
