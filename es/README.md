# Traducción al español (Uruguay)

Agradezcamos todo tipo de [sugerencias y correcciones][issues] sobre este traducción
del Secure Coding Practices Quick Reference Guide

Para PDF desde el directorio `es`:

```
pandoc -o OWASP_SCP_Quick_Reference_Guide.es.pdf title.pdf.txt \
00-front-toc/01-front.markdown 00-front-toc/02-toc.markdown \
01-introduction/01-chapter1.markdown \
02-overview/01-chapter2.markdown \
03-checklist/01-chapter3.markdown \
04-appendices/01-references.markdown \
04-appendices/02-glossary.markdown
```

Y para EBook:

```
pandoc -o OWASP_SCP_Quick_Reference_Guide.es.epub title.txt \    
00-front-toc/01-front.markdown 00-front-toc/02-toc.markdown \
01-introduction/01-chapter1.markdown \
02-overview/01-chapter2.markdown \
03-checklist/01-chapter3.markdown \
04-appendices/01-references.markdown \
04-appendices/02-glossary.markdown
```

[issues]: https://github.com/OWASP/www-project-secure-coding-practices-quick-reference-guide/issues/new
