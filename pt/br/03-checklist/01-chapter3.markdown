\newpage
# Lista de Verificação de Práticas de Programação Segura

## Validação dos Dados de Entrada

- [ ]   Efetuar toda a validação dos dados em um sistema confiável. Por
    exemplo, centralizar todo o processo no servidor

- [ ]   Identificar todas as fontes de dados e classificá-las como sendo
    confiáveis ou não. Em seguida, validar os dados provenientes de
    fontes nas quais não se possa confiar (ex: base de dados, stream de
    arquivos etc.)

- [ ]   A rotina de validação de dados de entrada deve ser centralizada na
    aplicação

- [ ]   Especificar o conjunto de caracteres apropriado, como UTF-8, para
    todas as fontes de entrada de dados

- [ ]   Codificar os dados para um conjunto de caracteres comuns antes da
    validação (*Canonicalize*)

- [ ]   Quando há falha de validação, a aplicação deve rejeitar os dados
    fornecidos

- [ ]   Determinar se o sistema suporta conjuntos de caracteres estendidos
    UTF-8 e, em caso afirmativo, validar após efetuar a descodificação
    UTF-8

- [ ]   Validar todos os dados provenientes dos clientes antes do
    processamento, incluindo todos os parâmetros, campos de formulário,
    conteúdos das URLs e cabeçalhos HTTP, como, por exemplo, os nomes e
    os valores dos Cookies. Certificar-se, também, de incluir mecanismos
    automáticos de *postback*[^301] nos blocos de código
    JavaScript, Flash ou qualquer outro código embutido

- [ ]   Verificar se os valores de cabeçalho, tanto das requisições, como
    das respostas, contêm apenas caracteres ASCII

- [ ]   Validar dados provenientes de redirecionamentos. Os atacantes podem
    incluir conteúdo malicioso diretamente para o alvo do mecanismo de
    redirecionamento, podendo assim contornar a lógica da aplicação e
    qualquer validação executada antes do redirecionamento

- [ ]   Validar tipos de dados esperados

- [ ]   Validar intervalo de dados

- [ ]   Validar o tamanho dos dados

- [ ]   Validar, sempre que possível, todos os dados de entrada através de
    um método baseado em "listas brancas\" que utilizem uma lista de
    caracteres ou expressões regulares para definirem os caracteres
    permitidos

- [ ]   Se qualquer caractere potencialmente perigoso precisa ser permitido
    na entrada de dados da aplicação, certificar-se de que foram
    implementados controles adicionais como codificação dos dados de
    saída, APIs especificas que fornecem tarefas seguras e trilhas de
    auditoria no uso dos dados pela aplicação. A seguir, como exemplo de
    caracteres "potencialmente perigosos",
    temos: \<, \>, \", \', %, (, ), &, +, \\, \\\', \\\"

