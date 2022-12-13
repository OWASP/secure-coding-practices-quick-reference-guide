\newpage
# Introducción

El presente documento define un conjunto de prácticas comunes de
codificación de software, tecnológicamente agnósticas, en formato de
lista de verificación con el fin de ser integrado al ciclo de
desarrollo. La implementación de estas prácticas mitiga las
vulnerabilidades más comunes del software.

En términos generales, es mucho menos costoso construir software seguro
que corregir problemas de seguridad cuando ha sido completado, sin
mencionar los costos que pueden estar asociados a un quiebre en la
seguridad.

Asegurar recursos críticos de software se ha vuelto más importante que
nunca debido a que el foco de los atacantes se ha desplazado hacia la
capa de aplicación. Un estudio en 2009 de la SANS determinó que los
ataques contra aplicaciones web constituyen más del 60% del total de
intentos de ataque observados en la Internet.

Utilizando la presente guía, el equipo de desarrollo debería comenzar
evaluando el grado de madurez de su ciclo de desarrollo de software
desde el punto de vista de la seguridad, así como el nivel de
conocimiento de sus miembros. Dado que esta guía no cubre los detalles
de implementación de las prácticas de codificación, los desarrolladores
deben poseer previamente los conocimientos suficientes o bien tener
disponibles recursos que los guíen. Esta guía provee prácticas de
codificación que pueden ser traducidas en requisitos de codificación sin
la necesidad que el desarrollador posea un entendimiento profundo de
vulnerabilidades de seguridad y exploits. Sin embargo, otros miembros
del equipo de desarrollo deberían de poseer el entrenamiento adecuado,
recursos y herramientas para ser responsables y validar que el diseño e
implementación del sistema es seguro.

En el apéndice B se presenta un glosario de los términos más importantes
utilizados en este documento, incluyendo los cabezales de sección y las
palabras resaltadas con itálicas.

Se encuentra fuera del alcance de este documento la información
detallada de cómo implementar un proceso de desarrollo de software
seguro, sin embargo, se recomiendan las siguientes prácticas y recursos:

-   Definir claramente roles y responsabilidades.

-   Proveer al equipo de desarrollo capacitación suficiente en el área
    de seguridad del software.

-   Implementar un ciclo de desarrollo de software seguro.

-   Establecer estándares de codificación segura.

    -   [OWASP Development Guide][guide] Project

-   Construir una biblioteca de objetos reutilizable.

    -   [OWASP Enterprise Security API][esapi] (ESAPI) Project

-   Verificar la efectividad de los controles de seguridad.

    -   [OWASP Application Security Verification Standard][asvs] (ASVS) Project

-   Establecer prácticas de seguridad por fuera del ciclo de desarrollo,
    incluyendo requerimientos de seguridad y metodologías de
    verificación tanto en los request for proposal (RFP) como en los
    contratos.

[asvs]: https://owasp.org/www-project-application-security-verification-standard/
[esapi]: https://owasp.org/www-project-enterprise-security-api/
[guide]: http://www.owasp.org/index.php/Category:OWASP_Guide_Project
