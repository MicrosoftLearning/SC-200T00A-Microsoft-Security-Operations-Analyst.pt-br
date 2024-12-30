---
lab:
  title: 'Exercício 1: criar consultas para o Microsoft Sentinel usando a Linguagem de consulta Kusto (KQL)'
  module: Learning Path 6 - Create queries for Microsoft Sentinel using Kusto Query Language (KQL)
---

# Roteiro de aprendizagem 6 — Laboratório 1 — Exercício 1 — Criar consultas para o Microsoft Sentinel usando a Linguagem de consulta Kusto (KQL)

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod4_L1_Ex1.png)

Você trabalha como analista de operações de segurança em uma empresa que está implementando o Microsoft Sentinel. É responsável por executar a análise de dados de log para procurar atividades mal-intencionadas, exibir visualizações e realizar a busca de ameaças. Para consultar os dados do log, você usa a KQL (Linguagem de Consulta Kusto).

>**Importante:** este laboratório envolve a inserção de muitos scripts KQL no Microsoft Sentinel. Os scripts foram fornecidos em um arquivo no início deste laboratório. Um local alternativo para baixá-los é: <https://github.com/MicrosoftLearning/SC-200T00A-Microsoft-Security-Operations-Analyst/tree/master/Allfiles>

### Tempo estimado para concluir este laboratório: 60 minutos

### Tarefa 1: acessar a área de teste da KQL

Nesta tarefa, você acessará um ambiente do Log Analytics onde poderá praticar a escrita de instruções KQL.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Microsoft Edge, acesse <https://aka.ms/lademo> e faça logon com as credenciais de administrador.

1. Feche a janela pop-up de vídeo do Log Analytics que aparece.

1. Explore as tabelas disponíveis e outras ferramentas listadas no *painel de esquema e filtro* no lado esquerdo da tela.

1. No editor de consultas, insira a consulta a seguir e clique no botão **Executar**. Você deve ver os resultados da consulta na janela inferior.

    ```KQL
    SecurityEvent
    ```

1. Observe que você atingiu o número máximo de resultados (30.000).

1. Altere o *Intervalo de tempo* para **Últimos 30 minutos** na janela Consulta.

1. Ao lado do primeiro registro, selecione o **>** para expandir as informações da linha.


### Tarefa 2: executar instruções básicas do KQL

Nesta tarefa, você compilará instruções básicas do KQL.

>**Importante:** Para cada consulta, limpe a instrução anterior da janela Consulta ou abra uma nova janela Consulta selecionando **+** após a última guia aberta (até 25).

1. A instrução a seguir demonstra o operador de **pesquisa**, que pesquisa o valor em todas as colunas da tabela.

1. Altere o *Intervalo de tempo* para **Últimos 30 minutos** na janela Consulta.

1. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    search "location"
    ```

    >**Observação:** Usar o operador *Pesquisa* sem tabelas específicas ou cláusulas de qualificação é menos eficiente do que a filtragem de texto específica à tabela e à coluna.

1. A instrução a seguir demonstra a **pesquisa** entre tabelas listadas na cláusula **in**. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    search in (SecurityEvent,App*) "new"
    ```

1. Altere novamente o *Intervalo de tempo* para **Últimas 24 horas** na janela Consulta.

1. As instruções a seguir demonstram o operador **where**, que filtra em um predicado específico. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    >**Importante:** você deve selecionar **Executar** depois de inserir cada consulta nos blocos de código abaixo.

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    ```

    >**Observação:** o *intervalo de tempo* agora mostra *Definir na consulta*, pois estamos filtrando com a coluna TimeGenerated.

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) and EventID == 4624
    ```

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | where EventID == 4624  
    | where AccountType =~ "user"
    ```

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) and EventID in (4624, 4625)
 
    ```

