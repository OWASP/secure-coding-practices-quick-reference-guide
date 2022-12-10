\newpage
# Appendix B: Glossary {#appendix-b-glossary .list-paragraph}

[]{#Abuse_Case .anchor}**Abuse Case:** Describes the intentional and
unintentional misuses of the software. Abuse cases should challenge the
assumptions of the system design.

**Access Control:** A set of controls that grant or deny a user, or
other entity, access to a system resource. This is usually based on
hierarchical roles and individual privileges within a role, but also
includes system to system interactions.

**Authentication:** A set of controls that are used to verify the
identity of a user, or other entity, interacting with the software.

[]{#Availability .anchor}**Availability:** A measure of a system\'s
accessibility and usability.

[]{#Canonicalize .anchor}**Canonicalize:** To reduce various encodings
and representations of data to a single simple form.

**Communication Security:** A set of controls that help ensure the
software handles the sending and receiving of information in a secure
manner.

[]{#Confidentiality .anchor}**Confidentiality:** To ensure that
information is disclosed only to authorized parties.

[]{#Contextual_Output_Encoding .anchor}**Contextual Output Encoding:**
Encoding output data based on how it will be utilized by the
application. The specific methods vary depending on the way the output
data is used. If the data is to be included in the response to the
client, account for inclusion scenarios like: the body of an HTML
document, an HTML attribute, within JavaScript, within a CSS or in a
URL. You must also account for other use cases like SQL queries, XML and
LDAP.

[]{#Cross_Site_Request_Forgery .anchor}**Cross Site Request Forgery:**
An external website or application forces a client to make an unintended
request to another application that the client has an active session
with. Applications are vulnerable when they use known, or predictable,
URLs and parameters; and when the browser automatically transmits all
required session information with each request to the vulnerable
application.

This is one of the only attacks specifically discussed in
this document and is only included because the associated vulnerability
is very common and poorly understood.

**Cryptographic Practices:** A set of controls that ensure cryptographic
operations within the application are handled securely.

**Data Protection:** A set of controls that help ensure the software
handles the storing of information in a secure manner.

**Database Security:** A set of controls that ensure that software
interacts with a database in a secure manner and that the database is
configured securely.

**Error Handling and Logging:** A set of practices that ensure the
application handles errors safely and conducts proper event logging.

[]{#Exploit .anchor}**Exploit:** To take advantage of a vulnerability.
Typically this is an intentional action designed to compromise the
software\'s security controls by leveraging a vulnerability.

**File Management:** A set of controls that cover the interaction
between the code and other system files.

**General Coding Practices:** A set of controls that cover coding
practices that do not fit easily into other categories.

[]{#Hazardous_Character .anchor}**Hazardous Character:** Any character
or encoded representation of a character that can effect the intended
operation of the application or associated system by being interpreted
to have a special meaning, outside the intended use of the character.
These characters may be used to:

> • Altering the structure of existing code or statements
>
> • Inserting new unintended code
>
> • Altering paths
>
> • Causing unexpected outcomes from program functions or routines
>
> • Causing error conditions
>
> • Having any of the above effects on down stream applications or
> systems

[]{#HTML_Entity_Encode .anchor}**HTML Entity Encode:** The process of
replacing certain ASCII characters with their HTML entity equivalents.
For example, encoding would replace the less than character \"\<\" with
the HTML equivalent \"&lt;\". HTML entities are \'inert\' in most
interpreters, especially browsers, which can mitigate certain client
side attacks.

[]{#Impact .anchor}**Impact:** A measure of the negative effect to the
business that results from the occurrence of an undesired event; what
would be the result of a vulnerability being exploited.

**Input Validation:** A set of controls that verify the properties of
all input data matches what is expected by the application including
types, lengths, ranges, acceptable character sets and does not include
known hazardous characters.

[]{#Integrity .anchor}**Integrity:** The assurance that information is
accurate, complete and valid, and has not been altered by an
unauthorized action.

[]{#Log_Event_Data .anchor}**Log Event Data:** This should include the
following:

> 1\. Time stamp from a trusted system component
>
> 2\. Severity rating for each event
>
> 3\. Tagging of security relevant events, if they are mixed with other
> log entries
>
> 4\. Identity of the account/user that caused the event
>
> 5\. Source IP address associated with the request
>
> 6\. Event outcome (success or failure)
>
> 7\. Description of the event

**Memory Management:** A set of controls that address memory and buffer
usage.

[]{#Mitigate .anchor}**Mitigate:** Steps taken to reduce the severity of
a vulnerability. These can include removing a vulnerability, making a
vulnerability more difficult to exploit, or reducing the negative impact
of a successful exploitation.

[]{#Multi_Factor_Authentication .anchor}**Multi-Factor Authentication:**
An authentication process that requires the user to produce multiple
distinct types of credentials. Typically this is based on something:

-   they have, eg a smartcard
-   something they know, eg a PIN
-   something they are, eg data from a biometric reader

**Output Encoding:** A set of controls addressing the use of encoding to
ensure data output by the application is safe.

[]{#Parameterized_Queries .anchor}**Parameterized Queries / Prepared
Statements:** Keeps the query and data separate through the use of
placeholders. The query structure is defined with place holders, the SQL
statement is sent to the database and prepared, and then the prepared
statement is combined with the parameter values. The prevents the query
from being altered, because the parameter values are combined with the
compiled statement, not a SQL string.

[]{#Sanitize_Data .anchor}**Sanitize Data:** The process of making
potentially harmful data safe through the use of data removal,
replacement, encoding or escaping of the characters.

[]{#Security_Controls .anchor}**Security Controls:** An action that
mitigates a potential vulnerability and helps ensure that the software
behaves only in the expected manner.

[]{#Security_Requirements .anchor}**Security Requirements:** A set of
design and functional requirements that help ensure the software is
built and deployed in a secure manner.

[]{#Sequential_Authentication .anchor}**Sequential Authentication:**
When authentication data is requested on successive pages rather than
being requested all at once on a single page.

**Session Management:** A set of controls that help ensure web
applications handle HTTP sessions in a secure manner.

[]{#State_Data .anchor}**State Data:** When data or parameters are used,
by the application or server, to emulate a persistent connection or
track a client\'s status across a multi-request process or transaction.

[]{#System .anchor}**System:** A generic term covering the operating
systems, web server, application frameworks and related infrastructure.

**System Configuration:** A set of controls that help ensure the
infrastructure components supporting the software are deployed securely.

[]{#Threat_Agent .anchor}**Threat Agent:** Any entity which may have a
negative impact on the system. This may be a malicious user who wants to
compromise the system\'s security controls; however, it could also be an
accidental misuse of the system or a more physical threat like fire or
flood.

[]{#Trust_Boundaries .anchor}**Trust Boundaries:** Typically a trust
boundary constitutes the components of the system under your direct
control. All connections and data from systems outside of your direct
control, including all clients and systems managed by other parties,
should be consider untrusted and be validated at the boundary, before
allowing further system interaction.

[]{#Vulnerability .anchor}**Vulnerability:** A weakness that makes the
system susceptible to attack or damage.
