---
lab:
  title: 'Exercício 1: criar consultas para o Microsoft Sentinel usando a Linguagem de consulta Kusto (KQL)'
  module: Learning Path 6 - Create queries for Microsoft Sentinel using Kusto Query Language (KQL)
---

# Roteiro de aprendizagem 6 — Laboratório 1 — Exercício 1 — Criar consultas para o Microsoft Sentinel usando a Linguagem de consulta Kusto (KQL)

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod4_L1_Ex1.png)

Você trabalha como analista de operações de segurança em uma empresa que está implementando o Microsoft Azure Sentinel. Você é responsável por executar a análise de dados de log para procurar atividades mal intencionadas, exibir visualizações e realizar a busca de ameaças. Para consultar os dados do log, você usa o KQL (Kusto Query Language).

>**Importante:** os exercícios de laboratório para o Roteiro de Aprendizagem nº 6 estão em um ambiente *autônomo*. Se você sair do laboratório antes de concluí-lo, será necessário executar as etapas de configuração novamente.

>**Observação:** esse perfil de laboratório leva >15 minutos para ser totalmente compilado, pois o Microsoft Sentinel está sendo pré-implantado em sua assinatura do Azure com o nome **defenderWorkspace**.

<!--- >**Tip:** This lab involves entering many KQL scripts into Microsoft Sentinel. The scripts were provided in a file at the beginning of this lab. An alternate location to download them is:  <https://github.com/MicrosoftLearning/SC-200T00A-Microsoft-Security-Operations-Analyst/tree/master/Allfiles> --->

### Tempo estimado para concluir este laboratório: 60 minutos

### Tarefa 1: Preparar a área de teste do KQL

Nesta tarefa, você instala a **Solução de Laboratório de Treinamento do Microsoft Sentinel** do Marketplace, que preencherá um workspace do Log Analytics com dados de exemplo que você pode usar para praticar a escrita de instruções KQL.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Microsoft Edge, acesse <https://portal.azure.com> e faça logon com as credenciais atribuídas.

1. Na barra de pesquisa do Azure, digite **Solução de Laboratório de Treinamento do Microsoft Sentinel** e selecione-a nos resultados.

    >**Dica:** ela estará na seção Marketplace.

1. Na página **Solução de Laboratório de Treinamento do Microsoft Sentinel**, selecione **Criar** para instalar a solução.

1. Na página **Criar Solução de Laboratório de Treinamento do Microsoft Sentinel**, selecione o Grupo de Recursos **defender-RG** e o workspace **defenderWorkspace**.

1. Selecione **Examinar + Criar** para implantar a solução.

1. Após a conclusão da validação, escolha **Criar** para implantar a solução.

  >**Observação:** leva aproximadamente dez minutos para que a solução seja totalmente implantada e para que todos os recursos fiquem disponíveis.

1. Aguarde a conclusão da implantação e selecione **Início** na navegação estrutural.

### Tarefa 2: Explorar o workspace do Log Analytics

1. Na barra de pesquisa do portal do Azure, digite **Microsoft Sentinel** e selecione-o nos resultados.

1. Na página do Microsoft Sentinel, selecione o workspace **defenderWorkspace**.

1. No Microsoft Sentinel, expanda a seção **Geral** e selecione **Logs** no menu de navegação.

1. Feche a janela pop-up de vídeo do Log Analytics que aparece.

1. Feche o **Hub de consultas**.

1. Use o menu suspenso para alterar do **Modo simples** para o **Modo KQL**.

1. Explore as tabelas disponíveis e outras ferramentas listadas no *painel de esquema e filtro* no lado esquerdo da tela.

1. No editor de consultas, insira a consulta a seguir e clique no botão **Executar**. Você deve ver os resultados da consulta na janela inferior.

    ```KQL
    SecurityEvent_CL
    ```

    >**Observação:** a tabela *SecurityEvent_CL* é uma tabela personalizada criada pela Solução de Laboratório de Treinamento do Microsoft Sentinel. Ela contém dados de amostra que você pode usar para praticar a escrita de instruções KQL.

1. Observe o filtro definido como **Mostrar: 1000 resultados**.