1. A instrução a seguir demonstra o uso da instrução **let** para declarar *variáveis*. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    let timeOffset = 1h;
    let discardEventId = 4688;
    SecurityEvent
    | where TimeGenerated > ago(timeOffset*2) and TimeGenerated < ago(timeOffset)
    | where EventID != discardEventId
    ```

1. A instrução a seguir demonstra o uso da instrução **let** para declarar uma *lista dinâmica*. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    let suspiciousAccounts = datatable(account: string) [
      @"NA\timadmin", 
      @"NT AUTHORITY\SYSTEM"
    ];
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | where Account in (suspiciousAccounts)
    ```

    >**Dica:** você pode reformatar a consulta facilmente selecionando as reticências (...) na janela Consulta e depois selecionando **Formatar consulta**.

1. A instrução a seguir demonstra o uso da instrução **let** para declarar uma *tabela dinâmica*. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    let LowActivityAccounts =
        SecurityEvent 
        | summarize cnt = count() by Account 
        | where cnt < 1000;
    LowActivityAccounts | where Account contains "sql"
    ```

1. Altere o **Intervalo de tempo** para **Última hora** na janela Consulta. Isso limitará nossos resultados para as instruções a seguir.

1. A instrução a seguir demonstra o operador **extend**, que cria uma coluna calculada e a adiciona ao conjunto de resultados. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))
    ```

1. A instrução a seguir demonstra o operador **order by**, que classifica as linhas da tabela de entrada por uma ou mais colunas em ordem crescente ou decrescente. O operador **order by** é um alias para o operador **sort by**. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) 
    | order by StartDir desc, Process asc
    ```

1. As instruções a seguir demonstram o operador **project**, que seleciona as colunas a serem incluídas na ordem especificada. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) 
    | order by StartDir desc, Process asc 
    | project Process, StartDir
    ```

1. As instruções a seguir demonstram o operador **project-away**, que seleciona as colunas a serem excluídas da saída. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) 
    | order by StartDir desc, Process asc 
    | project-away ProcessName
    ```

### Tarefa 3: analisar resultados no KQL com o operador summarize

Nesta tarefa, você compilará instruções KQL para agregar dados. **Summarize** agrupa as linhas de acordo com as colunas do grupo **by** e calcula as agregações em cada grupo.

1. A instrução a seguir demonstra a função **count()**, que retorna uma contagem do grupo. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) and EventID == 4688  
    | summarize count() by Process, Computer
    ```

1. A instrução a seguir demonstra a função **count()**, mas, neste exemplo, nomeamos a coluna como *cnt*. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h) and EventID == 4624  
    | summarize cnt=count() by AccountType, Computer
    ```

1. A instrução a seguir demonstra a função **dcount()**, que retorna uma contagem distinta aproximada dos elementos do grupo. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | summarize dcount(IpAddress)
    ```

1. A instrução a seguir é uma regra para detectar falhas de senha inválida em vários aplicativos para a mesma conta. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    let timeframe = 30d;
    let threshold = 1;
    SigninLogs
    | where TimeGenerated >= ago(timeframe)
    | where ResultDescription has "Invalid password"
    | summarize applicationCount = dcount(AppDisplayName) by UserPrincipalName, IPAddress
    | where applicationCount >= threshold
    ```

1. A instrução a seguir demonstra a função **arg_max()**, que retorna uma ou mais expressões quando o argumento é maximizado. A instrução a seguir retornará a linha mais atual da tabela SecurityEvent para o computador SQL10.NA.contosohotels.com. O * na função arg_max solicita todas as colunas da linha. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where Computer == "SQL10.na.contosohotels.com"
    | summarize arg_max(TimeGenerated,*) by Computer
    ```

