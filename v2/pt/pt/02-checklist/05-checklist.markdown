\newpage
# Lista de Verificação de Práticas de Programação Segura

## Validação dos Dados de Entrada

- [ ] Efetuar toda a validação dos dados num sistema de confiança. Por
    exemplo, centralizar todo o processo no servidor

- [ ] Identificar todas as fontes de dados e classificá-las como sendo ou
    não de confiança. Em seguida, validar os dados provenientes de
    fontes nas quais não exista confiança (ex: base de dados, stream de
    arquivos etc.)

- [ ] A rotina de validação de dados de entrada deve ser centralizada na
    aplicação

- [ ] Especificar o conjunto de caracteres apropriados, como UTF-8, para
    todas as fontes de entrada de dados

- [ ] Codificar os dados para um conjunto de caracteres comuns antes da
    validação (*Canonicalize*)

- [ ] Quando há falha de validação a aplicação deve rejeitar os dados
    fornecidos

- [ ] Determinar se o sistema suporta conjuntos de caracteres estendidos
    UTF-8 e em caso afirmativo, validar após efetuar a descodificação
    UTF-8

- [ ] Validar todos os dados provenientes dos clientes antes do
    processamento, incluindo todos os parâmetros, campos de formulário,
    conteúdos das URLs e cabeçalhos HTTP, como, por exemplo, os nomes e
    os valores dos Cookies. Certificar-se, também, de incluir mecanismos
    automáticos de *postback*[^301] nos blocos de código
    JavaScript, Flash ou qualquer outro código embutido

- [ ] Verificar se os valores de cabeçalho, tanto dos pedidos, como das
    respostas, contêm apenas caracteres ASCII

- [ ] Validar dados provenientes de redirecionamentos. Os atacantes podem
    incluir conteúdo malicioso diretamente para o alvo do mecanismo de
    redirecionamento, podendo assim contornar a lógica da aplicação e
    qualquer validação executada antes do redirecionamento

- [ ] Validar tipos de dados esperados

- [ ] Validar intervalo de dados

- [ ] Validar o tamanho dos dados

- [ ] Validar, sempre que possível, todos os dados de entrada através de
    um método baseado em "listas brancas\" que utilizam uma lista de
    caracteres ou expressões regulares para definirem os caracteres
    permitidos

- [ ] Se qualquer caractere potencialmente perigoso precisa ser permitido
    na entrada de dados da aplicação, certifique-se que foram
    implementados mecanismos adicionais como codificação dos dados de
    saída, APIs especificas que fornecem tarefas seguras e caminhos de
    auditoria no uso dos dados pela aplicação. A seguir, como exemplo de
    caracteres "potencialmente perigosos", temos: \<, \>, \", \', %, (,
    ), &, +, \\, \\\', \\\"

- [ ] Se a rotina de validação padrão não abordar as seguintes entradas,
    então elas devem ser verificadas:

    a.  Verificar bytes nulos (%00)

    b.  Verificar se há caracteres de nova linha (%0d, %0a, \\r, \\n)

    c.  Verificar se há caracteres "ponto-ponto barra" (../ ou ..\\) que
        alteram caminhos. Nos casos de
        conjunto de caracteres que usem a extensão UTF-8, o sistema deve
        utilizar representações alternativas como: %c0%ae%c0%ae/. A
        *canonicalização* deve ser utilizada para resolver problemas de
        codificação dupla (double encoding[^302]) ou outras formas
        de ataques por ofuscação

## Codificação de Dados de Saída

- [ ] Efetuar toda a codificação dos dados num sistema de confiança, por
    exemplo, centralizar todo o processo no servidor

- [ ] Utilizar uma rotina padrão, testada, para cada tipo de codificação
    de saída

- [ ] Realizar a codificação, baseada em contexto, de todos os dados
    enviados para o cliente que têm origem num ambiente fora dos limites
    de confiança da aplicação. A codificação das entidades HTML é um
    exemplo, mas nem sempre funciona para todos os casos

- [ ] Codificar todos os caracteres, a menos que sejam conhecidos por
    serem seguros para o interpretador de destino

- [ ] Realizar o tratamento (limpeza), baseado em contexto, de todos os
    dados provenientes de fontes que não sejam de confiança usados para
    construir consultas SQL, XML, e LDAP

- [ ] Tratar todos os dados provenientes de fontes que não sejam de
    confiança que gerem comandos para o sistema operativo

## Autenticação e Gestão de Credenciais

- [ ] Requerer autenticação para todas as páginas e recursos, exceto para
    aqueles que são intencionalmente públicos

