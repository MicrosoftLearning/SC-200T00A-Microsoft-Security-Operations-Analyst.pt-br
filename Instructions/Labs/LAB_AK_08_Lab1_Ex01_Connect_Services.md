---
lab:
  title: 'Exercício 1: conectar os dados ao Microsoft Sentinel usando os conectores de dados'
  module: Learning Path 8 - Connect logs to Microsoft Sentinel
---

# Roteiro de aprendizagem 8 – Laboratório 1 – Exercício 1 – Conectar dados ao Microsoft Sentinel usando conectores de dados

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex1.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você deve saber como conectar os dados de log de várias fontes de dados na organização. A organização tem dados do Microsoft 365, do Microsoft Defender XDR, dos recursos do Azure, das máquinas virtuais não relacionadas ao Azure etc. Você começa a conectar as fontes da Microsoft primeiro.

>**Importante:** os exercícios de laboratório para o Roteiro de Aprendizagem 8 estão em um ambiente *independente*. Se você sair do laboratório antes de concluí-lo, será necessário executar as configurações novamente.

### Tempo estimado para concluir este laboratório: 20 minutos

### Tarefa 1: acessar o workspace do Microsoft Sentinel

Nesta tarefa, você irá acessar seu workspace do Microsoft Sentinel.

>**Observação:** o Microsoft Sentinel foi pré-implantado em sua assinatura do Azure com o nome **defenderWorkspace** e as soluções necessárias do *hub de conteúdo* foram instaladas.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.  

1. Abra o navegador Microsoft Edge.

1. No navegador Edge, acesse o portal do Azure em <https://portal.azure.com>.

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o **defenderWorkspace** do Microsoft Sentinel.

1. Prossiga para a próxima tarefa.

### Tarefa 2: conectar o conector de dados do Microsoft Defender para Nuvem

Nesta tarefa, você irá se conectar ao conector de dados do Microsoft Defender para Nuvem.

1. No menu de navegação do Microsoft Sentinel, role para baixo até a seção **Gerenciamento de conteúdo** e selecione **Hub de conteúdo**.

1. No *Hub de conteúdo*, procure a solução **Microsoft Defender para Nuvem** e selecione-a na lista.

1. Na página de detalhes da solução do Microsoft Defender para Nuvem, selecione **Gerenciar**.

    >**Observação:** a solução *Microsoft Defender para Nuvem* instala o conector de dados do *Microsoft Defender para Nuvem (Herdado) baseado em assinatura*, o conector de dados do *Microsoft Defender para Nuvem (Versão preliminar) baseado em locatário* e uma regra de Análise. O conector de dados *Microsoft Defender for Cloud (versão prévia)* baseado em locatário é usado quando um locatário tem várias assinaturas.

1. Selecione a caixa de seleção Conector de dados do *Microsoft Defender para Nuvem (Herdado) baseado em assinatura* e selecione a **página Abrir conector**.

1. Na seção *Configuração*, **marque** a caixa de seleção da *MOC Subscription-XXXXXXXXXXX* e clique no link **Conectar**.

1. O **Status** agora deve ser **Conectado**.

1. Para habilitar a sincronização bidirecional, selecione o link **Habilitar o Microsoft Defender para todas as assinaturas**.

    >**Observação:** talvez seja necessário rolar para a direita para ver o link.

1. Na página *Microsoft Defender para Nuvem – Introdução*, a caixa de seleção da *MOC Subscription-XXXXXXXXXXX* estará selecionada e o *plano do Microsoft Defender* exibirá *Habilitado – Parcial (30 dias de avaliação restantes)*.

1. Selecione o botão **X (Fechar)** no canto superior direito para fechar a página *Introdução*. Você retornará à página de configuração do *Microsoft Defender para Nuvem*.

1. O *Status* da *MOC Subscription-XXXXXXXXXXX* será *Conectado* e a *Sincronização bidirecional* deve estar **Habilitada**.

    >**Observação:** talvez seja necessário repetir este procedimento para ver a *Sincronização bidirecional habilitada*. Depois de executar novamente as etapas, tente definir o menu suspenso *Sincronização bidirecional* como **Habilitada**.

### Tarefa 3: conector o conector de dados de Atividade do Azure

Nesta tarefa, você conectará o conector de dados de *Atividade do Azure*.

1. No menu de navegação do Microsoft Sentinel, role para baixo até a seção *Gerenciamento de conteúdo* e selecione **Hub de conteúdo**.

1. No *Hub de conteúdo*, procure a solução de **Atividade do Azure** e selecione-a na lista.

1. Na página de detalhes da solução *Atividade do Azure*, selecione **Gerenciar**.

    >**Observação:** a solução de *Atividade do Azure* instala o conector de dados de *Atividade do Azure*, 13 regras de análise, 14 consultas de busca e 1 pasta de trabalho.

1. Selecione um conector de dados de *Atividade do Azure* e depois clique no botão **Abrir página do conector**.

1. Na área *Configuração*, a guia *Instruções*, role a página para baixo até "2. Conecte suas assinaturas..." e, por fim, selecione **Iniciar assistente de atribuição do Azure Policy>**.

1. Na guia **Básico**, selecione o botão de reticências (...) em **Escopo**, escolha sua assinatura *MOC Subscription-XXXXXXXXXXX* na lista suspensa e clique em **Selecionar**.

    >**Observação:***Não* selecione um grupo de recursos opcional.

1. Selecione a guia **Parâmetros**, escolha o workspace *uniquenameDefender* na lista suspensa **Workspace principal do Log Analytics**. Essa ação aplica a configuração de assinatura para enviar as informações para o workspace do Log Analytics.

1. Selecione a guia **Correção** e marque a caixa de seleção **Criar uma tarefa de correção**. Essa ação aplicará a política a recursos já existentes do Azure.

1. Selecione o botão **Examinar + criar** para examinar a configuração.

1. Selecione **Criar** para concluir.

## Prossiga para o Exercício 2