1. A instrução a seguir demonstra a função **arg_min()**, que retorna uma ou mais expressões quando o argumento é minimizado. Nesta instrução, o SecurityEvent mais antigo para o computador SQL10.NA.contosohotels.com será retornado como o conjunto de resultados. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where Computer == "SQL10.na.contosohotels.com"
    | summarize arg_min(TimeGenerated,*) by Computer
    ```

1. As instruções a seguir demonstram a importância de compreender os resultados com base na ordem do *pipe*. Na janela Consulta, insira as seguintes consultas e execute cada uma delas separadamente: 

    1. A **Consulta 1** terá contas para as quais a última atividade foi um logon. A tabela SecurityEvent será primeiro resumida e retornará a linha mais atual para cada Conta. Então, apenas as linhas com EventID igual a 4624 (logon) serão retornadas.

        ```KQL
        SecurityEvent  
        | summarize arg_max(TimeGenerated, *) by Account 
        | where EventID == 4624  
        ```

    1. A **Consulta 2** terá o logon mais recente para as Contas que fizeram logon. A tabela SecurityEvent será filtrada para incluir somente EventID = 4624. Em seguida, esses resultados serão resumidos para a linha de logon mais atual por Conta.

        ```KQL
        SecurityEvent  
        | where EventID == 4624  
        | summarize arg_max(TimeGenerated, *) by Account
        ```

    >**Observação:** você também pode revisar a "CPU total" e os "Dados usados para a consulta processada" selecionando o link "Detalhes da consulta" no canto inferior direito e comparar os dados entre ambas as instruções.

1. A instrução a seguir demonstra a função **make_list()**, que retorna uma *lista* de todos os valores dentro do grupo. Essa consulta KQL primeiro filtrará o EventID com o operador where. Em seguida, para cada Computador, os resultados são uma matriz JSON de Contas. A matriz JSON resultante incluirá contas duplicadas. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | where EventID == 4624  
    | summarize make_list(Account) by Computer
    ```

1. A instrução a seguir demonstra a função **make_set()**, que retorna um conjunto de valores *distintos* dentro do grupo. Essa consulta KQL primeiro filtrará o EventID com o operador where. Em seguida, para cada Computador, os resultados são uma matriz JSON de Contas exclusivas. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | where EventID == 4624  
    | summarize make_set(Account) by Computer
    ```


### Tarefa 4: criar visualizações em KQL com o operador render

Nesta tarefa, você usará a geração de visualizações com instruções KQL.

1. A instrução a seguir demonstra o operador **render** (que renderiza os resultados como uma saída gráfica), usando uma visualização de **gráfico de barras**. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | summarize count() by Account
    | render barchart
    ```

1. A instrução a seguir demonstra o operador **render** visualizando resultados com uma série temporal. A função **bin()** arredonda todos os valores em um período de tempo e os agrupa, sendo usada com frequência em combinação com **summarize**. Se você tiver um conjunto disperso de valores, os valores serão agrupados em um conjunto menor de valores específicos. Combinar os resultados gerados e canalizá-los para um operador **render** com um **gráfico de tempo** fornece uma visualização de série temporal. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where TimeGenerated > ago(1h)
    | summarize count() by bin(TimeGenerated, 1m)
    | render timechart
    ```


### Tarefa 5: compilar instruções de várias tabelas em KQL

Nesta tarefa, você compilará instruções de várias tabelas em KQL.

1. Altere o **Intervalo de tempo** para **Última hora** na janela Consulta. Isso limitará nossos resultados para as instruções a seguir.

1. A instrução a seguir demonstra o operador **union**, que pega duas ou mais tabelas e retorna todas as suas linhas. É essencial compreender como os resultados passam e sofrem impacto pelo caractere pipe. Na janela Consulta, insira as seguintes instruções e selecione **Executar** para cada consulta separadamente para ver os resultados: 

    1. A **Consulta 1** retornará todas as linhas do SecurityEvent e todas as linhas do SigninLogs.

        ```KQL
        SecurityEvent  
        | union SigninLogs  
        ```

    1. A **Consulta 2** retornará uma linha e uma coluna, que é a contagem de todas as linhas do SecurityEvent e todas as linhas do SigninLogs.

        ```KQL
        SecurityEvent  
        | union SigninLogs  
        | summarize count() 
        ```

    1. A **Consulta 3** retornará todas as linhas do SecurityEvent e uma (última) linha do SigninLogs. A última linha de SigninLogs terá a contagem resumida do número total de linhas.

        ```KQL
        SecurityEvent  
        | union (SigninLogs | summarize count() | project count_)
        ```

    >**Observação:** a "linha vazia" nos resultados mostrará a contagem resumida de SigninLogs.

1. A instrução a seguir demonstra o suporte do operador **union** para unir várias tabelas com curingas. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    union App*  
    | summarize count() by Type
    ```

