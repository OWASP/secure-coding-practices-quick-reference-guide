\newpage
# Apêndice B Glossário {#glossário .list-paragraph}

**Agente de Ameaça:** Qualquer entidade que pode causar um impacto
negativo num sistema. Pode ser tanto um utilizador mal-intencionado
querendo comprometer os controlos de segurança do sistema, quanto um
desvio acidental do sistema ou uma ameaça física como incêndios ou
inundações.

**Autenticação:** É um conjunto de controlos usados para verificar a
identidade de um utilizador, ou outra entidade que interage com o
software.

**Autenticação de Múltiplos Fatores:** É um processo de autenticação que
requer vários tipos de credenciais do utilizador. Normalmente é baseado
em algo que ele possui (ex.: cartão inteligente), algo que ele sabe (uma
ex.: senha), ou em algo que ele é (ex.: dados provenientes de um leitor
biométrico).

**Autenticação Sequencial:** Ocorre quando os dados de autenticação são
solicitados em sucessivas páginas, ao invés de serem solicitados numa
única página.

**Canonicalização:** É uma operação realizada para reduzir várias
codificações e representações de dados numa única forma simplificada.

**Caracteres Maliciosos:** Quaisquer caracteres ou representações
codificadas de caracteres que podem produzir efeitos indesejáveis sobre
a operação normal de aplicações ou dos sistemas associados quando são
interpretados, por terem significado especial. Estes caracteres podem
ser usados para:

-   Modificar a estrutura de código ou de declarações

-   Inserir código indesejado

-   Modificar caminhos

-   Causar saídas inesperadas das funções ou rotinas dos programas

-   Causar condições de erro

-   Causar qualquer dos efeitos anteriores em aplicações subjacentes

**Casos de Abuso:** Descrevem o mau uso, intencional ou não, do
software. Os casos de abuso devem desafiar os pressupostos do projeto do
sistema.

**Codificação de Entidade HTML:** Processo de substituição de
determinados caracteres ASCII pelas entidades HTML equivalentes. Por
exemplo, a codificação poderia substituir o caractere "\<" pela entidade
HTML equivalente \"&lt;\". Essas entidades são "inertes" na maioria dos
interpretadores --especialmente navegadores-- e podem atenuar os ataques
do lado do cliente.

**Codificação de Saída Baseada em Contexto:** É a codificação de dados
da saída realizada usando como referência o modo como os dados serão
utilizados pela aplicação. Se os dados da saída estiverem incluídos na
resposta ao cliente, deve-se levar em consideração situações como: o
corpo de um documento HTML, um atributo de HTML, codificação JavaScript,
codificação dentro de um CSS ou de uma URL. Devem também ser levados em
consideração outros casos como consultas SQL, XML e LDAP.

**Codificação de Saída de Dados:** É um conjunto de controlos que
abordam o uso de codificação para

garantir uma saída de dados segura gerada pela aplicação.

**Confidencialidade:** É o ato de garantir que as informações são
divulgadas apenas para as partes autorizadas.

**Configuração do Sistema:** Conjunto de controlos que ajudam a garantir
que os componentes de infraestrutura de apoio ao software são
disponibilizados de forma segura.

**Consultas Parametrizadas (prepared statements):** Mantém a consulta e
os dados separados através do uso de espaços reservados. A estrutura de
consulta é definida por caracteres especiais que representam os
parâmetros a serem substituídos. A consulta parametrizada é enviada para
a base de dados e preparada para receber os parâmetros e, em seguida, é
combinada com os valores dos mesmos. Isto impede que a consulta seja
alterada porque os valores dos parâmetros são combinados com a
declaração compilada e não concatenados diretamente na sequência de
caracteres que compõem a consulta SQL.

**Controle de Acesso**: É um conjunto de controlos que liberta ou nega o
acesso a um recurso do sistema a um utilizador ou outra entidade
qualquer. Normalmente é baseado em regras hierárquicas e privilégios
individuais associados a papéis, porém também inclui interações entre
sistemas.

**Controles de Segurança:** São ações que mitigam uma vulnerabilidade
potencial e ajudam a garantir que o software se comporta conforme o
esperado.

**Cross Site Request Forgery (CSRF):** Ocorre quando uma aplicação ou
site web externos forçam o navegador do cliente a realizar um pedido
involuntário para uma aplicação em que o cliente possui uma sessão
ativa. As aplicações são vulneráveis ao CSRF quando usam URLs e
parâmetros conhecidos ou previsíveis ou quando o navegador transmite
todas as informações da sessão para a aplicação vulnerável de forma
automática em cada solicitação. Este é apenas um dos ataques discutidos
neste documento e só está incluído porque a vulnerabilidade associada é
muito comum, porém mal compreendida.