1. Ao lado do primeiro registro, selecione o **>** para expandir as informações da linha.

### Tarefa 3: Executar instruções KQL básicas

Nesta tarefa, você compilará instruções básicas do KQL.

>**Importante:** Para cada consulta, limpe a instrução anterior da janela Consulta ou abra uma nova janela Consulta selecionando **+** após a última guia aberta (até 25).

1. A instrução a seguir demonstra o operador de **pesquisa**, que pesquisa o valor em todas as colunas da tabela.

1. O *Intervalo de tempo* deve ser, por padrão, **Últimas 24 horas** na janela Consulta.

1. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    search "Computer"
    ```

    >**Observação:** Usar o operador *Pesquisa* sem tabelas específicas ou cláusulas de qualificação é menos eficiente do que a filtragem de texto específica à tabela e à coluna.

1. A instrução a seguir demonstra a **pesquisa** entre tabelas listadas na cláusula **in**. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    search in (SecurityEvent_CL,App*) "new"
    ```

1. Altere novamente o *Intervalo de tempo* para **Últimas 24 horas** na janela Consulta.

1. As instruções a seguir demonstram o operador **where**, que filtra em um predicado específico. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    >**Importante:** você deve selecionar **Executar** depois de inserir cada consulta nos blocos de código abaixo.

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    ```

    >**Observação:** o *intervalo de tempo* agora mostra *Definir na consulta*, pois estamos filtrando com a coluna TimeGenerated.

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) and EventID_s == 4624
    ```

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | where EventID_s == 4624  
    | where AccountType_s =~ "user"
    ```

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) and EventID_s in (4624, 4625)
 
    ```

1. A instrução a seguir demonstra o uso da instrução **let** para declarar *variáveis*. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    let timeOffset = 1h;
    let discardEventID = 4688;
    SecurityEvent_CL
    | where TimeGenerated > ago(timeOffset*2) and TimeGenerated < ago(timeOffset)
    | where EventID_s != discardEventID
    ```

1. A instrução a seguir demonstra o uso da instrução **let** para declarar uma *lista dinâmica*. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    let suspiciousAccounts = datatable(account: string) [
      @"NA\timadmin", 
      @"NT AUTHORITY\SYSTEM"
    ];
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | where Account_s in (suspiciousAccounts)
    ```

    >**Dica:** você pode reformatar a consulta facilmente selecionando as reticências (...) na janela Consulta e depois selecionando **Formatar consulta**.

1. A instrução a seguir demonstra o uso da instrução **let** para declarar uma *tabela dinâmica*. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    let LowActivityAccounts =
        SecurityEvent_CL 
        | summarize cnt = count() by Account_s 
        | where cnt < 1000;
    LowActivityAccounts | where Account_s contains "sql"
    ```

    <!--- 1. Change the **Time range** to **Last hour** in the Query Window. This limits our results for the following statements.

    1. The following statement demonstrates the **extend** operator, which creates a calculated column and adds it to the result set. In the Query Window, enter the following statement and select **Run**: 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process))
    ```

    1. The following statement demonstrates the **order by** operator, which sorts the rows of the input table by one or more columns in ascending or descending order. The **order by** operator is an alias to the **sort by** operator. In the Query Window, enter the following statement and select **Run**: 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) 
    | order by StartDir desc, Process asc
    ```

    1. The following statements demonstrate the **project** operator, which selects the columns to include in the order specified. In the Query Window, enter the following statement and select **Run**: 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) 
    | order by StartDir desc, Process asc 
    | project Process, StartDir
    ```

    1. The following statements demonstrate the **project-away** operator, which selects the columns to exclude from the output. In the Query Window, enter the following statement and select **Run**: 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) 
    | where ProcessName != "" and Process != "" 
    | extend StartDir =  substring(ProcessName,0, string_size(ProcessName)-string_size(Process)) 
    | order by StartDir desc, Process asc 
    | project-away ProcessName --->
    ```

### Task 4: Analyze Results in KQL with the Summarize Operator

In this task, you'll build KQL statements to aggregate data. **Summarize** groups the rows according to the **by** group columns, and calculates aggregations over each group.

1. The following statement demonstrates the **count()** function, which returns a count of the group. In the Query Window enter the following statement and select **Run**: 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) and EventID_s == 4688  
    | summarize count() by Computer
    ```