1. A instrução a seguir demonstra o operador **join**, que mescla as linhas de duas tabelas para formar uma nova tabela, combinando os valores das colunas especificadas de cada tabela. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where EventID == 4624 
    | summarize LogOnCount=count() by  EventID, Account
    | project LogOnCount, Account
    | join kind = inner( 
     SecurityEvent  
    | where EventID == 4634 
    | summarize LogOffCount=count() by  EventID, Account
    | project LogOffCount, Account
    ) on Account
    ```

    >**Importante:** a primeira tabela especificada no operador join é a tabela esquerda. A tabela depois do operador **join** é a tabela direita. Ao trabalhar com colunas das tabelas, o nome $left.Column e o nome $right.Column servem para distinguir quais colunas das tabelas são referenciadas. O operador **join** dá suporte a uma gama completa de tipos: flouter, inner, innerunique, leftanti, leftantisemi, leftouter, leftsemi, rightanti, rightantisemi, rightouter, rightsemi.

1. Altere novamente o **Intervalo de tempo** para **Últimas 24 horas** na janela Consulta.

### Tarefa 6: trabalhar com dados de cadeia de caracteres em KQL

Nesta tarefa, você trabalhará com campos de cadeia de caracteres estruturados e não estruturados com instruções KQL.

1. A instrução a seguir demonstra a função **extract**, que obtém uma correspondência para uma expressão regular de uma cadeia de caracteres de fonte. Você tem a opção de converter a substring extraída para o tipo indicado. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    print extract("x=([0-9.]+)", 1, "hello x=45.6|wo") == "45.6"
    ```

1. As instruções a seguir usam a função **extract** para extrair o nome da conta do campo Conta da tabela SecurityEvent. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent  
    | where EventID == 4672 and AccountType == 'User' 
    | extend Account_Name = extract(@"^(.*\\)?([^@]*)(@.*)?$", 2, tolower(Account))
    | summarize LoginCount = count() by Account_Name
    | where Account_Name != "" 
    | where LoginCount < 10
    ```

1. A instrução a seguir demonstra o operador **parse**, que avalia uma expressão de cadeia de caracteres e analisa o valor dela em uma ou mais colunas calculadas. Use para estruturar dados não estruturados. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    let Traces = datatable(EventText:string)
    [
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=23, lockTime=02/17/2016 08:40:01, releaseTime=02/17/2016 08:40:01, previousLockTime=02/17/2016 08:39:01)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=15, lockTime=02/17/2016 08:40:00, releaseTime=02/17/2016 08:40:00, previousLockTime=02/17/2016 08:39:00)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=20, lockTime=02/17/2016 08:40:01, releaseTime=02/17/2016 08:40:01, previousLockTime=02/17/2016 08:39:01)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=22, lockTime=02/17/2016 08:41:01, releaseTime=02/17/2016 08:41:00, previousLockTime=02/17/2016 08:40:01)",
    "Event: NotifySliceRelease (resourceName=PipelineScheduler, totalSlices=27, sliceNumber=16, lockTime=02/17/2016 08:41:00, releaseTime=02/17/2016 08:41:00, previousLockTime=02/17/2016 08:40:00)"
    ];
    Traces   
    | parse EventText with * "resourceName=" resourceName ", totalSlices=" totalSlices:long * "sliceNumber=" sliceNumber:long * "lockTime=" lockTime ", releaseTime=" releaseTime:date "," * "previousLockTime=" previousLockTime:date ")" *  
    | project resourceName, totalSlices, sliceNumber, lockTime, releaseTime, previousLockTime
    ```

