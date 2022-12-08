**OWASP Secure Coding Practices**

**Quick Reference Guide**

**Copyright and License**

Copyright © 2010 The OWASP Foundation.

This document is released under the Creative Commons Attribution
ShareAlike 3.0 license. For any reuse or distribution, you must make
clear to others the license terms of this work.

<http://creativecommons.org/licenses/by-sa/3.0/>

# Table of Contents {#table-of-contents .TOC-Heading}

[Introduction 3](#introduction)

[Software Security and Risk Principles Overview
4](#software-security-and-risk-principles-overview)

[Secure Coding Practices Checklist
5](#secure-coding-practices-checklist)

[Input Validation: 5](#input-validation)

[Output Encoding: 5](#output-encoding)

[Authentication and Password Management:
6](#authentication-and-password-management)

[Session Management: 7](#session-management)

[Access Control: 8](#access-control)

[Cryptographic Practices: 9](#cryptographic-practices)

[Error Handling and Logging: 9](#error-handling-and-logging)

[Data Protection: 10](#data-protection)

[Communication Security: 10](#communication-security)

[System Configuration: 11](#system-configuration)

[Database Security: 11](#database-security)

[File Management: 12](#file-management)

[Memory Management: 12](#memory-management)

[General Coding Practices: 13](#general-coding-practices)

[Appendix A: 14](#appendix-a)

[External References: 14](#external-references)

[Appendix B: Glossary 15](#appendix-b-glossary)

# Introduction {#introduction .list-paragraph}

This technology agnostic document defines a set of general software
security coding practices, in a checklist format, that can be integrated
into the software development lifecycle. Implementation of these
practices will mitigate most common software vulnerabilities.

Generally, it is much less expensive to build secure software than to
correct security issues after the software package has been completed,
not to mention the costs that may be associated with a security breach.

Securing critical software resources is more important than ever as the
focus of attackers has steadily moved toward the application layer. A
2009 SANS study^1^ found that attacks against web applications
constitute more than 60% of the total attack attempts observed on the
Internet.

When utilizing this guide, development teams should start by assessing
the maturity of their secure software development lifecycle and the
knowledge level of their development staff. Since this guide does not
cover the details of how to implement each coding practice, developers
will either need to have the prior knowledge or have sufficient
resources available that provide the necessary guidance. This guide
provides coding practices that can be translated into coding
requirements without the need for the developer to have an in depth
understanding of security vulnerabilities and exploits. However, other
members of the development team should have the responsibility, adequate
training, tools and resources to validate that the design and
implementation of the entire system is secure.

A glossary of important terms in this document, including section
headings and words shown in *italics*, is provided in appendix B.

Guidance on implementing a secure software development framework is
beyond the scope of this paper, however the following additional general
practices and resources are recommended:

-   Clearly define roles and responsibilities

-   Provide development teams with adequate software security training

-   Implement a secure software development lifecycle

    -   [OWASP CLASP
        Project](http://www.owasp.org/index.php/Category:OWASP_CLASP_Project)

-   Establish secure coding standards

    -   [OWASP Development Guide
        Project](http://www.owasp.org/index.php/Category:OWASP_Guide_Project)

-   Build a re-usable object library

    -   [OWASP Enterprise Security API (ESAPI)
        Project](http://www.owasp.org/index.php/Category:OWASP_Enterprise_Security_API)

-   Verify the effectiveness of security controls

    -   [OWASP Application Security Verification Standard (ASVS)
        Project)](http://www.owasp.org/index.php/Category:OWASP_Application_Security_Verification_Standard_Project)

-   Establish secure outsourced development practices including defining
    > security requirements and verification methodologies in both the
    > request for proposal (RFP) and contract.

    -   [OWASP Legal
        Project](http://www.owasp.org/index.php/Category:OWASP_Legal_Project)
