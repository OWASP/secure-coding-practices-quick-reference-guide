# Korean language (ko-KR) version

We appreciate all kinds of [suggestions and corrections][issues] on this translation
of the Secure Coding Practices Quick Reference Guide

Create the PDF document from directory `ko/kr`:

```
pandoc -o OWASP_SCP_Quick_Reference_Guide.ko-KR.pdf title.pdf.txt \
--pdf-engine=xelatex -r markdown 00-front-toc/01-front.markdown \
00-front-toc/02-toc.markdown \
01-introduction/01-chapter1.markdown \
02-overview/01-chapter2.markdown \
03-checklist/01-chapter3.markdown \
04-appendices/01-references.markdown \
04-appendices/02-glossary.markdown
```

Similarly create the EBook:

```
pandoc -o OWASP_SCP_Quick_Reference_Guide.ko-KR.epub title.txt \
--pdf-engine=xelatex -r markdown 00-front-toc/01-front.markdown \
00-front-toc/02-toc.markdown \
01-introduction/01-chapter1.markdown \
02-overview/01-chapter2.markdown \
03-checklist/01-chapter3.markdown \
04-appendices/01-references.markdown \
04-appendices/02-glossary.markdown
```

There is a dependency on having a *tex installed that will provide pdflatex for the PDF output.
For example with MacOS the command `brew install basictex` can be used.
Also make sure font 'Nanum Myeongjo' is installed when creating the PDF and eBook.

[issues]: https://github.com/OWASP/www-project-secure-coding-practices-quick-reference-guide/issues/new