>**Importante:** as consultas a seguir não produzem resultados no ambiente lademo usado para este laboratório. As entradas na tabela *SigninLogs* foram removidas. No entanto, as consultas KQL demonstram conceitos e casos de uso importantes, portanto, reserve um tempo para revisá-los.

1. A instrução a seguir demonstra o trabalho com campos **dinâmicos**, que são especiais, pois podem assumir qualquer valor de outros tipos de dados. Neste exemplo, o campo DeviceDetail da tabela SigninLogs é do tipo **dinâmico**. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SigninLogs 
    | extend OS = DeviceDetail.operatingSystem
    ```

1. O exemplo a seguir mostra como separar campos compactados para SigninLogs. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    SigninLogs 
    | extend OS = DeviceDetail.operatingSystem, Browser = DeviceDetail.browser 
    | extend StatusCode = tostring(Status.errorCode), StatusDetails = tostring(Status.additionalDetails) 
    | extend Date = startofday(TimeGenerated) 
    | summarize count() by Date, Identity, UserDisplayName, UserPrincipalName, IPAddress, ResultType, ResultDescription, StatusCode, StatusDetails 
    | sort by Date
    ```

    >**Importante:** embora o tipo dinâmico pareça semelhante ao JSON, ele pode conter valores que o modelo JSON não representa porque não existem no JSON. Portanto, ao serializar valores dinâmicos em uma representação de JSON, os valores que o JSON não pode representar são serializados em valores de cadeia de caracteres. 

1. As instruções a seguir demonstram os operadores para manipular o JSON armazenado em campos de cadeia de caracteres. Muitos logs enviam dados no formato JSON, o que exige que você saiba como transformar dados JSON em campos que possam ser consultados. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SigninLogs 
    | extend AuthDetails =  parse_json(AuthenticationDetails) 
    | extend AuthMethod =  AuthDetails[0].authenticationMethod 
    | extend AuthResult = AuthDetails[0].["authenticationStepResultDetail"] 
    | project AuthMethod, AuthResult, AuthDetails 
    ```

1. A instrução a seguir demonstra o operador **mv-expand**, que transforma matrizes dinâmicas em linhas (expansão de vários valores).

    ```KQL
    SigninLogs 
    | mv-expand AuthDetails = parse_json(AuthenticationDetails) 
    | project AuthDetails
    ```

1. Expanda a primeira linha selecionando ">" e, em seguida, expanda novamente ao lado de *AuthDetails* para revisar os resultados expandidos.

1. A instrução a seguir demonstra o operador **mv-apply**, que aplica uma subconsulta a cada registro e retorna a união dos resultados de todas as subconsultas.

    ```KQL
    SigninLogs 
    | mv-apply AuthDetails = parse_json(AuthenticationDetails) on
    (where AuthDetails.authenticationMethod == "Password")
    ```

1. Uma **função** é uma consulta de log que pode ser usada em outras consultas de log com o nome salvo como um comando. Para criar uma **função**, depois de executar sua consulta, clique no botão **Salvar** e, em seguida, selecione **Salvar como função** no menu suspenso. Insira o nome desejado (por exemplo: *PrivLogins*) na caixa **Nome da função**, insira uma **Categoria herdada** (por exemplo: *Geral*) e selecione **Salvar**. A função estará disponível no KQL usando o alias da função:

    >**Observação:** você não poderá fazer isso no ambiente do lademo usado neste laboratório, pois sua conta tem apenas permissões de leitor, mas esse é um conceito importante para tornar suas consultas mais eficientes e eficazes. 

    ```KQL
    PrivLogins  
    ```

## Você concluiu o laboratório.
