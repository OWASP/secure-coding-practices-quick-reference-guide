# Portuguese (Brazil) language (pt-BR) version

We appreciate all kinds of [suggestions and corrections][issues] on this translation
of the Secure Coding Practices Quick Reference Guide

Create the PDF document from directory `pt/br`:

```
pandoc -o OWASP_SCP_Quick_Reference_Guide.pt-BR.pdf \
-r markdown+footnotes title.pdf.txt \
00-front-toc/01-front.markdown \
00-front-toc/02-toc.markdown \
00-front-toc/03-credits.markdown \
01-introduction/01-chapter1.markdown \
03-checklist/01-chapter3.markdown \
02-overview/01-chapter2.markdown \
04-appendices/01-references.markdown \
04-appendices/02-glossary.markdown \
04-appendices/03-footnotes.markdown
```

Similarly create the EBook:

```
pandoc -o OWASP_SCP_Quick_Reference_Guide.pt-BR.epub \
-r markdown+footnotes title.txt \
00-front-toc/01-front.markdown \
00-front-toc/02-toc.markdown \
00-front-toc/03-credits.markdown \
01-introduction/01-chapter1.markdown \
03-checklist/01-chapter3.markdown \
02-overview/01-chapter2.markdown \
04-appendices/01-references.markdown \
04-appendices/02-glossary.markdown \
04-appendices/03-footnotes.markdown
```

There is a dependency on having a *tex installed that will provide pdflatex for the PDF output.
For example with MacOS the command `brew install basictex` can be used.

[issues]: https://github.com/OWASP/www-project-secure-coding-practices-quick-reference-guide/issues/new
