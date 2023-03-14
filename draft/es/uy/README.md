# Traducción al español (es-UR)

Agradecemos todo tipo de [sugerencias y correcciones][issues] sobre esta traducción
de la Guía Rápida de Prácticas de Codificación Segura 

Para generar el PDF, posicionado en el directorio `es/uy`:

```
pandoc --output=OWASP_SCP_Quick_Reference_Guide.es-UY.pdf title.pdf.yaml \
01-introduction/01-front.markdown \
01-introduction/02-toc.markdown \
01-introduction/03-credits.markdown \
01-introduction/04-copyright.markdown \
01-introduction/05-introduction.markdown \
02-checklist/05-checklist.markdown \
03-appendices/03-overview.markdown \
03-appendices/05-glossary.markdown \
03-appendices/07-references.markdown
```

De forma similar, para generar el EBook:

```
pandoc --output=OWASP_SCP_Quick_Reference_Guide.es-UY.epub title.yaml \
01-introduction/01-front.markdown \
01-introduction/02-toc.markdown \
01-introduction/03-credits.markdown \
01-introduction/04-copyright.markdown \
01-introduction/05-introduction.markdown \
02-checklist/05-checklist.markdown \
03-appendices/03-overview.markdown \
03-appendices/05-glossary.markdown \
03-appendices/07-references.markdown
```

Es necesario poseer instalada una dependencia *tex para la correcta generación del formato PDF.
Por ejemplo, en MacOS puede ser utilizado el comando `brew install basictex`.

[issues]: https://github.com/OWASP/www-project-secure-coding-practices-quick-reference-guide/issues/new
