---
lab:
  title: 'Exercício 1: realizar a busca de ameaças no Microsoft Sentinel'
  module: Learning Path 8 - Perform threat hunting in Microsoft Sentinel
---

# Roteiro de aprendizagem 8, Laboratório 1, Exercício 1: realizar a busca de ameaças no Microsoft Sentinel

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod8_L1_Ex1.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você recebeu a inteligência contra ameaças sobre uma técnica de Comando e controle (C2 ou C&C). É necessário realizar uma busca e observar a ameaça.

>**Importante:** os dados de log usados no laboratório foram criados no módulo anterior. Veja o **Ataque 3** no servidor WIN1 no Exercício 5.

>**Observação:** como você já experimentou o processo de exploração de dados em um módulo anterior, este laboratório fornece uma instrução KQL para começar.

>**Observação:** uma **[simulação de laboratório interativa](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Perform%20threat%20hunting%20in%20Microsoft%20Sentinel)** está disponível e permite que você clique neste laboratório no seu próprio ritmo. Você pode encontrar pequenas diferenças entre a simulação interativa e o laboratório hospedado, mas os principais conceitos e ideias que estão sendo demonstrados são os mesmos. 


### Tarefa 1: criar uma consulta de busca

Nesta tarefa, você criará uma consulta de busca, marcará um resultado e criará uma transmissão ao vivo.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Edge, acesse o portal do Azure em <https://portal.azure.com>.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione seu workspace do Microsoft Sentinel.

1. Selecione **Logs** 

