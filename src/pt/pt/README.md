# Portuguese language (pt-PT) version

We appreciate all kinds of [suggestions and corrections][issues] on this translation
of the Secure Coding Practices Quick Reference Guide

Create the PDF document from directory `pt/pt`:

```
pandoc -o OWASP_SCP_Quick_Reference_Guide.pt-PT.pdf \
-r markdown+footnotes title.pdf.yaml \
01-introduction/01-front.markdown \
01-introduction/02-toc.markdown \
01-introduction/03-credits.markdown \
01-introduction/05-introduction.markdown \
02-checklist/05-checklist.markdown \
03-appendices/03-overview.markdown \
03-appendices/05-glossary.markdown \
03-appendices/07-references.markdown \
03-appendices/08-footnotes.markdown
```

Similarly create the EBook:

```
pandoc -o OWASP_SCP_Quick_Reference_Guide.pt-PT.epub \
-r markdown+footnotes title.yaml \
01-introduction/01-front.markdown \
01-introduction/02-toc.markdown \
01-introduction/03-credits.markdown \
01-introduction/05-introduction.markdown \
02-checklist/05-checklist.markdown \
03-appendices/03-overview.markdown \
03-appendices/05-glossary.markdown \
03-appendices/07-references.markdown \
03-appendices/08-footnotes.markdown
```

There is a dependency on having a *tex installed that will provide pdflatex for the PDF output.
For example with MacOS the command `brew install basictex` can be used.

[issues]: https://github.com/OWASP/www-project-secure-coding-practices-quick-reference-guide/issues/new