1. A instrução a seguir demonstra a função **count()**, mas, neste exemplo, nomeamos a coluna como *cnt*. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d) and EventID_s == 4624  
    | summarize cnt=count() by AccountType_s, Computer
    ```

1. A instrução a seguir demonstra a função **dcount()**, que retorna uma contagem distinta aproximada dos elementos do grupo. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    SigninLogs_CL  
    | where TimeGenerated > ago(7d)
    | summarize dcount(IpAddress)
    ```

1. A instrução a seguir é uma regra para detectar falhas de senha inválida em vários aplicativos para a mesma conta. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    let timeframe = 30d;
    let threshold = 1;
    SigninLogs_CL
    | where TimeGenerated >= ago(timeframe)
    | where ResultDescription has "Invalid password"
    | summarize applicationCount = dcount(AppDisplayName_s) by UserPrincipalName_s, IPAddress
    | where applicationCount >= threshold
    ```

1. A instrução a seguir demonstra a função **arg_max()**, que retorna uma ou mais expressões quando o argumento é maximizado. A seguinte instrução retorna a linha mais recente da tabela SecurityEvent_CL para o computador *VictimPC2*. O * na função arg_max solicita todas as colunas da linha. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    SecurityEvent_CL  
    | where Computer == "VictimPC2"
    | summarize arg_max(TimeGenerated,*) by Computer
    ```

1. A instrução a seguir demonstra a função **arg_min()**, que retorna uma ou mais expressões quando o argumento é minimizado. Nesta instrução, o SecurityEvent_CL mais antigo para o computador *VictimPC2* será retornado como o conjunto de resultados. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    SecurityEvent_CL  
    | where Computer == "VictimPC2"
    | summarize arg_min(TimeGenerated,*) by Computer
    ```

1. As instruções a seguir demonstram a importância de compreender os resultados com base na ordem do *pipe*. Na janela Consulta, insira as seguintes consultas e execute cada uma delas separadamente:

    1. A **Consulta 1** terá Contas que tiveram um logon como última atividade. A tabela SecurityEvent_CL será primeiro resumida e retornará a linha mais atual para cada Conta. Então, apenas as linhas com EventID_s igual a 4624 (login) serão retornadas.

        ```KQL
        SecurityEvent_CL  
        | summarize arg_max(TimeGenerated, *) by Account_s 
        | where EventID_s == 4624  
        ```

    1. A **Consulta 2** terá o logon mais recente para as Contas que fizeram logon. A tabela SecurityEvent_CL é filtrada para incluir apenas EventID_s = 4624. Em seguida, esses resultados são resumidos pela linha de logon mais recente por Conta.

        ```KQL
        SecurityEvent_CL  
        | where EventID_s == 4624  
        | summarize arg_max(TimeGenerated, *) by Account_s
        ```

    >**Observação:** você também pode revisar a "CPU total" e os "Dados usados para a consulta processada" selecionando o link "Detalhes da consulta" no canto inferior direito e comparar os dados entre ambas as instruções.

1. A instrução a seguir demonstra a função **make_list()**, que retorna uma *lista* de todos os valores dentro do grupo. Essa consulta KQL primeiro filtrará o EventID_s com o operador where. Em seguida, para cada Computador, os resultados são uma matriz JSON de Contas. A matriz JSON resultante incluirá contas duplicadas. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | where EventID_s == 4624  
    | summarize make_list(Account_s) by Computer
    ```

1. A instrução a seguir demonstra a função **make_set()**, que retorna um conjunto de valores *distintos* dentro do grupo. Essa consulta KQL primeiro filtrará o EventID_s com o operador where. Em seguida, para cada Computador, os resultados são uma matriz JSON de Contas exclusivas. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | where EventID_s == 4624  
    | summarize make_set(Account_s) by Computer
    ```

### Tarefa 5: Criar visualizações em KQL com o operador render

Nesta tarefa, você usará a geração de visualizações com instruções KQL.

1. A instrução a seguir demonstra o operador **render** (que renderiza os resultados como uma saída gráfica), usando uma visualização de **gráfico de barras**. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | summarize count() by Account_s
    | render barchart
    ```

