\newpage
# Introdução

Este documento não se baseia apenas em questões tecnológicas e tem o
propósito de definir um conjunto de boas práticas de segurança no
desenvolvimento de aplicações. As recomendações serão apresentadas no
formato de lista de verificações, que podem ser integradas ao ciclo de
desenvolvimento das aplicações. A adoção destas práticas provavelmente
reduzirá as vulnerabilidades mais comuns em aplicações Web.

Geralmente, é mais barato construir software seguro do que corrigir
problemas de segurança após a entrega do mesmo como um produto final ou
pacote completo, sem falar nos custos que podem estar associados a uma
falha de segurança.

Proteger os recursos críticos das aplicações tem se tornado cada vez
mais importante, pois o foco dos atacantes mudou para a camada de
aplicação. Um estudo da SANS em 2009[^1] descobriu que os ataques
contra aplicações Web constituem mais de 60% das tentativas de ataque
observados na Internet.

Ao utilizar este guia é recomendável que equipes de desenvolvimento
avaliem a maturidade do ciclo de vida de desenvolvimento de software e o
nível de conhecimento da equipe. Como este guia não entra em detalhes de
como implantar cada prática de programação, os programadores precisam
possuir conhecimento prévio ou devem ter disponíveis os recursos que
forneçam o conhecimento necessário. Este guia apresenta práticas que
podem ser traduzidas em requisitos de desenvolvimento sem a necessidade
do programador possuir uma compreensão aprofundada das vulnerabilidades
e *exploits* de segurança. No entanto, outros membros da equipe de
desenvolvimento devem possuir responsabilidades, competências adequadas,
ferramentas e recursos para validar se o projeto e a implementação
atendem os requisitos de segurança.

No apêndice B encontra-se um glossário dos termos importantes usados
neste documento, incluindo o título das secções e palavras mostradas em
*itálico*.

Não faz parte do escopo deste guia fornecer orientações para implantar
um *framework* de desenvolvimento seguro de software, mas as seguintes
práticas gerais e referências são recomendadas:

-   Definir claramente os papéis e responsabilidades

-   Fornecer às equipes de desenvolvimento pessoal com formação adequada
    em segurança no desenvolvimento de aplicações

-   Implementar um ciclo de desenvolvimento de software seguro

-   Estabelecer padrões de programação segura

    -   [[OWASP Development Guide](http://www.owasp.org/index.php/Category:OWASP_Guide_Project) Project

-   Construir uma biblioteca reutilizável ou fazer uso de uma biblioteca
    de segurança[^1]

    -   [OWASP Enterprise Security API][esapi] (ESAPI) Project

-   Verificar a efetividade dos controles de segurança

    -   [OWASP Application Security Verification Standard][asvs] (ASVS) Project

-   Estabelecer práticas para garantir a segurança quando há
    terceirização no desenvolvimento, incluindo a definição dos
    requisitos de segurança e metodologias de verificação tanto para
    os requisitos das propostas, como para o contrato a ser firmado
    entre as partes

[asvs]: https://owasp.org/www-project-application-security-verification-standard/
[esapi]: https://owasp.org/www-project-enterprise-security-api/

[^1] NT: Complemento adicionado pelo tradutor

