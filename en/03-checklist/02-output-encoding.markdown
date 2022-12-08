## Output Encoding: {#output-encoding .list-paragraph}

-   Conduct all encoding on a trusted system (e.g., The server)

-   Utilize a standard, tested routine for each type of outbound
    > encoding

-   [*Contextually output encode*](#Contextual_Output_Encoding) all data
    > returned to the client that originated outside the application\'s
    > [*trust boundary*](#Trust_Boundaries). [*HTML entity
    > encoding*](#HTML_Entity_Encode) is one example, but does not work
    > in all cases

-   Encode all characters unless they are known to be safe for the
    > intended interpreter

-   Contextually [*sanitize*](#Sanitize_Data) all output of un-trusted
    > data to queries for SQL, XML, and LDAP

-   [*Sanitize*](#Sanitize_Data) all output of un-trusted data to
    > operating system commands
