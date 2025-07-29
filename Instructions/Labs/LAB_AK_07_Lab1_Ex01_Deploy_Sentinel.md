---
lab:
  title: 'Exercício 1: configurar seu ambiente do Microsoft Sentinel'
  module: Learning Path 7 - Configure your Microsoft Sentinel environment
---

# Roteiro de aprendizagem 7 — Laboratório 1 — Exercício 1 — Configurar seu ambiente do Microsoft Sentinel

## Cenário do laboratório

Você trabalha como analista de operações de segurança em uma empresa que está implementando o Microsoft Azure Sentinel. Você é responsável por configurar o ambiente do Microsoft Azure Sentinel para atender aos requisitos da empresa, a fim de minimizar os custos, atender às normas de conformidade e fornecer o ambiente mais gerenciável para que a equipe de segurança cumpra as responsabilidades de trabalho diárias.

>**Importante:** Os exercícios de laboratório para o Roteiro de Aprendizagem 7 estão em um ambiente *independente*. Se você sair do laboratório antes de concluí-lo, será necessário executar as configurações novamente.

### Tempo estimado para concluir este laboratório: 30 minutos

### Tarefa 1 – Crie um workspace do Log Analytics

Crie um workspace do Log Analytics, incluindo a opção de região. Saiba mais sobre a [integração do Microsoft Sentinel](https://learn.microsoft.com/azure/sentinel/quickstart-onboard).

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.

1. No navegador Microsoft Edge, acesse o portal do Azure em <https://portal.azure.com>.
  
1. Na caixa de diálogo **Entrar**, copie e cole a conta de email do locatário referente ao nome de usuário do administrador fornecido pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a senha de locatário do administrador fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite "Microsoft Sentinel" e selecione 

1. Selecione **+ Criar**.

1. Selecione **Criar um workspace**.

1. Selecione **Criar novo** para o Grupo de recursos.

1. Digite *Defender-RG* e selecione **Ok**.

1. Para o Nome, insira *defenderWorkspace*.

1. Você pode deixar a região padrão para o workspace.

1. Selecione **Examinar + criar** para validar o novo workspace.

1. Selecione **Criar** para implantar o workspace.

### Tarefa 2 – Implantar o Microsoft Sentinel em um workspace

Implantar o Microsoft Sentinel no workspace.

1. Quando a implantação do workspace for concluída, selecione **Página Inicial** no menu "estrutural" do Microsoft Azure.

1. Você verá o **Microsoft Sentinel** na seção de *serviços do Azure* do portal. Selecione-a.

1. Nos itens do menu, selecione **+ Criar**.

1. Selecione o workspace ao qual você deseja adicionar o Microsoft Sentinel (criado na Tarefa 1).

1. Selecione **Adicionar**.

### Tarefa 3 – Configurar a retenção de dados

1. No menu de navegação estrutural do Microsoft Azure, selecione **Página Inicial**.

1. Na barra de Pesquisa do portal do Azure, digite "Análise de logs" e selecione o espaço de trabalho criado na Tarefa 1.

1. Expanda a seção *Configurações* no menu de navegação e selecione **Uso e custos estimados**.

1. Selecione **Retenção de dados** nos itens de menu.

1. Altere o período de retenção de dados para **180 dias**.

1. Selecione **OK**.

### Tarefa 4: Criar uma lista de observação

Nesta tarefa, você irá criar uma watchlist no Microsoft Sentinel.

1. Na caixa de pesquisa na parte inferior da tela do Windows 10, insira *Bloco de notas*. Selecione **Bloco de notas** nos resultados.

1. Insira *Nome do host* e clique no Enter para criar uma nova linha.

1. Na linha 2 do Bloco de notas, copie os seguintes nomes de host, cada um em uma linha diferente:

    ```Notepad
    Host1
    Host2
    Host3
    Host4
    Host5
    ```

1. No menu, selecione **Arquivo – Salvar como**, nomeie o arquivo *HighValue.csv*, altere o tipo de arquivo de **Todos os arquivos(*.*)** e selecione **Salvar**. **Dica:** o arquivo pode ser salvo na pasta *Documentos*.

1. Feche o Bloco de notas.

1. No menu "estrutural" do Microsoft Azure, selecione **Página Inicial**.

1. Você verá o bloco **Microsoft Sentinel** na seção *Serviços do Azure* no portal. Selecione-a.

1. Selecione o workspace do Microsoft Sentinel **defenderWorkspace**.

1. No Microsoft Sentinel, selecione a opção **Watchlist** na área Configuração.

1. Escolha **+ Novo** na barra de comandos.

1. No assistente Watchlist, insira as seguintes informações:

    |Configurações gerais|Valor|
    |---|---|
    |Nome|**HighValueHosts**|
    |Descrição|**Hosts de alto valor**|
    |Alias da watchlist|**HighValueHosts**|

1. Selecione **Avançar: Fonte >**.

1. Selecione **Procurar arquivos** em *Carregar arquivo* e procure o arquivo *HighValue.csv* que você criou.

1. No campo *SearchKey,* selecione **Nome do host**.

1. Clique em **Avançar: Examinar e criar >**.

1. Examine as configurações que você definiu e selecione **Criar**.

1. A tela retorna à página Watchlist.

1. Selecione **Atualizar** no menu para ver a nova lista de observação.

1. Selecione a watchlist *HighValueHosts* e, no painel direito, selecione **Exibir em logs**.

    >**Importante:** pode levar até dez minutos para que a watchlist apareça. **Prossiga para a tarefa a seguir e execute este comando no próximo laboratório**.

    >**Observação:** agora você pode usar o _GetWatchlist('HighValueHosts') em suas próprias instruções KQL para acessar a lista. A coluna a ser referenciada seria *Nome do host*.

1. Feche a janela *Logs* selecionando o "x" no canto superior direito e selecione **OK** para descartar as edições não salvas.

### Tarefa 5: Criar um indicador de ameaça

Nesta tarefa, você irá criar um indicador no Microsoft Sentinel.

1. No Microsoft Sentinel, selecione a opção **Inteligência contra ameaças** na área Gerenciamento de ameaças.

1. Na barra de comandos, selecione **+ Adicionar novo**.

1. Selecione o **Objeto de TI**.

1. No menu suspenso *Tipo de objeto*, selecione **Indicador**.

1. Selecione a lista suspensa **+ Novo observável** e selecione **Nome de domínio**.

1. Em Domínio, insira o nome de domínio, por exemplo, *contoso.com*.

1. No campo **Nome**, insira o mesmo valor usado para o Domínio.

1. Nos *Tipos de indicador*, selecione **malicious-activity**.

1. Defina o campo **Válido de** como a data de hoje.

1. Role para baixo até a **Descrição** e digite *Este domínio é conhecido por ser malicioso*.

1. Selecione **Adicionar**.

1. Selecione a opção **Logs** na área *Geral* do menu de navegação do *Sentinel*. Talvez você queira desabilitar a opção " Sempre mostrar consultas" e fechar a janela *Consultas* para executar as instruções KQL.

    >**Observação:** na guia padrão *Nova Consulta 1*, a consulta **_GetWatchList('HighValueHosts')** ainda estará lá e agora produzirá resultados se for executada.

1. Selecione o sinal *+* para criar uma guia de consulta.

1. Execute a seguinte instrução KQL.

    ```KQL
    ThreatIntelligenceIndicator
    ```

    >**Observação:** pode levar até dez minutos para que o indicador apareça.

1. Role os resultados para a direita para ver a coluna DomainName. Você também pode executar a seguinte instrução KQL para ver apenas a coluna DomainName.

    ```KQL
    ThreatIntelligenceIndicator 
    | project DomainName
    ```

### Tarefa 6: Configurar retenção de log

Nesta tarefa, você irá alterar o período de retenção da tabela SecurityEvent.

1. No Microsoft Sentinel, selecione a opção **Configurações** na área *Configuração*.

1. Selecione **Configurações do workspace**.

1. No workspace do Log Analytics, selecione a opção **Tabelas** na área *Configurações*.

1. Pesquise e selecione a tabela **SecurityEvent** e, em seguida, clique no link de reticências (...).

    >**Observação:** talvez seja necessário rolar para a direita para ver o link de reticências.

1. Selecionar **Gerenciar tabela**.

1. Altere o *Período de retenção interativa* para **90 dias**.

1. Redefina o *Período de retenção total* para **180 dias** (se necessário). Observe que o *Período de arquivo* está definido como *90 dias*, pois o *Azure Monitor* trata automaticamente os 90 dias restantes de retenção total como retenção de longo prazo e baixo custo.

1. Selecione **Salvar** para aplicar as alterações.

## Você concluiu o laboratório