- [ ] Os mecanismos de autenticação devem ser executados num sistema de
    confiança, por exemplo, centralizar todo o processo no servidor

- [ ] Sempre que possível, estabelecer e utilizar serviços de autenticação
    padronizados e testados

- [ ] Utilizar uma implementação centralizada para realizar os
    procedimentos de autenticação, disponibilizando bibliotecas que
    invocam os serviços de autenticação externos

- [ ] Separar a lógica de autenticação do recurso que está a ser
    requisitado e usar redirecionadores dos controladores de
    autenticação centralizados

- [ ] Quando ocorrerem situações excecionais nos controladores de
    autenticação, executar procedimentos em caso de falha com o
    propósito de manter o sistema seguro

- [ ] Todas as funções administrativas e de gestão de contas devem ser tão
    seguras quanto o mecanismo de autenticação principal

- [ ] Se a aplicação gerir um repositório de credenciais, esta deverá
    garantir que as senhas são armazenadas na base de dados somente sob
    a forma de resumo/*hash* da senha na forma de *one-way salted
    hashes*[^303], e que a tabela/arquivo que armazena as
    senhas e as próprias chaves são manipuladas apenas pela aplicação.
    Não utilizar o algoritmo de hash MD5, sempre que esse puder ser
    evitado

- [ ] A geração dos resumos (*hash*) das senhas deve ser executada num
    sistema de confiança, por exemplo, centralizar o controlo no
    servidor

- [ ] Validar os dados de autenticação somente no final de todas as
    entradas de dados, especialmente para as implementações de
    *autenticação sequencial*

- [ ] As mensagens de falha na autenticação não devem indicar
    qual parte dos dados de autenticação está
    incorreta. Por exemplo, em vez de exibir mensagens como "Nome de
    utilizador incorreto" ou "Senha incorreta", utilize apenas mensagens
    como: "Utilizador e/ou senha inválidos", para ambos os casos de erro. As
    respostas de erro devem ser idênticas nos dois casos

- [ ] Utilizar autenticação para ligação a sistemas externos que envolvam
    tráfego de informação sensível ou acesso a funções

- [ ] As credenciais de autenticação para aceder a serviços externos à
    aplicação devem ser cifradas e armazenadas num local protegido num
    sistema de confiança, por exemplo, no servidor da aplicação. Obs.: o
    código-fonte não é considerado um local seguro

- [ ] Utilizar apenas pedidos POST para transmitir credenciais de
    autenticação

- [ ] Somente trocar senhas (não temporárias) através de uma ligação
    protegida (SSL/TLS) ou como dado cifrado, como no caso de envio de
    e-mail cifrado. Senhas temporárias enviadas por e-mail podem ser um
    caso de exceção aceitável

- [ ] Exigir que os requisitos de complexidade de senha estabelecidos pela
    política ou regulamento sejam cumpridos. As credenciais de
    autenticação devem ser suficientes para resistir a ataques que,
    tipicamente, ameaçam o ambiente de produção. Um exemplo pode ser a
    exigência do uso simultâneo de caracteres alfabéticos, numérico e/ou
    caracteres especiais

- [ ] Exigir que os requisitos de comprimento de senha estabelecidos pela
    política ou regulamento sejam cumpridos. O uso de oito caracteres é
    o mais comum, porém usar 16 é mais recomendado. Considere, ainda, o
    uso de senhas que contenham várias palavras (uma frase)

- [ ] A entrada da senha deve ser ocultada no dispositivo de apresentação
    do utilizador. Em HTML, utilize o campo com o tipo \"password\"

- [ ] Desativar a conta após um número pré-definido de tentativas
    inválidas de autenticação (ex: cinco tentativas é o mais comum). A
    conta deve ser desativada por um período de tempo suficientemente
    longo para desencorajar a dedução das credenciais pelo método de
    força bruta, mas não tão longo ao ponto de permitir um ataque de
    negação de serviço

- [ ] Os processos de redefinição de senhas e operações de mudanças devem
    exigir os mesmos níveis de controlo previstos para a criação de
    contas e autenticação

- [ ] Esquemas de pergunta/resposta (pré-definidas) usadas para a
    redefinição da senha devem evitar ataques que lançam respostas
    aleatórias. Por exemplo, "livro favorito" é uma questão fraca, pois
    "A Bíblia" é uma resposta muito comum

- [ ] Se optar por usar redefinição de senha baseada em e-mail, envie um
    e-mail somente para o endereço pré-definido contendo um *link* ou
    senha de acesso temporário que permitam ao utilizador redefinir a
    senha

- [ ] O tempo de validade das senhas e dos *links* temporários deve ser
    curto

- [ ] Exigir a mudança de senhas temporárias na próxima vez que o
    utilizador realizar a autenticação no sistema

- [ ] Notificar o utilizador quando a sua senha for reiniciada (*reset*)

- [ ] Prevenir a reutilização de senhas

- [ ] As senhas devem ter, pelo menos, um dia de duração antes de poderem
    ser alteradas, a fim de evitar ataques de reutilização de senhas

- [ ] Garantir que a troca de senhas está em conformidade com os
    requisitos estabelecidos na política ou regulamento. Sistemas
    críticos podem exigir alterações mais frequentes nas credenciais de
    segurança. O tempo entre as trocas de senhas deve ser controlado
    administrativamente

- [ ] Desativar a funcionalidade de lembrar a senha nos campos de senha do
    navegador

- [ ] A data/hora da última utilização (bem ou mal sucedida) de uma conta
    de utilizador deve ser comunicada na próxima entrada no sistema

- [ ] Realizar monitorização para identificar ataques contra várias contas
    de utilizadores, utilizando a mesma senha. Esse padrão de ataque é
    utilizado para explorar o uso de senhas padrão

- [ ] Modificar todas as senhas que, por padrão, são definidas pelos
    fornecedores, bem como os identificadores de utilizadores (IDs) ou
    desativar as contas associadas

- [ ] Exigir nova autenticação dos utilizadores antes da realização de
    operações críticas

- [ ] Utilizar *autenticação de múltiplos fatores* (utilizando
    simultaneamente token, senha, biometria etc.[^304]) para
    contas altamente sensíveis ou de elevado valor transacional

- [ ] Caso utilize código de terceiros para realizar a autenticação,
    inspecione-o cuidadosamente para garantir que o mesmo não é afetado
    por qualquer código malicioso

## Gestão de Sessões

- [ ] Utilizar controlos de gestão de sessão baseados no servidor ou em
    framework. A aplicação deve reconhecer apenas esses identificadores
    de sessão como válidos

- [ ] A criação dos identificadores de sessão deve ser sempre realizada
    num sistema de confiança, por exemplo, centralizado no servidor

- [ ] O controlo de gestão de sessão deve usar algoritmos conhecidos,
    padronizados e bem testados que garantam a aleatoriedade dos
    identificadores de sessão

- [ ] Definir o domínio e o caminho para os cookies que contêm
    identificadores de sessão autenticados, para um valor devidamente
    restrito para o site

- [ ] A funcionalidade de saída (*logout*) deve encerrar completamente a
    sessão ou ligação associada

- [ ] A funcionalidade de saída (*logout*) deve estar disponível em todas
    as páginas que requerem autenticação

- [ ] Estabelecer um tempo de expiração da sessão que seja o mais curto
    possível, baseado no balanceamento dos riscos e requisitos
    funcionais do negócio. Na maioria dos casos não deve ser mais do que
    algumas horas

- [ ] Não permitir logins persistentes (sem prazo de expiração) e realizar
    o encerramento da sessão periodicamente, mesmo quando ela estiver
    ativa. Isso deve ser feito, especialmente, em aplicações que
    suportam várias ligações de rede ou que se ligam a sistemas
    críticos. O tempo de encerramento deve estar de acordo com os
    requisitos do negócio e o utilizador deve receber notificações
    suficientes para atenuar os impactos negativos dessa medida

- [ ] Se uma sessão estava estabelecida antes do login ela deve ser
    encerrada para que uma nova seja estabelecida após o login

- [ ] Gerar um novo identificador de sessão quando houver uma nova
    autenticação

- [ ] Não permitir conexões simultâneas com o mesmo identificador de
    utilizador

- [ ] Não expor os identificadores de sessão em URLs, mensagens de erro ou
    logs. Os identificadores de sessão devem apenas ser encontrados no
    cabeçalho do cookie HTTP. Por exemplo, não enviar os identificadores
    de sessão sob a forma de parâmetros GET

- [ ] Proteger os dados de sessão do lado servidor contra acessos não
    autorizados por outros utilizadores do servidor, através da
    implementação de controlos de acesso apropriados no servidor

- [ ] Gerar um novo identificador de sessão e desativar o antigo
    periodicamente. Isso pode mitigar certos cenários de ataques de
    rapto de sessão (*session hijacking*), quando o identificador de
    sessão original for comprometido

- [ ] Gerar um novo identificador de sessão caso a segurança da ligação
    mude de HTTP para HTTPS, como pode ocorrer durante a autenticação.
    Internamente à aplicação, é recomendável utilizar HTTPS de forma
    constante em vez de alternar entre HTTP e HTTPS

- [ ] Utilizar mecanismos complementares ao mecanismo padrão de gestão de
    sessões para operações sensíveis do lado do servidor -- como no caso
    de operações de gestão de contas -- através da
    utilização de tokens aleatórios ou parâmetros associados à sessão. Este
    método pode ser usado para prevenir ataques do tipo Cross Site Request
    Forgery (CSRF)

- [ ] Utilizar mecanismos complementares à gestão de sessões para
    operações altamente sensíveis ou críticas, utilizando tokens
    aleatórios ou parâmetros em cada requisição em vez de basear-se
    apenas na sessão

- [ ] Configurar o atributo \"secure\" para cookies transmitidos através
    de uma ligação TLS

- [ ] Configurar os cookies com o atributo "HttpOnly", a menos que seja
    explicitamente necessário ler ou definir os valores dos mesmos
    através de scripts do lado cliente da aplicação

## Controlo de Acessos

- [ ] Utilizar apenas objetos do sistema que sejam de confiança, como
    ocorre com os objetos de sessão do servidor, para realizar a tomada
    de decisão sobre a autorização de acesso

- [ ] Utilizar um único componente em toda a aplicação Web para realizar o
    processo de verificação de autorização de acesso. Isto inclui
    bibliotecas que invocam os serviços externos de autorização

- [ ] Quando ocorrer alguma falha no controlo de acesso, ela deve ocorrer
    de modo seguro

- [ ] Negar todos os acessos, caso a aplicação não consiga ter acesso às
    informações contidas na configuração de segurança

- [ ] Garantir o controlo de autorização em todos os pedidos, inclusive em
    scripts do lado do servidor, \"includes\" e pedidos provenientes de
    tecnologias do lado cliente, como AJAX e Flash

- [ ] Isolar do código da aplicação os trechos de código que contêm lógica
    priviligiada

- [ ] Restringir o acesso aos arquivos e outros recursos, incluindo
    aqueles que estão fora do controle direto da aplicação, somente aos
    utilizadores autorizados

- [ ] Restringir o acesso às URLs protegidas somente aos utilizadores
    autorizados

- [ ] Restringir o acesso às funções protegidas somente aos utilizadores
    autorizados

- [ ] Restringir o acesso às referências diretas aos objetos somente aos
    utilizadores autorizados

- [ ] Restringir o acesso aos serviços somente aos utilizadores
    autorizados

- [ ] Restringir o acesso aos dados da aplicação somente aos utilizadores
    autorizados

- [ ] Restringir o acesso aos atributos e dados dos utilizadores, bem como
    informações das políticas usadas pelos mecanismos de controle de
    acesso

- [ ] Restringir o acesso às configurações de segurança relevantes apenas
    aos utilizadores autorizados

- [ ] As regras de controlo de acesso representadas pela camada de
    apresentação devem coincidir com as regras presentes no lado
    servidor

- [ ] Se o *estado dos dados* deve ser armazenado no lado do cliente,
    utilizar mecanismos de criptografia e verificação de integridade no
    lado servidor para detetar possíveis adulterações

- [ ] Garantir que os fluxos lógicos da aplicação obedecem as regras de
    negócio

- [ ] Limitar o número de transações que um único utilizador ou
    dispositivo pode executar em determinado período de tempo. As
    transações por período de tempo devem estar acima das necessidades
    reais do negócio, mas abaixo o suficiente para impedir ataques
    automatizados

- [ ] Utilizar o campo "referer" do cabeçalho somente como forma de
    verificação suplementar. O mesmo não deve ser usado sozinho como
    forma de validação de autorização porque ele pode ter o valor
    adulterado

- [ ] Se for permitida a existência de sessões autenticadas por longos
    períodos de tempo, fazer a revalidação periódica da autorização do
    utilizador para garantir que os privilégios não foram modificados e,
    caso tenham sido, realizar o registo em log do utilizador e exigir
    nova autenticação

- [ ] Implementar a auditoria das contas de utilizador e assegurar a
    desativação de contas não utilizadas.
    Por exemplo: a conta deve ser desativada não mais do que 30 dias após a
    expiração da senha

- [ ] A aplicação deve dar suporte à desativação de contas e ao
    encerramento das sessões quando terminar a autorização do
    utilizador. Por exemplo: quando ocorrer alguma alteração dos dados
    do utilizador, situação profissional, processos de negócio etc.

- [ ] As contas de serviço ou contas de suporte a ligações provenientes ou
    destinadas a serviços externos devem possuir o menor privilégio
    possível

- [ ] Criar uma Política de Controlo de Acesso para documentar as regras
    de negócio da aplicação, tipos de dados e critérios ou processos de
    autorização para que os acessos possam ser devidamente concedidos e
    controlados. Isto inclui identificar requisitos de acessos, tanto
    para os dados, como para os recursos do sistema

## Práticas de Criptografia

- [ ] Todas as funções de criptografia utilizadas para proteger dados
    sensíveis dos utilizadores da aplicação, devem ser implantadas num
    sistema de confiança (neste caso o servidor)

- [ ] A senha mestre deve ser protegida contra acessos não autorizados

- [ ] Quando ocorrer alguma falha nos módulos de criptografia, permitir
    que as mesmas ocorram de modo seguro

- [ ] Todos os números, nomes de arquivos, GUIDs e strings aleatórias
    devem ser gerados usando um módulo criptográfico com gerador de
    números aleatórios, somente se os valores aleatórios gerados forem
    impossíveis de serem deduzidos

- [ ] Os módulos de criptografia usados pela aplicação devem ser
    compatíveis com a FIPS 140-2 ou com um padrão equivalente
    ([http://csrc.nist.gov/groups/STM/cmvp/validation.html])

- [ ] Estabelecer e utilizar uma política e processo que defina como é
    realizada a gestão das chaves criptográficas

## Tratamento de Erros e Log

- [ ] Não expor informações sensíveis nas repostas de erros, inclusive
    detalhes de sistema, identificadores de sessão ou informação da
    conta do utilizador

- [ ] Usar mecanismos de tratamento de erros que não mostrem informações
    de depuração (*debug*) ou informações da pilha de exceção

- [ ] Usar mensagens de erro genéricas e páginas de erro personalizadas

- [ ] A aplicação deve tratar os erros sem se basear nas configurações do
    servidor

- [ ] A memória reservada deve ser libertada de modo apropriado quando
    ocorrerem condições de erro

- [ ] O tratamento de erros lógicos associados com os controlos de
    segurança devem, por padrão, negar o acesso

- [ ] Todos os controlos de log devem ser implementados num sistema de
    confiança, por exemplo, centralizar todo o processo no servidor

- [ ] Os controlos de log devem dar suporte tanto para os casos de sucesso
    como os de falha relacionados com os eventos de segurança

- [ ] Garantir que os logs armazenam eventos importantes

- [ ] Garantir que as entradas de log que incluam dados nos quais não se
    confia não sejam executadas como código-fonte na interface de
    visualização de logs

- [ ] Restringir o acesso aos logs apenas para pessoal autorizado

- [ ] Utilizar uma rotina centralizada para realizar todas as operações de
    log

- [ ] Não armazenar informações sensíveis nos registos de logs, como
    detalhes desnecessários do sistema, identificadores de sessão e
    senhas

- [ ] Garantir o uso de algum mecanismo que conduza (ou facilite) o
    processo de análise de logs

- [ ] Registar em log todas as falhas de validação de entrada de dados

- [ ] Registar em log todas as tentativas de autenticação, especialmente
    as que falharam por algum motivo

- [ ] Registar em log todas as falhas de controlo de acesso

- [ ] Registar em log todos os eventos suspeitos de adulteração, inclusive
    alterações inesperadas no estado dos dados

- [ ] Registar em log as tentativas de ligação com tokens de sessão
    inválidos ou expirados

- [ ] Registar em log todas as exceções lançadas pelo sistema

- [ ] Registar em log todas as funções administrativas, inclusive as
    mudanças realizadas nas configurações de segurança

- [ ] Registar em log todas as falhas de ligação TLS com o backend

- [ ] Registar em log todas as falhas que ocorreram nos módulos de
    criptografia

- [ ] Utilizar uma função de hash criptográfica para validar a integridade
    dos registros de log

## Proteção de Dados

- [ ] Implementar uma política de privilégio mínimo, restringindo os
    utilizadores apenas às funcionalidades, dados e informações do
    sistema que são necessárias para executarem as suas tarefas

- [ ] Proteger contra acesso não autorizado todas as cópias temporárias ou
    registadas em cache que contenham dados sensíveis e estejam
    armazenadas no servidor e excluir esses arquivos logo que não forem
    mais necessários

- [ ] Cifrar informações altamente sensíveis quando armazenadas -- como
    dados de verificação de autenticação -- mesmo que estejam no lado
    servidor, usando sempre algoritmos conhecidos, padronizados e bem
    testados. Consulte a secção que trata sobre "Práticas de
    Criptografia" para orientações adicionais

- [ ] Proteger o código-fonte presente no servidor para que não seja
    descarregado por algum utilizador

- [ ] Não armazenar senhas, strings de ligação ou outras informações
    confidenciais em texto claro/legível ou em qualquer forma
    criptograficamente insegura no lado cliente. Isto é válido também
    quando há utilização de formatos inseguros como: MS viewstate, Adobe
    Flash ou código compilado que corre no lado do cliente

- [ ] Remover comentários do código de produção que podem ser acessados
    pelos utilizadores e podem revelar detalhes internos do sistema ou
    outras informações sensíveis

- [ ] Remover aplicações desnecessárias e documentação do sistema que
    possam revelar informações importantes para os atacantes

- [ ] Não incluir informações sensíveis nos parâmetros de pedidos HTTP GET

- [ ] Desativar a funcionalidade de auto completar nos formulários que
    contenham informações sensíveis, inclusive no formulário de
    autenticação

- [ ] Desativar a cache realizada no lado do cliente das páginas que
    contenham informações sensíveis. O parâmetro **Cache-Control:
    no-store**, pode ser usado em conjunto com o controlo definido no
    cabeçalhos HTTP **"Pragma: no-cache"**, que é menos efetivo, porém
    compatível com HTTP/1.0

- [ ] A aplicação deve dar suporte à remoção de dados sensíveis quando
    estes não forem mais necessários. Por exemplo: informação pessoal ou
    dados financeiros

- [ ] Implementar mecanismos de controlo de acesso apropriados para dados
    sensíveis armazenados no servidor. Isto inclui dados em cache,
    arquivos temporários e dados que devem ser acessíveis somente
    por utilizadores específicos do sistema

## Segurança nas comunicações

- [ ] Utilizar criptografia na transmissão de todas as informações
    sensíveis. Isto deve incluir TLS para proteger a ligação e deve ser
    complementado com criptografia de ficheiros que contém dados
    sensíveis ou ligações que não usam o protocolo HTTP

- [ ] Os certificados TLS devem ser válidos, possuírem o nome de domínio
    correto, não estarem expirados e serem instalados com certificados
    intermédios, quando necessário

- [ ] Quando ocorrer alguma falha nas ligações TLS, o sistema não deve
    fornecer uma ligação insegura

- [ ] Utilizar ligações TLS para todo o conteúdo que requer acesso
    autenticado ou ou que contenha informação sensível

- [ ] Utilizar TLS para ligações com sistemas externos que envolvam
    funções ou informações sensíveis

- [ ] Utilizar um padrão único de implementação TLS configurado de modo
    apropriado

- [ ] Especificar a codificação dos caracteres para todas as conexões

- [ ] Filtrar os parâmetros que contenham informações sensíveis,
    provenientes do "HTTP referer", nos links para sites externos

## Configuração do Sistema

- [ ] Garantir que os servidores, frameworks e componentes do sistema
    estão a executar a última versão aprovada

- [ ] Garantir que os servidores, frameworks e componentes do sistema
    possuem as atualizações mais recentes aplicadas para a versão em uso

- [ ] Desativar a listagem de diretórios

- [ ] Restringir, para o mínimo possível, os privilégios do servidor Web,
    dos processos e das contas de serviços

- [ ] Quando ocorrerem exceções no sistema, garantir que as falhas ocorrem
    de modo seguro

- [ ] Remover todas as funcionalidades e arquivos desnecessários

- [ ] Remover código de teste ou qualquer funcionalidade desnecessária
    para o ambiente de produção, antes de disponibilizar o sistema no
    servidor de produção

- [ ] Prevenir a divulgação da estrutura de diretórios impedindo que
    robôs[^305] de busca façam a indexação de arquivos
    sensíveis, através da configuração do arquivo
    "robots.txt"[^306]. Os diretórios que não devem ser
    acessados por estes indexadores devem ser colocados num diretório
    isolado. Assim, apenas é necessário negar o acesso ao diretório pai
    definido no arquivo "robots.txt", evitando ter que negar o acesso a
    cada diretório individualmente

- [ ] Definir quais métodos HTTP, GET ou POST, a aplicação irá suportar e
    se serão tratados de modo diferenciado nas diversas páginas da
    aplicação

- [ ] Desativar as extensões HTTP desnecessárias como, por exemplo, o
    WebDAV. Caso seja necessário o uso de alguma extensão HTTP com o
    propósito de suportar a manipulação de arquivos, utilize um
    mecanismo de autenticação conhecido, padronizado e bem testado

- [ ] Se o servidor processa tanto pedidos HTTP 1.0 como HTTP 1.1,
    certificar-se de que ambos são
    configurados de modo semelhante ou assegure que qualquer diferença que
    possa existir seja compreendida, como, por exemplo, o manuseamento de
    métodos HTTP estendidos

- [ ] Remover informações desnecessárias presentes nos cabeçalhos de
    resposta HTTP e que podem estar relacionadas com o sistema
    operativo, versão do servidor web e frameworks de aplicação

- [ ] O armazenamento da configuração de segurança para a aplicação deve
    ser capaz de ser produzida de forma legível para dar suporte à
    auditoria

- [ ] Implementar um sistema de gestão de ativos para manter o registo dos
    componentes e programas

- [ ] Isolar o ambiente de desenvolvimento da rede de produção e conceder
    acesso somente para grupos de desenvolvimento e testes. É comum os
    ambientes de desenvolvimento serem configurados de modo menos seguro
    do que os ambientes de produção. Deste modo, os atacantes podem usar
    essa diferença para descobrir vulnerabilidades comuns ou encontrar
    formas de exploração das mesmas

- [ ] Implementar um sistema de controlo de mudanças para gerir e registar
    as alterações no código, tanto de desenvolvimento, como dos sistemas
    em produção

## Segurança em Base de Dados

- [ ] Usar *consultas parametrizadas* fortemente tipificadas

- [ ] Utilizar validação de entrada e codificação de saída e assegurar a
    abordagem de meta caracteres. Se houver falha, o comando não deverá
    ser executado na base de dados

- [ ] Certificar-se de que as variáveis são fortemente tipificadas

- [ ] Realizar a codificação (escaping) de meta caracteres em instruções
    SQL[^307]

- [ ] A aplicação deve usar o menor nível possível de privilégios ao
    aceder a base de dados

- [ ] Usar credenciais seguras para aceder a base de dados

- [ ] Não incluir strings de ligação na aplicação. As strings de ligação
    devem ser armazenadas num arquivo de configuração separado,
    armazenado num sistema de confiança e as informações devem ser
    cifradas

- [ ] Usar procedimentos armazenados (*stored procedures*) para abstrair o
    acesso aos dados e permitir a remoção de permissões das tabelas no
    banco de dados

- [ ] Encerrar a ligação assim que possível

- [ ] Remover ou modificar senhas padrão de contas administrativas.
    Utilizar senhas robustas (pouco comuns ou difíceis de deduzir) ou
    implementar autenticação de múltiplos fatores. Desativar qualquer
    funcionalidade desnecessária na base de dados, como "stored
    procedures" ou serviços não utilizados. Instalar o conjunto mínimo
    de componentes ou de opções necessárias (redução da superfície de
    ataque)

- [ ] Eliminar o conteúdo desnecessário incluído por padrão pelo
    fornecedor como esquemas e bases de dados de exemplo

- [ ] Desativar todas as contas criadas por padrão e que não sejam
    necessárias para suportar os requisitos de negócio

- [ ] A aplicação deve ligar-se à base de dados com diferentes credenciais
    de segurança para cada tipo de necessidade como, por exemplo,
    utilizador, somente leitura, convidado ou administrador

## Gestão de Ficheiros

- [ ] Não passar dados fornecidos pelos utilizadores diretamente a uma
    função de inclusão dinâmica

- [ ] Solicitar autenticação antes de permitir que seja feito o
    carregamento de ficheiros

- [ ] Limitar os tipos de ficheiros que podem ser enviados para aceitar
    somente os necessários ao propósito do negócio

- [ ] Validar se os ficheiros enviados são do tipo esperado, através da
    validação dos cabeçalhos, pois, realizar a verificação apenas pela
    extensão não é suficiente

- [ ] Não gravar ficheiros no mesmo diretório de contexto da aplicação
    Web. Os ficheiros devem ser armazenados no servidor de conteúdos ou
    na base de dados

- [ ] Prevenir ou restringir o carregamento de qualquer ficheiro que possa
    ser interpretado ou executado pelo servidor Web

- [ ] Desativar privilégios de execução nos diretórios de armazenamento de
    ficheiros

- [ ] Implantar o carregamento seguro nos ambientes UNIX por meio da
    montagem do diretório de destino como uma unidade lógica, usando o
    caminho associado ou o ambiente de "chroot"

- [ ] Ao referenciar ficheiros, usar uma lista branca (*whitelist*) de
    nomes e de tipos de ficheiros permitidos. Realizar a validação do
    valor do parâmetro passado e caso ele não corresponda ao que é
    esperado, rejeitar a entrada ou utilizar um valor padrão

- [ ] Não transmitir, sem nenhum tipo de tratamento, os dados informados
    pelo utilizador a redirecionamentos dinâmicos. Se isso for
    necessário, o redirecionamento deverá aceitar apenas URLs relativas
    e validadas

- [ ] Não passar caminhos de diretórios ou de ficheiros em pedidos. Usar
    algum mecanismo de mapeamento desses recursos para índices definidos
    numa lista pré-definida de caminhos

- [ ] Nunca enviar o caminho absoluto do ficheiro para o cliente

- [ ] Certificar-se de que os ficheiros da aplicação e os recursos estão
    definidos somente com o atributo de leitura

- [ ] Verificar os ficheiros que os utilizadores submeterem através do
    mecanismo de carregamento em busca de vírus e malwares

## Gestão de Memória

- [ ] Utilizar controlo de entrada/saída de dados que não sejam de
    confiança

- [ ] Verificar se o buffer é tão grande quanto o especificado

- [ ] Ao usar funções que aceitem determinado número de bytes para
    realizar cópias, como strncpy(), esteja ciente de que se o tamanho
    do buffer de destino for igual ao tamanho do buffer de origem, ele
    não pode encerrar a sequência de caracteres com valor nulo (null)

- [ ] Verificar os limites do buffer caso as chamadas à função sejam
    realizadas em ciclos e verificar se não há nenhum risco de ocorrer
    gravação de dados além do espaço reservado

- [ ] Truncar todas as strings de entrada para um tamanho razoável antes
    de passá-las para as funções de cópia e concatenação

- [ ] Na liberação de recursos reservados para objetos de ligação,
    identificadores de ficheiro etc., não contar com o "*garbage
    collector*" e realizar a tarefa explicitamente

- [ ] Usar pilhas não executáveis, quando disponíveis

- [ ] Evitar o uso de funções reconhecidamente vulneráveis como printf(),
    strcat(), strcpy() etc.

- [ ] Liberar a memória reservada de modo apropriado após concluir a
    sub-rotina (função/método) e em todos pontos de saída

## Práticas Gerais de Programação:

- [ ] Para tarefas comuns, utilizar sempre código testado, gerido e
    aprovado ao invés de criar código novo e não gerido

- [ ] Utilizar APIs que executem tarefas específicas para realizar
    operações do sistema operativo. Não permitir que a aplicação execute
    comandos diretamente no sistema operativo, especialmente através da
    utilização de "shells" de comando iniciadas pela aplicação

- [ ] Utilizar mecanismos de verificação de integridade por "checksum" ou
    "hash" para verificar a integridade do código interpretado,
    bibliotecas, ficheiros executáveis e ficheiros de configuração

- [ ] Utilizar mecanismos de bloqueio para evitar pedidos simultâneos para
    a aplicação ou utilizar um mecanismo de sincronização para evitar
    condições de concorrência (*race conditions*)

- [ ] Proteger as variáveis partilhadas e os recursos contra acessos
    concorrentes inapropriados

- [ ] Instanciar explicitamente todas as variáveis e dados persistentes
    durante a declaração, ou antes da primeira utilização

- [ ] Quando a aplicação tiver que ser executada com privilégios elevados,
    aumentar os privilégios o mais tarde possível e revogá-los logo que
    seja possível

- [ ] Evitar erros de cálculo decorrentes da falta de entendimento da
    representação interna da linguagem de programação usada e de como é
    realizada a interação com os aspetos de cálculo numérico. Prestar
    bastante atenção nas discrepâncias de tamanho de byte, precisão,
    distinções de sinal (signed/unsigned), truncamento, conversão e
    "casting" entre os tipos, cálculos que devolvam erros do tipo
    "not-a-number" e, também, como a linguagem de programação trata a
    representação interna de números muito grandes ou muito pequenos

- [ ] Não transferir, diretamente, dados fornecidos pelo utilizador para
    qualquer função de execução dinâmica sem realizar o *tratamento dos
    dados* de modo adequado

- [ ] Restringir a geração e a alteração de código por parte dos
    utilizadores

- [ ] Rever todas as aplicações secundárias, códigos e bibliotecas de
    terceiros para determinar a necessidade do negócio e validar as
    funcionalidades de segurança, uma vez que estas podem introduzir
    novas vulnerabilidades

- [ ] Implementar atualizações de modo seguro. Se a aplicação precisar
    realizar atualizações automáticas, utilizar mecanismos de assinatura
    digital para garantir a integridade do código e garantir que os
    clientes façam a verificação da assinatura após descarregarem as
    atualizações. Usar canais cifrados para transferir o código a partir
    do host do servidor
