\newpage
# Apêndice A Princípios Gerais de Segurança em Aplicações e Riscos {#princípios-gerais-de-segurança-em-aplicações-e-riscos .list-paragraph}

Construir software seguro exige o conhecimento básico dos princípios de
segurança. Uma revisão abrangente dos princípios de segurança está fora
do escopo desse guia, porém os conceitos de segurança serão abordados de
forma superficial, mas abrangente.

O objetivo da segurança em aplicações é manter a *confidencialidade*,
*integridade* e *disponibilidade* dos recursos de informação a fim de
permitir que as operações de negócios sejam bem sucedidas e esse
objetivo é alcançado através da implementação de *controles de
segurança*. Este guia concentra-se nos controles técnicos, específicos
para *mitigar* as ocorrências das *vulnerabilidades* mais comuns no
software e como o foco principal são as aplicações Web e a
infraestrutura de apoio, boa parte desse documento pode ser usada para
qualquer plataforma de desenvolvimento de software.

Para proteger o negócio contra os riscos inaceitáveis, isto é,
relacionados com a dependência e com a confiança depositada na
aplicação, este guia ajuda a compreender o que podemos entender por
risco. Deste modo, risco é a combinação de fatores que ameaçam o sucesso
do negócio. Isto pode ser descrito conceitualmente da seguinte forma: um
*agente de ameaça* interage com um *sistema*, no qual pode haver uma
*vulnerabilidade* latente que quando *explorada* causa um *impacto*.
Como isto pode parecer um conceito abstrato, pense do seguinte modo: um
ladrão de carros (agente de ameaça) passa por um estacionamento
verificando nos carros presentes (o sistema) a existência de portas
destrancadas (a vulnerabilidade) e quando a encontra, abre a porta (a
exploração) e leva para si o que está dentro do carro (o impacto). Todos
esses fatores desempenham um papel no desenvolvimento de software
seguro.

Existe uma diferença fundamental entre a abordagem adotada por uma
equipe de desenvolvimento e a abordagem que é adotada por alguém que
está interessado em atacar uma aplicação. Uma equipe de desenvolvimento
normalmente desenvolve uma aplicação com base naquilo que ela pretende
fazer e isso significa criar uma aplicação para executar tarefas
específicas, baseadas em requisitos funcionais e casos de uso
documentados. Um atacante, por outro lado, está mais interessado no que
a aplicação pode ser levada a fazer e parte do princípio que \"qualquer
ação não expressamente proibida, é permitida\". Para resolver isso,
alguns elementos adicionais precisam ser integrados nas fases iniciais
do ciclo de vida do software e esses novos elementos são *requisitos de
segurança* e *casos de abuso.* Este guia foi construído para ajudar a
identificar os requisitos de segurança de alto nível e abordar vários
cenários de ataques.

É importante que as equipes de desenvolvimento de aplicações Web
entendam que os mecanismos de controle do lado cliente, como validação
de dados de entrada no cliente, campos ocultos e controles de interface
(combo box, radio buttons), fornecem pouco ou nenhum benefício de
segurança. Nesse caso, um atacante pode usar ferramentas como *proxies*
do lado cliente, como o OWASP WebScarab, Burp ou ferramentas de captura
de pacotes de rede, como o Wireshark, para analisar o tráfego da
aplicação e enviar requisições manipuladas, burlando todas as
interfaces. Além disso, o Flash, os Applets Java e demais objetos que
trabalham no lado cliente podem ser alvo de engenharia reversa e
analisados em busca de falhas.

As falhas de segurança de software podem ser introduzidas em qualquer
fase do ciclo de desenvolvimento, inclusive:

-   No início, ao não identificar as necessidades de segurança

-   Na criação de arquiteturas conceituais que possuam erros de lógica

-   No uso de más práticas de programação que introduzam
    vulnerabilidades técnicas

-   Na implementação do software de modo inapropriado

-   Na inserção de falhas durante a manutenção ou a atualização

Além disso, é importante entender que as vulnerabilidades de software
podem ter um escopo muito maior do que o do próprio software. Dependendo
da natureza do software, da vulnerabilidade e da infraestrutura de
apoio, o impacto de uma exploração bem sucedida pode comprometer
qualquer um, ou mesmo todos os seguintes aspectos:

-   O software e sua informação associada

-   O sistema operacional dos servidores associados

-   A base de dados do *backend*

-   Outras aplicações em um ambiente compartilhado

-   O sistema do usuário

-   Outros softwares com os quais o usuário interage
