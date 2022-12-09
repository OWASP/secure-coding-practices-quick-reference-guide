English lanugauge (US) version of the Secure Coding Practices Quick Reference Guide

Create the PDF output from directory `en`:

```
en$ pandoc -o OWASP_SCP_Quick_Reference_Guide.pdf title.pdf.txt \
00-front-toc/01-front.markdown 00-front-toc/02-toc.markdown \
01-introduction/01-chapter1.markdown \
02-overview/01-chapter2.markdown \
03-checklist/01-chapter3.markdown \
04-appendices/01-references.markdown \
04-appendices/02-glossary.markdown
```

Create the EBook output from directory `en`:

```
en$ pandoc -o OWASP_SCP_Quick_Reference_Guide.epub title.txt \    
00-front-toc/01-front.markdown 00-front-toc/02-toc.markdown \
01-introduction/01-chapter1.markdown \
02-overview/01-chapter2.markdown \
03-checklist/01-chapter3.markdown \
04-appendices/01-references.markdown \
04-appendices/02-glossary.markdown
```