1. A instrução a seguir demonstra o operador **render** visualizando resultados com uma série temporal. A função **bin()** arredonda todos os valores em um período de tempo e os agrupa, sendo usada com frequência em combinação com **summarize**. Se você tiver um conjunto disperso de valores, os valores serão agrupados em um conjunto menor de valores específicos. Combinar os resultados gerados e canalizá-los para um operador **render** com um **gráfico de tempo** fornece uma visualização de série temporal. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent_CL  
    | where TimeGenerated > ago(7d)
    | summarize count() by bin(TimeGenerated, 1m)
    | render timechart
    ```

### Tarefa 6: Compilar instruções de várias tabelas em KQL

Nesta tarefa, você compilará instruções de várias tabelas em KQL.

1. Altere o **Intervalo de tempo** para **Sete últimos dias** na janela Consulta. Isso limitará nossos resultados para as instruções a seguir.

1. A instrução a seguir demonstra o operador **union**, que pega duas ou mais tabelas e retorna todas as suas linhas. É essencial compreender como os resultados passam e sofrem impacto pelo caractere pipe. Na janela Consulta, insira as seguintes instruções e selecione **Executar** para cada consulta separadamente para ver os resultados:

    1. A **Consulta 1** retorna todas as linhas de SecurityEvent_CL e todas as linhas de SigninLogs_CL.

        ```KQL
        SecurityEvent_CL  
        | union SigninLogs_CL  
        ```

    1. A **Consulta 2** retorna uma linha e coluna, que é a contagem de todas as linhas de SigninLogs_CL e todas as linhas de SecurityEvent_CL.

        ```KQL
        SecurityEvent_CL  
        | union SigninLogs_CL  
        | summarize count() 
        ```

    1. A **Consulta 3** retorna todas as linhas de SecurityEvent_CL e uma (última) linha de SigninLogs_CL. A última linha de SigninLogs_CL apresentará a contagem resumida do número total de linhas.

        ```KQL
        SecurityEvent_CL  
        | union (SigninLogs_CL | summarize count() | project count_)
        ```

    >**Observação:** a "linha vazia" nos resultados mostrará a contagem resumida de SigninLogs_CL.

1. A instrução a seguir demonstra o suporte do operador **union** para unir várias tabelas com curingas. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    union App*  
    | summarize count() by Type
    ```

1. A instrução a seguir demonstra o operador **join**, que mescla as linhas de duas tabelas para formar uma nova tabela, combinando os valores das colunas especificadas de cada tabela. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    SecurityEvent_CL  
    | where EventID_s == 4624 
    | summarize LogOnCount=count() by  EventID_s, Account_s
    | project LogOnCount, Account_s
    | join kind = inner( 
     SecurityEvent_CL  
    | where EventID_s == 4634 
    | summarize LogOffCount=count() by  EventID_s, Account_s
    | project LogOffCount, Account_s
    ) on Account_s
    ```

    >**Importante:** a primeira tabela especificada no operador join é a tabela esquerda. A tabela depois do operador **join** é a tabela direita. Ao trabalhar com colunas das tabelas, o nome $left.Column e o nome $right.Column servem para distinguir quais colunas das tabelas são referenciadas. O operador **join** dá suporte a uma gama completa de tipos: flouter, inner, innerunique, leftanti, leftantisemi, leftouter, leftsemi, rightanti, rightantisemi, rightouter, rightsemi.

1. Você pode deixar o **Intervalo de tempo** em **Últimos 7 dias** na janela Consulta.

### Tarefa 7: Trabalhar com dados de cadeia de caracteres em KQL

Nesta tarefa, você trabalhará com campos de cadeia de caracteres estruturados e não estruturados com instruções KQL.

1. A instrução a seguir demonstra a função **extract**, que obtém uma correspondência para uma expressão regular de uma cadeia de caracteres de fonte. Você tem a opção de converter a substring extraída para o tipo indicado. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    print extract("x=([0-9.]+)", 1, "hello x=45.6|wo") == "45.6"
    ```

