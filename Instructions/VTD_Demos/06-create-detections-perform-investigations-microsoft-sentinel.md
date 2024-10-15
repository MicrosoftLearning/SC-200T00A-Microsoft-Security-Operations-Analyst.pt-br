# Módulo 6: criar detecções e executar investigações com o Microsoft Sentinel

**Observação**: a conclusão bem-sucedida desta demonstração depende da conclusão de todas as etapas no [documento de Pré-requisitos](00-prerequisites.md).

**Importante:** esta demonstração não é necessária para o VTD-5002-FY25.

## Criar uma regra de consulta NRT

Nesta tarefa, você criará uma regra de consulta analítica NRT (Near Real Time).

1. No Microsoft Sentinel, em *Configuração*, selecione a página **Análise**.

1. Selecione a guia **Criar** e, em seguida, a **Regra de consulta NRT**.

1. Isso abre o "Assistente de regras de análise". Para a regra *Geral*, digite:

    |Configuração|Valor|
    |---|---|
    |Nome|**Busca do PowerShell NRT**|
    |Descrição|**Busca do PowerShell NRT**|
    |Táticas e Técnicas|**Comando e controle**|
    |Severidade|**Alta**|

1. Clique no botão **Avançar: Definir lógica da regra >**. 

1. Para *Consulta de regra*, insira a seguinte instrução KQL:

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam
    ```

1. Selecione **Exibir resultados da consulta >** para garantir que sua consulta não tenha erros.

1. Feche a janela *Logs* selecionando o **X** no canto superior direito da janela e selecione **OK** para descartar as alterações. 

1. Selecione **Testar com dados atuais** em *Simulação de resultados*. Observe o número esperado de *Alertas por dia*.

1. Em *Mapeamento de entidade*, selecione:

    - Na lista suspensa *Tipo de entidade*, selecione **Host**.
    - Na lista suspensa *Identificador*, selecione **Nome do host**.
    - Na lista suspensa *Valor*, selecione **Computador**.

1. Role para baixo e selecione o botão **Avançar: Configurações de Incidentes>**.

1. Para a guia *Configurações de Incidentes*, deixe os valores padrão e selecione o botão **Avançar: Resposta automatizada >**.

1. Selecione **Avançar: Revisar + criar >**.

1. Na guia *Revisar e criar*, selecione o botão **Salvar** para criar e salvar a nova regra de Análise Agendada.

## Detecção de ataques do Windows configurado com o AMA (agente do Azure Monitor)

Nesta tarefa, você investigará o incidente criado a partir da regra `NRT` que você criou.

1. Faça logon na máquina virtual WIN1 como administrador com a senha: **Pa55w.rd**.  

1. No navegador Edge, acesse o portal do Azure em https://portal.azure.com.

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** para administrador fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** para administrador fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o workspace do Microsoft Sentinel que você criou anteriormente.

1. No `Microsoft Sentinel`, vá para a seção do menu `Threat management` e selecione **Incidentes**

**Observação**: podem ser necessários vários minutos para que o `Incident` seja exibido.

1. Você verá um incidente que corresponda à `Severity` e `Title` que você configurou na regra `NRT` criada

1. Selecione o `Incident` e o painel `detail` será aberto

1. Selecione **Exibir detalhes completos** e selecione o botão **Investigar**.

1. Explore as `Entities` associadas com o incidente `NRT PowerShell Hunt`.

1. Feche a janela `Investigation` selecionando o **X** no canto superior direito.

1. Selecione a guia `Logs` e insira a seguinte instrução KQL:

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam
    ```

**Observação**: você pode encontrar essa consulta no `Queries History`, e pode **Executar** a partir daí.

1. Selecione o botão **Pronto** para fechar a janela `Logs`.

1. Feche a janela `Incident` selecionando o **X** no canto superior direito.

## Você concluiu a demonstração
