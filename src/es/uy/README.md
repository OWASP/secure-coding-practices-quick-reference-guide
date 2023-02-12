# Traducción al español (es-UR)

Agradecemos todo tipo de [sugerencias y correcciones][issues] sobre esta traducción
de la Guía Rápida de Prácticas de Codificación Segura 

Para generar el PDF, posicionado en el directorio `es/uy`:

```
pandoc -o OWASP_SCP_Quick_Reference_Guide.es-UY.pdf title.pdf.txt \
00-front-toc/01-front.markdown \
00-front-toc/02-toc.markdown \
00-front-toc/03-credits.markdown \
01-introduction/01-chapter1.markdown \
02-overview/01-chapter2.markdown \
03-checklist/01-chapter3.markdown \
04-appendices/01-references.markdown \
04-appendices/02-glossary.markdown
```

De forma similar, para generar el EBook:

```
pandoc -o OWASP_SCP_Quick_Reference_Guide.es-UY.epub title.txt \
00-front-toc/01-front.markdown \
00-front-toc/02-toc.markdown \
00-front-toc/03-credits.markdown \
01-introduction/01-chapter1.markdown \
02-overview/01-chapter2.markdown \
03-checklist/01-chapter3.markdown \
04-appendices/01-references.markdown \
04-appendices/02-glossary.markdown
```

Es necesario poseer instalada una dependencia *tex para la correcta generación del formato PDF.
Por ejemplo, en MacOS puede ser utilizado el comando `brew install basictex`.

[issues]: https://github.com/OWASP/www-project-secure-coding-practices-quick-reference-guide/issues/new