1. Insira a instrução KQL a seguir no espaço *Nova consulta 1*:

   >**Importante:** cole as consultas KQL primeiro no Bloco de notas e, em seguida, copie-as para a janela Log de *Nova consulta 1* para evitar erros.

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam 
    | order by count_ desc nulls last 
    ```

1. Analise os diferentes resultados. Agora você identificou as solicitações do PowerShell que estão sendo executadas em seu ambiente.

1. Marque a caixa de seleção dos resultados que mostra o *"-file c2.ps1"*.

1. Na barra de comandos do painel *Resultados*, clique no botão **Adicionar indicador**.

1. Selecione **+ Adicionar nova entidade** em *Mapeamento de entidade*.

1. Em *Entidade*, selecione **Host** e, em seguida, **Nome do host** e **Computador** para obter os valores.

1. Em *Táticas e técnicas*, selecione **Comando e controle**.

1. Na folha *Adicionar indicador*, selecione **Criar**. Mapearemos este indicador para um incidente mais tarde.

1. Feche a janela *Logs* selecionando o **X** no canto superior direito da janela e selecione **OK** para descartar as alterações. 

1. Selecione seu workspace do Microsoft Sentinel novamente e depois selecione a página **Busca** na área *Gerenciamento de ameaças*.

1. Selecione a **guia Consultas** e, em seguida, **+ Nova consulta** na barra de comandos.

1. Na janela *Criar consulta personalizada*, em *Nome*, insira **Busca do PowerShell**.

1. Para *Consulta personalizada*, insira a seguinte instrução KQL:

    ```KQL
    let lookback = 2d; 
    SecurityEvent 
    | where TimeGenerated >= ago(lookback) 
    | where EventID == 4688 and Process =~ "powershell.exe"
    | extend PwshParam = trim(@"[^/\\]*powershell(.exe)+" , CommandLine) 
    | project TimeGenerated, Computer, SubjectUserName, PwshParam 
    | summarize min(TimeGenerated), count() by Computer, SubjectUserName, PwshParam 
    | order by count_ desc nulls last 
    ```

1. Role para baixo e, em *Mapeamento de entidade*, selecione:

    - Na lista suspensa *Tipo de entidade*, selecione **Host**.
    - Na lista suspensa *Identificador*, selecione **Nome do host**.
    - Na lista suspensa *Valor*, selecione **Computador**.

1. Role para baixo e, em *Táticas e técnicas*, selecione **Comando e controle** e, em seguida, selecione **Criar** para criar a consulta de busca.

1. Na folha *"Microsoft Sentinel – Busca"*, procure a consulta que você acabou de criar na lista, *Busca do PowerShell*.

1. Selecione **Busca do PowerShell** na lista.

1. Revise o número de resultados no painel do meio na coluna *Resultados*.

1. Selecione o botão **Exibir resultados** no painel direito. Sua consulta KQL será executada automaticamente.

1. Feche a janela *Logs* selecionando o **X** no canto superior direito da janela e selecione **OK** para descartar as alterações. 

1. Clique com o botão direito do mouse na consulta **Busca do PowerShell** e selecione **Adicionar à transmissão ao vivo**. **Dica:** isso também pode ser feito deslizando para a direita e selecionando as reticências **(...)** no final da linha para abrir um menu de contexto.

1. Verifique se o *Status* agora está *Em execução*. Isso será executado a cada 30 segundos em segundo plano, e você receberá uma notificação no Portal do Azure (ícone de sino) quando um novo resultado for encontrado. 

1. Selecione a guia **Indicadores** no painel do meio.

1. Selecione o indicador que você acabou de criar na lista de resultados.

1. No painel direito, role para baixo e selecione o botão **Investigar**. **Dica:** pode levar alguns minutos para mostrar o gráfico de investigação.

1. Explore o gráfico de Investigação assim como você fez no módulo anterior. Observe o alto número de *Alertas relacionados* ao *WINServer*.

1. Feche a janela do gráfico de *Investigação* selecionando o **X** no canto superior direito da janela. 

1. Oculte a folha direita selecionando o ícone **>>** e, em seguida, role para a direita até ver o ícone de reticências **(...)**.

1. Selecione **Adicionar a um incidente existente**. Todos os incidentes aparecem no painel direito.

1. Selecione um dos incidentes e então clique em **Adicionar**.

1. Role para a esquerda para ver que a coluna *Severidade* agora está preenchida com os dados do incidente.


### Tarefa 2: criar uma regra de consulta de NRT

Nesta tarefa, em vez de usar um LiveStream, você criará uma regra de consulta de análise NRT. As regras NRT são executadas a cada minuto e retrocedem um minuto. O benefício das regras NRT é que elas podem usar a lógica de criação de alertas e incidentes.

1. No Microsoft Sentinel, em *Configuração*, selecione a página **Análise**. 

1. Selecione a guia **Criar** e, em seguida, a **Regra de consulta NRT**.

1. Isso abre o "Assistente de regras de análise". Para a regra *Geral*, digite:

    |Configuração|Valor|
    |---|---|
    |Nome|**Busca do PowerShell NRT**|
    |Descrição|**Busca do PowerShell NRT**|
    |Táticas|**Comando e controle**|
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

1. Na guia *Configurações de Incidentes*, deixe os valores padrão e clique no botão **Avançar: Resposta automatizada >**.

1. Na guia *Resposta automatizada*, clique no botão **Avançar: Revisar e criar >**.

1. Na guia *Examinar e criar*, selecione o botão **Salvar** para criar e salvar a nova regra de Análise agendada.

### Tarefa 3: criar um trabalho de Pesquisa

Nesta tarefa, você usará um trabalho de Pesquisa para procurar um C2.

>**Observação:** a operação de *Restauração* incorre em custos que podem esgotar seus créditos de assinatura do Azure Pass. Por esse motivo, você não executará a operação de restauração neste laboratório. No entanto, você pode seguir as etapas abaixo para executar a operação de restauração em seu próprio ambiente.

1. Selecione a página **Pesquisar** em *Geral* no Microsoft Sentinel.

1. Na caixa de pesquisa, insira **reg.exe** e depois selecione **Iniciar**.

1. Será aberta uma nova janela executando a consulta. Selecione o ícone de reticências **(...)** no canto superior direito e, em seguida, alterne o **modo Pesquisar trabalho**.

1. Clique no botão **Pesquisar trabalho** na barra de comandos. 

1. O trabalho de pesquisa cria uma nova tabela com seus resultados assim que eles chegam. Os resultados podem ser consultados na guia *Pesquisas salvas*.

1. Feche a janela *Logs* selecionando o **X** no canto superior direito da janela e selecione **OK** para descartar as alterações.

1. Selecione a guia **Restauração** na barra de comandos e, em seguida, clique no botão **Restaurar**.

1. Em *Selecionar uma tabela a ser restaurada*, pesquise e selecione **SecurityEvent**.

1. Revise as opções disponíveis e clique no botão **Cancelar**.

    >**Observação:** se você estivesse executando o trabalho, a restauração seria executada por alguns minutos e seus dados estariam disponíveis em uma nova tabela.

## Prossiga para o Exercício 2