**Disponibilidade:** É a propriedade de estar acessível e utilizável
quando solicitado por uma entidade autorizada.

**Estado dos Dados:** São dados ou parâmetros usados pela aplicação ou
pelo servidor para emular uma ligação persistente ou controlar o estado
(status) de um cliente através de um processo de múltiplas pedidos ou
transações.

**Exploit:** É a ação de aproveitar-se da existência de uma
vulnerabilidade. Normalmente é uma ação intencional e tem como objetivo
comprometer os controles de segurança do software.

**Gestão de Ficheiros:** É um conjunto de controlos que resguardam a
interação entre o código da aplicação e os ficheiros do sistema.

**Gestão de Memória:** É um conjunto de controlos que dizem respeito ao
uso de memória e do buffer.

**Gestão de Sessão:** É um conjunto de controlos que tratam da
manipulação de sessões HTTP de forma segura por aplicações Web.

**Impacto:** É o efeito negativo percetível para o negócio, resultante
da ocorrência de um evento indesejável, que por sua vez é o resultado da
exploração de vulnerabilidades.

**Integridade:** É a garantia de que as informações são precisas,
completas e válidas, e que não foram alteradas por uma ação não
autorizada.

**Limites de Confiança:** Normalmente, um limite de confiança é
constituído pelos componentes do sistema sobre os quais se tem controlo
direto. Todas as ligações e dados do sistema fora deste controlo direto
-- incluindo todos os clientes e sistemas geridos por terceiros -- devem
ser considerados como não sendo de confiança e necessitam de validação
na fronteira, antes de receberem permissões para realizarem interações
com o sistema.

**Mitigar:** São medidas tomadas para reduzir o grau de severidade de
uma vulnerabilidade. Essas medidas incluem a remoção de uma
vulnerabilidade, seja ao torná-la mais difícil de ser explorada, ou ao
reduzir o impacto negativo de uma exploração bem sucedida.

**Práticas de Criptografia**: Conjunto de controlos para garantir que as
operações de criptografia dentro da aplicação são executadas de modo
seguro.

**Práticas Gerais de Programação:** Conjunto de controlos abrangendo
práticas de codificação que não se encaixam facilmente noutras
categorias.

**Proteção dos Dados**: Conjunto de controlos para ajudar a garantir que
o software trata o armazenamento das informações de modo seguro.

**Realizar Log dos Eventos:** Esta operação deve incluir os seguintes
requisitos:

1.  Utilizar um timestamp[^401] proveniente de um sistema de
    confiança

2.  Classificar a gravidade para cada evento

3.  Destacar eventos de segurança relevantes, caso eles sejam misturados
    com outros registros de log

4.  Registar o identificador da conta ou utilizador que causou o evento

5.  Registar o endereço IP de origem que realizou o pedido

6.  Registar o resultado dos eventos (sucesso ou falha)

7.  Registar a descrição do evento

**Requisitos de Segurança:** Conjunto de requisitos funcionais e de
projeto para ajudar a garantir que o software é construído e
disponibilizado de forma segura.

**Segurança das Comunicações:** Conjunto de controlos para ajudar a
garantir o envio e o recebimento das informações de modo seguro.

**Segurança da Base de Dados:** Conjunto de controlos para garantir que
o software interage com as bases de dados de forma segura e que as bases
de dados estão configuradas de forma segura.

**Sistema:** É um termo genérico que abrange sistemas operativos,
servidores web, frameworks de aplicações e infraestrutura relacionada.

**Tratamento de Erros e Log:** Conjunto de práticas para garantir que a
aplicação realiza o tratamento dos erros de modo seguro e, também
realiza o registo de log dos eventos de modo apropriado.

**Tratamento dos Dados:** É o processo de tornar seguros os dados
potencialmente prejudiciais através do processo de remoção,
substituição, codificação ou *escaping*[^402] dos
caracteres.

**Validação de Entrada de Dados:** Conjunto de controlos para verificar
se as propriedades de todas as entradas de dados correspondem ao que é
esperado pela aplicação, como, por exemplo, tipo dos dados, tamanho,
intervalos e conjunto de caracteres aceitáveis que não contenham
caracteres maliciosos.

**Vulnerabilidade:** É uma fragilidade que torna um sistema suscetível a
um ataque ou a um dano.