- [ ]   Se a rotina de validação padrão não abordar as seguintes entradas,
    então elas devem ser verificadas:

    a.  Verificar bytes nulos (%00)

    b.  Verificar se há caracteres de nova linha (%0d, %0a, \\r, \\n)

    c.  Verificar se há caracteres "ponto-ponto barra" (../ ou ..\\) que
        alteram caminhos. Nos casos de conjunto de caracteres que usem a extensão UTF-8, o sistema deve
        utilizar representações alternativas como: %c0%ae%c0%ae/. A
        *canonicalização* deve ser utilizada para resolver problemas de
        codificação dupla (double encoding[^302] ou outras formas
        de ataques por ofuscação

## Codificação de Dados de Saída

- [ ]   Efetuar toda a codificação dos dados em um sistema confiável, por
    exemplo, centralizar todo o processo no servidor

- [ ]   Utilizar uma rotina padrão, testada, para cada tipo de codificação
    de saída

- [ ]   Realizar a codificação, baseada em contexto, de todos os dados
    enviados para o cliente que têm origem em um ambiente fora dos
    limites de confiança da aplicação. A codificação das entidades HTML
    é um exemplo, mas nem sempre funciona para todos os casos

- [ ]   Codificar todos os caracteres, a menos que sejam conhecidos por
    serem seguros para o interpretador de destino

- [ ]   Realizar o tratamento (*sanitização*), baseado em contexto, de todos
    os dados provenientes de fontes não confiáveis usados para construir
    consultas SQL, XML, e LDAP

- [ ]   Tratar todos os dados provenientes de fontes que não sejam
    confiáveis que gerem comandos para o sistema operacional

## Autenticação e Gerenciamento de Credenciais

- [ ]   Requerer autenticação para todas as páginas e recursos, exceto para
    aqueles que são intencionalmente públicos

- [ ]   Os controles de autenticação devem ser executados em um sistema
    confiável, por exemplo, centralizar todo o processo no servidor

- [ ]   Sempre que possível, estabelecer e utilizar serviços de autenticação
    padronizados e testados

- [ ]   Utilizar uma implementação centralizada para realizar os
    procedimentos de autenticação, disponibilizando bibliotecas que
    invoquem os serviços externos de autenticação

- [ ]   Separar a lógica de autenticação do recurso que está a ser
    requisitado e usar redirecionadores dos controladores de
    autenticação centralizados

- [ ]   Quando ocorrerem situações excepcionais nos controles de
    autenticação, executar procedimentos em caso de falha com o
    propósito de manter o sistema seguro

- [ ]   Todas as funções administrativas e de gerenciamento de contas devem
    ser tão seguras quanto o mecanismo de autenticação principal

- [ ]   Se a aplicação gerenciar um repositório de credenciais, esta deverá
    garantir que as senhas são armazenadas na base de dados somente sob
    a forma de resumo/*hash* da senha na forma de *one-way salted
    hashes*[^303] e que a tabela/arquivo que armazena as
    senhas e as próprias chaves são manipuladas apenas pela aplicação.
    Não utilizar o algoritmo de hash MD5, sempre que esse puder ser
    evitado

- [ ]   A geração dos resumos (*hash*) das senhas deve ser executada em um
    sistema confiável, por exemplo, centralizar o controle no servidor

- [ ]   Validar os dados de autenticação somente no final de todas as
    entradas de dados, especialmente para as implementações de
    *autenticação sequencial*

- [ ]   As mensagens de falha na autenticação não devem indicar
    qual parte dos dados de autenticação está
    incorreta. Por exemplo, em vez de exibir mensagens como "Nome de usuário
    incorreto" ou "Senha incorreta", utilize apenas mensagens como: "Usuário
    e/ou senha inválidos", para ambos os casos de erro. As respostas de erro
    devem ser idênticas nos dois casos

- [ ]   Utilizar autenticação para conexão a sistemas externos que envolvam
    tráfego de informação sensível ou acesso a funções

- [ ]   As credenciais de autenticação para acessar serviços externos à
    aplicação devem ser cifradas e armazenadas em um local protegido de
    um sistema confiável, por exemplo, no servidor da aplicação. Obs.: o
    código-fonte não é considerado um local seguro

- [ ]   Utilizar apenas requisições POST para transmitir credenciais de
    autenticação

- [ ]   Somente trafegar senhas (não temporárias) através de uma conexão
    protegida (SSL/TLS) ou no formato de dado cifrado, como no caso de
    envio de e-mail cifrado. Senhas temporárias enviadas por e-mail
    podem ser um caso de exceção aceitável

- [ ]   Exigir que os requisitos de complexidade de senha estabelecidos pela
    política ou regulamento sejam cumpridos. As credenciais de
    autenticação devem resistir a ataques que, tipicamente, ameaçam o
    ambiente de produção. Um exemplo pode ser a exigência do uso
    simultâneo de caracteres alfabéticos, numérico e/ou caracteres
    especiais

- [ ]   Exigir que os requisitos de comprimento de senha estabelecidos pela
    política ou regulamento sejam cumpridos. O uso de oito caracteres é
    o mais comum, porém usar 16 é mais recomendado. Considere, ainda, o
    uso de senhas que contenham várias palavras (uma frase)

- [ ]   A entrada da senha deve ser ocultada na tela do usuário. Em HTML,
    utilizar o campo do tipo \"password\"

- [ ]   Desativar a conta após um número pré-definido de tentativas
    inválidas de autenticação (ex: cinco tentativas é o mais comum). A
    conta deve ser desativada por um período de tempo suficientemente
    longo para desencorajar a dedução das credenciais pelo método de
    força bruta, mas não tão longo ao ponto de permitir um ataque de
    negação de serviço

- [ ]   Os processos de redefinição de senhas e operações de mudanças devem
    exigir os mesmos níveis de controle previstos para a criação de
    contas e autenticação

- [ ]   Esquemas de pergunta/resposta (pré-definidas) usadas para a
    redefinição da senha devem evitar ataques que lancem respostas
    aleatórias. Por exemplo, "livro favorito" é uma questão fraca, pois
    "A Bíblia" é uma resposta muito comum

- [ ]   Se optar por usar redefinição de senha baseada em e-mail, envie um
    e-mail somente para o endereço pré-definido contendo um *link* ou
    senha de acesso temporário que permitam ao usuário redefinir a senha

- [ ]   O tempo de validade das senhas e dos *links* temporários deve ser
    curto

- [ ]   Exigir a mudança de senhas temporárias na próxima vez que o usuário
    realizar a autenticação no sistema

- [ ]   Notificar o usuário quando a senha for reiniciada (*reset*)

- [ ]   Prevenir a reutilização de senhas

- [ ]   As senhas devem ter, pelo menos, um dia de duração antes de poderem
    ser alteradas, a fim de evitar ataques de reutilização de senhas

- [ ]   Garantir que a troca de senhas está em conformidade com os
    requisitos estabelecidos na política ou regulamento. Sistemas
    críticos podem exigir alterações mais frequentes nas credenciais de
    segurança. O tempo entre as trocas de senhas deve ser controlado
    administrativamente

- [ ]   Desativar a funcionalidade de lembrar a senha nos campos de senha do
    navegador

- [ ]   A data/hora da última utilização (bem ou mal sucedida) de uma conta
    de usuário deve ser comunicada no próximo acesso ao sistema

- [ ]   Realizar monitoramento para identificar ataques contra várias contas
    de usuários, utilizando a mesma senha. Esse padrão de ataque é
    utilizado para explorar o uso de senhas padrão

- [ ]   Modificar todas as senhas que, por padrão, são definidas pelos
    fornecedores, bem como os identificadores de usuários (IDs) ou
    desativar as contas associadas

- [ ]   Exigir nova autenticação dos usuários antes da realização de
    operações críticas

- [ ]   Utilizar *autenticação de múltiplos fatores* (utilizando
    simultaneamente token, senha, biometria etc.[^304]) para
    contas altamente sensíveis ou de alto valor transacional

- [ ]   Caso utilize código de terceiros para realizar a autenticação,
    inspecione-o cuidadosamente para garantir que o mesmo não é afetado
    por qualquer código malicioso

## Gerenciamento de Sessões

- [ ]   Utilizar controles de gerenciamento de sessão baseados no servidor
    ou em framework. A aplicação deve reconhecer apenas esses
    identificadores de sessão como válidos

- [ ]   A criação dos identificadores de sessão deve ser sempre realizada em
    um sistema confiável, por exemplo, centralizado no servidor

- [ ]   O controle de gestão de sessão deve usar algoritmos conhecidos,
    padronizados e bem testados que garantam a aleatoriedade dos
    identificadores de sessão

- [ ]   Definir o domínio e o caminho para os cookies que contenham
    identificadores de sessão autenticados, para um valor devidamente
    restrito ao site

- [ ]   A funcionalidade de saída (*logout*) deve encerrar completamente a
    sessão ou conexão associada

- [ ]   A funcionalidade de saída (*logout*) deve estar disponível em todas
    as páginas que requerem autenticação

- [ ]   Estabelecer um tempo de expiração da sessão que seja o mais curto
    possível, baseado no balanceamento dos riscos e requisitos
    funcionais do negócio. Na maioria dos casos não deve ser maior do
    que algumas horas

- [ ]   Não permitir logins persistentes (sem prazo de expiração) e realizar
    o encerramento da sessão periodicamente, mesmo quando ela estiver
    ativa. Isso deve ser feito, especialmente, em aplicações que
    suportam várias conexões de rede ou que se conectam a sistemas
    críticos. O tempo de encerramento deve estar de acordo com os
    requisitos do negócio e o usuário deve receber notificações
    suficientes para atenuar os impactos negativos dessa medida

- [ ]   Se uma sessão estava estabelecida antes do login ela deve ser
    encerrada para que uma nova seja estabelecida após o login

- [ ]   Gerar um novo identificador de sessão quando houver uma nova
    autenticação

- [ ]   Não permitir conexões simultâneas com o mesmo identificador de
    usuário

- [ ]   Não expor os identificadores de sessão em URLs, mensagens de erro ou
    logs. Os identificadores de sessão devem apenas ser encontrados no
    cabeçalho do cookie HTTP. Por exemplo, não trafegar os
    identificadores de sessão sob a forma de parâmetros GET

- [ ]   Proteger os dados de sessão do lado servidor contra acessos não
    autorizados por outros usuários do servidor, através da
    implementação de controles de acesso apropriados no servidor

- [ ]   Gerar um novo identificador de sessão e desativar o antigo
    periodicamente. Isso pode mitigar certos cenários de ataques de
    sequestro de sessão (*session hijacking*), quando o identificador de
    sessão original for comprometido

- [ ]   Gerar um novo identificador de sessão caso a segurança da conexão
    mude de HTTP para HTTPS, como pode ocorrer durante a autenticação.
    Internamente à aplicação, é recomendável utilizar HTTPS de forma
    constante em vez de alternar entre HTTP e HTTPS

- [ ]   Utilizar mecanismos complementares ao mecanismo padrão de
    gerenciamento de sessões para operações sensíveis do lado servidor
    -- como no caso de operações de gerenciamento de contas --
    através da utilização de tokens aleatórios ou parâmetros associados à
    sessão. Esse método pode ser usado para prevenir ataques do tipo Cross
    Site Request Forgery (CSRF)

- [ ]   Utilizar mecanismos complementares ao gerenciamento de sessões para
    operações altamente sensíveis ou críticas, utilizando tokens
    aleatórios ou parâmetros em cada requisição em vez de basear-se
    apenas na sessão

- [ ]   Configurar o atributo \"secure\" para cookies transmitidos através
    de uma conexão TLS

- [ ]   Configurar os cookies com o atributo "HttpOnly", a menos que seja
    explicitamente necessário ler ou definir os valores dos mesmos
    através de scripts do lado cliente da aplicação

## Controle de Acessos

- [ ]   Utilizar apenas objetos do sistema que sejam confiáveis, como ocorre
    com os objetos de sessão do servidor, para realizar a tomada de
    decisão sobre a autorização de acesso

- [ ]   Utilizar um único componente em toda a aplicação Web para realizar o
    processo de verificação de autorização de acesso. Isto inclui
    bibliotecas que invocam os serviços externos de autorização

- [ ]   Quando ocorrer alguma falha no controle de acesso, ela deve ocorrer
    de modo seguro

- [ ]   Negar todos os acessos, caso a aplicação não consiga ter acesso às
    informações contidas na configuração de segurança

- [ ]   Garantir o controle de autorização em todas as requisições,
    inclusive em scripts do lado servidor, \"includes\" e requisições
    provenientes de tecnologias do lado cliente, como AJAX e Flash

- [ ]   Isolar do código da aplicação os trechos de código que contêm lógica
    priviligiada

- [ ]   Restringir o acesso aos arquivos e outros recursos, incluindo
    aqueles que estão fora do controle direto da aplicação, somente aos
    usuários autorizados

- [ ]   Restringir o acesso às URLs protegidas somente aos usuários
    autorizados

- [ ]   Restringir o acesso às funções protegidas somente aos usuários
    autorizados

- [ ]   Restringir o acesso às referências diretas aos objetos somente aos
    usuários autorizados

- [ ]   Restringir o acesso aos serviços somente aos usuários autorizados

- [ ]   Restringir o acesso aos dados da aplicação somente aos usuários
    autorizados

- [ ]   Restringir o acesso aos atributos e dados dos usuários, bem como
    informações das políticas usadas pelos mecanismos de controle de
    acesso

- [ ]   Restringir o acesso às configurações de segurança relevantes apenas
    aos usuários autorizados

- [ ]   As regras de controle de acesso representadas pela camada de
    apresentação devem coincidir com as regras presentes no lado
    servidor

- [ ]   Se o *estado dos dados* deve ser armazenado no lado cliente,
    utilizar mecanismos de criptografia e verificação de integridade no
    lado servidor para detectar possíveis adulterações

- [ ]   Garantir que os fluxos lógicos da aplicação obedecem as regras de
    negócio

- [ ]   Limitar o número de transações que um único usuário ou dispositivo
    pode executar em determinado período de tempo. As transações por
    período de tempo devem estar acima das necessidades reais do
    negócio, mas abaixo o suficiente para impedirem ataques
    automatizados

- [ ]   Utilizar o campo "referer" do cabeçalho somente como forma de
    verificação suplementar. O mesmo não deve ser usado sozinho como
    forma de validação de autorização porque ele pode ter o valor
    adulterado

- [ ]   Se for permitida a existência de sessões autenticadas por longos
    períodos de tempo, fazer a revalidação periódica da autorização do
    usuário para garantir que os privilégios não foram modificados e,
    caso tenham sido, realizar o registro em log do usuário e exigir
    nova autenticação

- [ ]   Implementar a auditoria das contas de usuário e assegurar a
    desativação de contas não utilizadas. Por
    exemplo, a conta deve ser desativada não mais do que 30 dias após a
    expiração da senha

- [ ]   A aplicação deve dar suporte à desativação de contas e ao
    encerramento das sessões quando terminar a autorização do usuário.
    Por exemplo, quando ocorrer alguma alteração dos dados do usuário,
    situação profissional, processos de negócio etc.

- [ ]   As contas de serviço ou contas de suporte a conexões provenientes ou
    destinadas a serviços externos devem possuir o menor privilégio
    possível

- [ ]   Criar uma Política de Controle de Acesso para documentar as regras
    de negócio da aplicação, tipos de dados e critérios ou processos de
    autorização para que os acessos possam ser devidamente concedidos e
    controlados. Isto inclui identificar requisitos de acessos, tanto
    para os dados, como para os recursos do sistema

## Práticas de Criptografia

- [ ]   Todas as funções de criptografia utilizadas para proteger dados
    sensíveis dos usuários da aplicação, devem ser implantadas em um
    sistema confiável (neste caso o servidor)

- [ ]   A senha mestre deve ser protegida contra acessos não autorizados

- [ ]   Quando ocorrer alguma falha nos módulos de criptografia, permitir
    que as mesmas ocorram de modo seguro

- [ ]   Todos os números, nomes de arquivos, GUIDs e strings aleatórias
    devem ser gerados usando um módulo criptográfico com gerador de
    números aleatórios, somente se os valores aleatórios gerados forem
    impossíveis de serem deduzidos

- [ ]   Os módulos de criptografia usados pela aplicação devem ser
    compatíveis com a FIPS 140-2 ou com um padrão equivalente
    ([NIST STM group](http://csrc.nist.gov/groups/STM/cmvp/validation.html))

- [ ]   Estabelecer e utilizar uma política e processo que defina como é
    realizado o gerenciamento das chaves criptográficas

## Tratamento de Erros e Log

- [ ]   Não expor informações sensíveis nas repostas de erros, inclusive
    detalhes de sistema, identificadores de sessão ou informação da
    conta do usuário

- [ ]   Usar mecanismos de tratamento de erros que não mostrem informações
    de depuração (*debug*) ou informações da pilha de exceção

- [ ]   Usar mensagens de erro genéricas e páginas de erro personalizadas

- [ ]   A aplicação deve tratar os erros sem se basear nas configurações do
    servidor

- [ ]   A memória alocada deve ser liberada de modo apropriado quando
    ocorrerem condições de erro

- [ ]   O tratamento de erros lógicos associados com os controles de
    segurança devem, por padrão, negar o acesso

- [ ]   Todos os controles de log devem ser implementados em um sistema
    confiável, por exemplo, centralizar todo o processo no servidor

- [ ]   Os controles de log devem dar suporte tanto para os casos de sucesso
    como os de falha relacionados com os eventos de segurança

- [ ]   Garantir que os logs armazenam eventos importantes

- [ ]   Garantir que as entradas de log que incluam dados nos quais não se
    confia não sejam executadas como código-fonte na interface de
    visualização de logs

- [ ]   Restringir o acesso aos logs apenas para pessoal autorizado

- [ ]   Utilizar uma rotina centralizada para realizar todas as operações de
    log

- [ ]   Não armazenar informações sensíveis nos registros de logs, como
    detalhes desnecessários do sistema, identificadores de sessão e
    senhas

- [ ]   Garantir o uso de algum mecanismo que conduza (ou facilite) o
    processo de análise de logs

- [ ]   Registrar em log todas as falhas de validação de entrada de dados

- [ ]   Registrar em log todas as tentativas de autenticação, especialmente
    as que falharam por algum motivo

- [ ]   Registrar em log todas as falhas de controle de acesso

- [ ]   Registrar em log todos os eventos suspeitos de adulteração,
    inclusive alterações inesperadas no estado dos dados

- [ ]   Registrar em log as tentativas de conexão com tokens de sessão
    inválidos ou expirados

- [ ]   Registrar em log todas as exceções lançadas pelo sistema

- [ ]   Registrar em log todas as funções administrativas, inclusive as
    mudanças realizadas nas configurações de segurança

- [ ]   Registrar em log todas as falhas de conexão TLS com o backend

- [ ]   Registrar em log todas as falhas que ocorreram nos módulos de
    criptografia

- [ ]   Utilizar uma função de hash criptográfica para validar a integridade
    dos registros de log

## Proteção de Dados

- [ ]   Implementar uma política de privilégio mínimo, restringindo os
    usuários apenas às funcionalidades, dados e informações do sistema
    que são necessárias para executarem suas tarefas

- [ ]   Proteger contra acesso não autorizado todas as cópias temporárias ou
    registradas em cache que contenham dados sensíveis e estejam
    armazenadas no servidor e excluir esses arquivos logo que não forem
    mais necessários

- [ ]   Criptografar informações altamente sensíveis quando armazenadas --
    como dados de verificação de autenticação -- mesmo que estejam no
    lado servidor, usando sempre algoritmos conhecidos, padronizados e
    bem testados. Consulte a seção que trata sobre "Práticas de
    Criptografia" para orientações adicionais

- [ ]   Proteger o código-fonte presente no servidor para que não sejam
    acessados por algum usuário

- [ ]   Não armazenar senhas, strings de conexão ou outras informações
    confidenciais em texto claro/legível ou em qualquer forma
    criptograficamente insegura no lado cliente. Isso é válido também
    quando há utilização de formatos inseguros como: MS viewstate, Adobe
    Flash ou código compilado que é executado no lado cliente

- [ ]   Remover comentários do código de produção que podem ser acessados
    pelos usuários e podem revelar detalhes internos do sistema ou
    outras informações sensíveis

- [ ]   Remover aplicações desnecessárias e documentação do sistema que
    possam revelar informações importantes para os atacantes

- [ ]   Não incluir informações sensíveis nos parâmetros de requisição HTTP
    GET

- [ ]   Desativar a funcionalidade de auto completar nos formulários que
    contenham informações sensíveis, inclusive no formulário de
    autenticação

- [ ]   Desativar a cache realizada no lado cliente das páginas que
    contenham informações sensíveis. O parâmetro **Cache-Control:
    no-store**, pode ser usado em conjunto com o controle definido no
    cabeçalho HTTP **"Pragma: no-cache"**, que é menos efetivo, porém
    compatível com HTTP/1.0

- [ ]   A aplicação deve dar suporte à remoção de dados sensíveis quando
    estes não forem mais necessários. Por exemplo, informação pessoal ou
    dados financeiros

- [ ]   Implementar mecanismos de controle de acesso apropriados para dados
    sensíveis armazenados no
    servidor. Isto inclui dados em cache, arquivos temporários e dados que
    devem ser acessíveis somente por usuários específicos do sistema

## Segurança nas comunicações

- [ ]   Utilizar criptografia na transmissão de todas as informações
    sensíveis. Isto deve incluir TLS para proteger a conexão e deve ser
    complementado com criptografia de arquivos que contém dados
    sensíveis ou conexões que não usam o protocolo HTTP

- [ ]   Os certificados TLS devem ser válidos, possuírem o nome de domínio
    correto, não estarem expirados e serem instalados com certificados
    intermediários, quando necessário

- [ ]   Quando ocorrer alguma falha nas conexões TLS, o sistema não deve
    fornecer uma conexão insegura

- [ ]   Utilizar conexões TLS para todo o conteúdo que requerer acesso
    autenticado ou que contenha informação sensível

- [ ]   Utilizar TLS para conexões com sistemas externos que envolvam
    funções ou informações sensíveis

- [ ]   Utilizar um padrão único de implementação TLS configurado de modo
    apropriado

- [ ]   Especificar a codificação dos caracteres para todas as conexões

- [ ]   Filtrar os parâmetros que contenham informações sensíveis,
    provenientes do "HTTP referer", nos links para sites externos

## Configuração do Sistema

- [ ]   Garantir que os servidores, frameworks e componentes do sistema
    estão executando a última versão aprovada

- [ ]   Garantir que os servidores, frameworks e componentes do sistema
    possuem as atualizações mais recentes aplicadas para a versão em uso

- [ ]   Desativar a listagem de diretórios

- [ ]   Restringir, para o mínimo possível, os privilégios do servidor Web,
    dos processos e das contas de serviços

- [ ]   Quando ocorrerem exceções no sistema, garantir que as falhas ocorram
    de modo seguro

- [ ]   Remover todas as funcionalidades e arquivos desnecessários

- [ ]   Remover código de teste ou qualquer funcionalidade desnecessária
    para o ambiente de produção, antes de instalar o sistema no servidor
    de produção

- [ ]   Prevenir a divulgação da estrutura de diretórios impedindo que
    robôs[^305] de busca façam indexação de arquivos
    sensíveis, através da configuração do arquivo
    "robots.txt"[^306]. Os diretórios que não devem ser
    acessados por estes indexadores devem ser colocados em um diretório
    isolado. Assim, apenas é necessário negar o acesso ao diretório pai
    definido no arquivo "robots.txt", evitando ter que negar o acesso a
    cada diretório individualmente

- [ ]   Definir quais métodos HTTP, GET ou POST, a aplicação irá suportar e
    se serão tratados de modo diferenciado nas diversas páginas da
    aplicação

- [ ]   Desativar as extensões HTTP desnecessárias como, por exemplo, o
    WebDAV. Caso seja necessário o uso de alguma extensão HTTP com o
    propósito de suportar a manipulação de arquivos, utilize um
    mecanismo de autenticação conhecido, padronizado e bem testado

- [ ]   Se o servidor processa tanto requisições HTTP 1.0 como HTTP 1.1,
    certificar-se de que ambos são configurados de modo semelhante ou
    assegure que qualquer diferença existente seja compreendida, como,
    por exemplo, o manuseio de métodos HTTP estendidos

- [ ]   Remover informações desnecessárias presentes nos cabeçalhos de
    resposta HTTP e que podem estar relacionadas com o sistema
    operacional, versão do servidor web e frameworks de aplicação

- [ ]   O armazenamento da configuração de segurança para a aplicação deve
    ser capaz de ser produzida de forma legível para dar suporte à
    auditoria

- [ ]   Implementar um sistema de gestão de ativos para manter o registro
    dos componentes e programas

- [ ]   Isolar o ambiente de desenvolvimento da rede de produção e conceder
    acesso somente para grupos de desenvolvimento e testes. É comum os
    ambientes de desenvolvimento serem configurados de modo menos seguro
    do que os ambientes de produção. Deste modo, os atacantes podem usar
    essa diferença para descobrir vulnerabilidades comuns ou encontrar
    formas de exploração das mesmas

- [ ]   Implementar um sistema de controle de mudanças para gerenciar e
    registrar as alterações no código, tanto de desenvolvimento, como
    dos sistemas em produção

## Segurança em Banco de Dados

- [ ]   Usar *consultas parametrizadas* fortemente tipadas

- [ ]   Utilizar validação de entrada e codificação de saída e assegurar a
    abordagem de meta caracteres. Se houver falha, o comando não deverá
    ser executado no banco de dados

- [ ]   Certificar-se de que as variáveis são fortemente tipadas

- [ ]   Realizar a codificação (escaping) de meta caracteres em instruções
    SQL[^307]

- [ ]   A aplicação deve usar o menor nível possível de privilégios ao
    acessar o banco de dados

- [ ]   Usar credenciais seguras para acessar o banco de dados

- [ ]   Não incluir strings de conexão na aplicação. As strings de conexão
    devem estar em um arquivo de configuração separado, armazenado em um
    sistema confiável e as informações devem ser criptografadas

- [ ]   Usar procedimentos armazenados (*stored procedures*) para abstrair o
    acesso aos dados e permitir a remoção de permissões das tabelas no
    banco de dados

- [ ]   Encerrar a conexão assim que possível

- [ ]   Remover ou modificar senhas padrão de contas administrativas.
    Utilizar senhas robustas (pouco comuns ou difíceis de deduzir) ou
    implementar autenticação de múltiplos fatores. Desativar qualquer
    funcionalidade desnecessária no banco de dados, como "stored
    procedures" ou serviços não utilizados. Instalar o conjunto mínimo
    de componentes ou de opções necessárias (redução da superfície de
    ataque)

- [ ]   Eliminar o conteúdo desnecessário incluído por padrão pelo
    fornecedor como esquemas e bancos de dados de exemplo

- [ ]   Desativar todas as contas criadas por padrão e que não sejam
    necessárias para suportar os requisitos de negócio

- [ ]   A aplicação deve conectar-se ao banco de dados com diferentes
    credenciais de segurança para cada tipo de necessidade como, por
    exemplo, usuário, somente leitura, convidado ou administrador

## Gerenciamento de Arquivos

- [ ]   Não repassar dados fornecidos pelos usuários diretamente a uma
    função de inclusão dinâmica

- [ ]   Solicitar autenticação antes de permitir que seja feito o
    carregamento de arquivos

- [ ]   Limitar os tipos de arquivos que podem ser enviados para aceitar
    somente os necessários ao propósito do negócio

- [ ]   Validar se os arquivos enviados são do tipo esperado, através da
    validação dos cabeçalhos, pois, realizar a verificação apenas pela
    extensão não é suficiente

- [ ]   Não salvar arquivos no mesmo diretório de contexto da aplicação Web.
    Os arquivos devem ser armazenados no servidor de conteúdos ou no
    banco de dados

- [ ]   Prevenir ou restringir o carregamento de qualquer arquivo que possa
    ser interpretado ou executado pelo servidor Web

- [ ]   Desativar privilégios de execução nos diretórios de armazenamento de
    arquivos

- [ ]   Implantar o carregamento seguro nos ambientes UNIX por meio da
    montagem do diretório de destino como uma unidade lógica, usando o
    caminho associado ou o ambiente de "chroot"

- [ ]   Ao referenciar arquivos, usar uma lista branca (*whitelist*) de
    nomes e de tipos de arquivos permitidos. Realizar a validação do
    valor do parâmetro passado e caso ele não corresponda ao que é
    esperado, rejeitar a entrada ou utilizar um valor padrão

- [ ]   Não transmitir, sem nenhum tipo de tratamento, os dados informados
    pelo usuário a redirecionamentos dinâmicos. Se isso for necessário,
    o redirecionamento deverá aceitar apenas URLs relativas e validadas

- [ ]   Não passar caminhos de diretórios ou de arquivos em requisições.
    Usar algum mecanismo de mapeamento desses recursos para índices
    definidos em uma lista pré-definida de caminhos

- [ ]   Nunca enviar o caminho absoluto do arquivo para o lado cliente de
    uma aplicação ou para o usuário

- [ ]   Certificar-se de que os arquivos da aplicação e os recursos estão
    definidos somente com o atributo de leitura

- [ ]   Verificar os arquivos que os usuários submeterem através do
    mecanismo de carregamento em busca de vírus e malwares

## Gerenciamento de Memória

- [ ]   Utilizar controle de entrada/saída para os dados que não sejam
    confiáveis

- [ ]   Verificar se o buffer é tão grande quanto o especificado

- [ ]   Ao usar funções que aceitem determinado número de bytes para
    realizar cópias, como strncpy(), esteja ciente de que se o tamanho
    do buffer de destino for igual ao tamanho do buffer de origem, ele
    não pode encerrar a sequência de caracteres com valor nulo (null)

- [ ]   Verificar os limites do buffer caso as chamadas à função sejam
    realizadas em ciclos e verificar se não há nenhum risco de ocorrer
    gravação de dados além do espaço reservado

- [ ]   Truncar todas as strings de entrada para um tamanho razoável antes
    de passá-las para as funções de cópia e concatenação

- [ ]   Na liberação de recursos alocados para objetos de conexão,
    identificadores de arquivo etc., não contar com o "*garbage
    collector*" e realizar a tarefa explicitamente

- [ ]   Usar pilhas não executáveis, quando disponíveis

- [ ]   Evitar o uso de funções reconhecidamente vulneráveis como printf(),
    strcat(), strcpy() etc.

- [ ]   Liberar a memória alocada de modo apropriado após concluir a
    sub-rotina (função/método) e em todos pontos de saída

## Práticas Gerais de Codificação

- [ ]   Para tarefas comuns, utilizar sempre código testado, gerenciado e
    aprovado ao invés de criar código novo e não gerenciado

- [ ]   Utilizar APIs que executem tarefas específicas para realizar
    operações do sistema operacional. Não permitir que a aplicação
    execute comandos diretamente no sistema operacional, especialmente
    através da utilização de "shells" de comando iniciadas pela
    aplicação

- [ ]   Utilizar mecanismos de verificação de integridade por "checksum" ou
    "hash" para verificar a integridade do código interpretado,
    bibliotecas, arquivos executáveis e arquivos de configuração

- [ ]   Utilizar mecanismos de bloqueio para evitar requisições simultâneas
    para a aplicação ou utilizar um mecanismo de sincronização para
    evitar condições de concorrência (*race conditions*)

- [ ]   Proteger as variáveis compartilhadas e os recursos contra acessos
    concorrentes inapropriados

- [ ]   Instanciar explicitamente todas as variáveis e dados persistentes
    durante a declaração, ou antes da primeira utilização

- [ ]   Quando a aplicação tiver que ser executada com privilégios elevados,
    aumentar os privilégios o mais tarde possível e revogá-los logo que
    seja possível

- [ ]   Evitar erros de cálculo decorrentes da falta de entendimento da
    representação interna da linguagem de programação usada e de como é
    realizada a interação com os aspectos de cálculo numérico. Prestar
    bastante atenção nas discrepâncias de tamanho de byte, precisão,
    distinções de sinal (signed/unsigned), truncamento, conversão e
    "casting" entre os tipos, cálculos que devolvam erros do tipo
    "not-a-number" e, também, como a linguagem de programação trata a
    representação interna de números muito grandes ou muito pequenos

- [ ]   Não transferir, diretamente, dados fornecidos pelo usuário para
    qualquer função de execução dinâmica sem realizar o *tratamento dos
    dados* de modo adequado

- [ ]   Restringir a geração e a alteração de código por parte dos usuários

- [ ]   Revisar todas as aplicações secundárias, códigos e bibliotecas de
    terceiros para determinar a necessidade do negócio e validar as
    funcionalidades de segurança, uma vez que estas podem introduzir
    novas vulnerabilidades

- [ ]   Implementar atualizações de modo seguro. Se a aplicação precisar
    realizar atualizações automáticas, utilizar mecanismos de assinatura
    digital para garantir a integridade do código e garantir que os
    clientes façam a verificação da assinatura após descarregarem as
    atualizações. Usar canais criptografados para transferir o código a
    partir do host do servidor
