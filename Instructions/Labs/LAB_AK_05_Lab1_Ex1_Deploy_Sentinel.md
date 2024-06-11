---
lab:
  title: 'Exercício 1: configurar seu ambiente do Microsoft Sentinel'
  module: Learning Path 5 - Configure your Microsoft Sentinel environment
---

# Roteiro de aprendizagem 5, Laboratório 1, Exercício 1: configurar seu ambiente do Microsoft Sentinel

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod5_L1_Ex1.png)

Você trabalha como analista de operações de segurança em uma empresa que está implementando o Microsoft Sentinel. Você é responsável por configurar o ambiente do Microsoft Sentinel para atender aos requisitos da empresa, a fim de minimizar os custos, atender às normas de conformidade e fornecer o ambiente mais gerenciável para que a equipe de segurança cumpra as responsabilidades de trabalho diárias.

>**Observação:** uma **[simulação de laboratório interativa](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Configure%20your%20Microsoft%20Sentinel%20environment)** está disponível e permite que você clique neste laboratório no seu próprio ritmo. Você pode encontrar pequenas diferenças entre a simulação interativa e o laboratório hospedado, mas os principais conceitos e ideias que estão sendo demonstrados são os mesmos. 


### Tarefa 1: inicializar o workspace do Microsoft Sentinel

Nesta tarefa, você criará um workspace do Microsoft Sentinel.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.  

1. Abra o navegador Edge.

1. No navegador Edge, acesse o portal do Azure em https://portal.azure.com.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione **+ Criar**.

1. Em seguida, selecione o workspace do Log Analytics criado anteriormente, por exemplo, *uniquenameDefender*, e selecione **Adicionar**. A ativação pode levar alguns minutos.

    >**Observação:** se você não vir um workspace do Log Analytics aqui, consulte o Módulo 3, Exercício 1, Tarefa 2 para criar um.

1. No **Microsoft Sentinel** você deve estar na seção **Geral** *Notícias e Guias* e consultar um aviso informando a *Ativação da avaliação gratuita do Microsoft Sentinel*. Clique no botão **OK**.

1. Navegue pelo workspace recém-criado do Microsoft Sentinel para se familiarizar com as opções da interface do usuário.

### Tarefa 2: criar uma watchlist

Nesta tarefa, você criará uma watchlist no Microsoft Sentinel.

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

1. No Microsoft Sentinel, selecione a opção **Watchlist** na área Configuração.

1. Na barra de comandos, selecione **+ Adicionar novo**.

1. No assistente Watchlist, insira as seguintes informações:

    |Configurações gerais|Valor|
    |---|---|
    |Nome|**HighValueHosts**|
    |Descrição|**Hosts de alto valor**|
    |Alias da watchlist|**HighValueHosts**|

1. Selecione **Avançar: Fonte >**.

1. Selecione **Procurar arquivos** em *Carregar arquivo* e procure o arquivo *HighValue.csv* que você acabou de criar.

1. No *campo SearchKey*, selecione **Nome do host**.

1. Clique em **Avançar: Examinar e criar >**.

1. Examine as configurações que você definiu e selecione **Criar**.

1. A tela retorna à página Watchlist.

1. Selecione a watchlist *HighValueHosts* e, no painel direito, selecione **Exibir em logs**.

    >**Importante:** pode levar até dez minutos para que a watchlist apareça. **Prossiga para a tarefa a seguir e execute este comando no próximo laboratório**.
    
    >**Observação:** agora você pode usar o _GetWatchlist('HighValueHosts') em suas próprias instruções KQL para acessar a lista. A coluna a ser referenciada seria *Nome do host*.

1. Feche a janela *Logs* selecionando o "x" no canto superior direito e selecione **OK** para descartar as edições não salvas.


### Tarefa 3: criar um indicador de ameaça

Nesta tarefa, você criará um indicador no Microsoft Sentinel.

1. No Microsoft Sentinel, selecione a opção **Inteligência contra ameaças** na área Gerenciamento de ameaças.

1. Na barra de comandos, selecione **+ Adicionar novo**.

1. Analise os diferentes tipos de indicadores disponíveis na lista suspensa *Tipos*. Selecione **domain-name**. 

1. Em Domínio, insira o nome de domínio, por exemplo, *contoso.com*.

1. Para *Tipos de ameaça*, selecione **+ Adicionar** e digite **malicious-activity**. Selecione **OK**.

1. Insira uma **Descrição**

1. Para o **Nome**, insira o mesmo valor usado para o Domínio.

1. Defina o campo **Válido de** como a data de hoje.

1. Selecione **Aplicar**.

1. Selecione a opção **Logs** na área Geral. Talvez você queira desabilitar a opção " Sempre mostrar consultas" e fechar a janela *Consultas* para executar as instruções KQL.

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


### Tarefa 4: configurar retenção de log

Nesta tarefa, você alterará o período de retenção da tabela SecurityEvent.

1. No Microsoft Sentinel, selecione a opção **Configurações** na área *Configuração*.

1. Selecione **Configurações do workspace**.

1. No workspace do Log Analytics, selecione a opção **Tabelas** na área *Configurações*.

1. Pesquise e selecione a tabela **SecurityEvent** e, em seguida, clique no botão de reticências (...).

1. Selecionar **Gerenciar tabela**.

1. Selecione **180 dias** para *Período de retenção total*. Observe que o *Período de arquivamento* é de apenas 150 dias, pois ele usa 30 dias da *Retenção interativa* (padrão).

1. Selecione **Salvar** para aplicar as alterações.


## Você concluiu o laboratório.