1. As instruções a seguir usam a função **extract** para extrair Account_s Name do campo Account_s da tabela SecurityEvent_CL. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

    ```KQL
    SecurityEvent_CL  
    | where EventID_s == 4672 and AccountType_s == 'User' 
    | extend Account_Name = extract(@"^(.*\\)?([^@]*)(@.*)?$", 2, tolower(Account_s))
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

    <!--- 1. The following statement demonstrates working with **dynamic** fields, which are special since they can take on any value of other data types. In this example, The DeviceDetail_s field from the SigninLogs_CL table is of type **dynamic**. In the Query Window, enter the following statement and select **Run**:

    ```KQL
    SigninLogs
    | extend OS = DeviceDetail.operatingSystem
    ```

     1. The following example shows how to break out packed fields for SigninLogs_CL. In the Query Window, enter the following statement and select **Run**:

    ```KQL
    SigninLogs_CL 
    | extend OS = DeviceDetail.operatingSystem, Browser = DeviceDetail.browser 
    | extend StatusCode = tostring(Status.errorCode), StatusDetails = tostring(Status.additionalDetails) 
    | extend Date = startofday(TimeGenerated) 
    | summarize count() by Date, Identity, UserDisplayName, UserPrincipalName, IPAddress, ResultType, ResultDescription, StatusCode, StatusDetails 
    | sort by Date

    SigninLogs_CL 
    | extend OS = todynamic(DeviceDetail_s)
    | where OS = DeviceDetail_s.operatingSystem, Browser = DeviceDetail_s.browser
    | extend StatusCode = tostring(Status_s.errorCode), StatusDetails = tostring(Status_s.additionalDetails) 
    | extend Date = startofday(TimeGenerated) 
    | summarize count() by Date, UserDisplayName_s, UserPrincipalName_s, IPAddress, ResultType, ResultDescription, StatusCode, StatusDetails, OS, Browser 
    | sort by Date

    ```

    >**Important:** Although the dynamic type appears JSON-like, it can hold values that the JSON model does not represent because they do not exist in JSON. Therefore, in serializing dynamic values into a JSON representation, values that JSON cannot represent are serialized into string values. --->

1. As instruções a seguir demonstram os operadores para manipular o JSON armazenado em campos de cadeia de caracteres. Muitos logs enviam dados no formato JSON, o que exige que você saiba como transformar dados JSON em campos que possam ser consultados. Na janela Consulta, insira a instrução a seguir e selecione **Executar**:

    ```KQL
    SigninLogs_CL 
    | extend AuthDetails =  parse_json(AuthenticationDetails_s) 
    | extend AuthMethod =  AuthDetails[0].authenticationMethod 
    | extend AuthResult = AuthDetails[0].["authenticationStepResultDetail"] 
    | project AuthMethod, AuthResult, AuthDetails 
    ```

1. A instrução a seguir demonstra o operador **mv-expand**, que transforma matrizes dinâmicas em linhas (expansão de vários valores).

    ```KQL
    SigninLogs_CL 
    | mv-expand AuthDetails = parse_json(AuthenticationDetails_s) 
    | project AuthDetails
    ```

1. Expanda a primeira linha selecionando ">" e, em seguida, expanda novamente ao lado de *AuthDetails* para revisar os resultados expandidos.

1. A instrução a seguir demonstra o operador **mv-apply**, que aplica uma subconsulta a cada registro e retorna a união dos resultados de todas as subconsultas.

    ```KQL
    SigninLogs_CL 
    | mv-apply AuthDetails = parse_json(AuthenticationDetails_s) on
    (where AuthDetails.authenticationMethod == "Password")
    ```

1. Uma **função** é uma consulta de log que pode ser usada em outras consultas de log com o nome salvo como um comando. Para criar uma **função**, depois de executar sua consulta, clique no botão **Salvar** e, em seguida, selecione **Salvar como função** no menu suspenso. Insira o nome desejado (por exemplo: *PrivLogins*) na caixa **Nome da função**, insira uma **Categoria herdada** (por exemplo: *Geral*) e selecione **Salvar**. A função estará disponível no KQL usando o alias da função:

    ```KQL
    PrivLogins  
    ```

## Você concluiu o laboratório
