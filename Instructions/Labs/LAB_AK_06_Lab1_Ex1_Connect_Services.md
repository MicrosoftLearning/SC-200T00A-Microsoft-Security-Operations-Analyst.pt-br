---
lab:
  title: 'Exercício 1: conectar os dados ao Microsoft Sentinel usando os conectores de dados'
  module: Learning Path 6 - Connect logs to Microsoft Sentinel
---

# Roteiro de aprendizagem 6, Laboratório 1, Exercício 1: conectar os dados ao Microsoft Sentinel usando os conectores de dados

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex1.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você deve saber como conectar os dados de log de várias fontes de dados na organização. A organização tem dados do Microsoft 365, do Microsoft 365 Defender, dos recursos do Azure, de máquinas virtuais que não pertencem ao Azure etc. Comece a conectar as fontes da do Microsoft primeiro.

>**Observação:** uma **[simulação de laboratório interativa](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Connect%20data%20to%20Microsoft%20Sentinel%20using%20data%20connectors)** está disponível e permite que você clique neste laboratório no seu próprio ritmo. Você pode encontrar pequenas diferenças entre a simulação interativa e o laboratório hospedado, mas os principais conceitos e ideias que estão sendo demonstrados são os mesmos. 


### Tarefa 1: acessar o workspace do Microsoft Sentinel

Nesta tarefa, você acessará seu workspace do Microsoft Sentinel.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.  

1. Abra o navegador Microsoft Edge.

1. No navegador Edge, acesse o portal do Azure em https://portal.azure.com.

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o workspace do Microsoft Sentinel que você criou no laboratório anterior.

1. Prossiga para a próxima tarefa.

### Tarefa 2: conectar o conector de dados do Microsoft Defender para Nuvem

Nesta tarefa, você conectará o conector de dados do Microsoft Defender para Nuvem.

1. No menu esquerdo do Microsoft Sentinel, role para baixo até a seção **Gerenciamento de conteúdo** e selecione **Hub de conteúdos**.

1. No *Hub de conteúdo*, procure a solução **Microsoft Defender para Nuvem** e selecione-a na lista.

1. Na página de detalhes da solução do *Microsoft Defender para Nuvem*, selecione **Instalar**.

1. Quando a instalação for concluída, pesquise a solução do **Microsoft Defender para Nuvem** e selecione-a.

1. Na página de detalhes da solução do *Microsoft Defender para Nuvem*, selecione **Gerenciar**

    >**Observação:** a solução *Microsoft Defender para Nuvem* instala o conector de dados do *Microsoft Defender para Nuvem (Herdado) baseado em assinatura*, o conector de dados do *Microsoft Defender para Nuvem (Versão preliminar) baseado em locatário* e uma regra de Análise. O conector de dados *Microsoft Defender for Cloud (versão prévia)* baseado em locatário é usado quando um locatário tem várias assinaturas.

1. Selecione a caixa de seleção Conector de dados do *Microsoft Defender para Nuvem (Herdado) baseado em assinatura* e selecione a **página Abrir conector**.

1. Na seção *Configuração*, na guia *Instruções*,** marque** a caixa de seleção da assinatura "Azure Pass - Patrocínio" e deslize a opção **Status** para a direita.

    >**Observação:** se ele voltar a ser desconectado, revise o Roteiro de aprendizagem 3, Exercício 1, Tarefa 1 para atribuir as permissões adequadas à sua conta.

1. O *Status* agora deve ser **Conectado** e "Sincronização bidirecional" deve estar *Habilitada*.

    <!--- 1. Scroll down and under the *Create incidents - Recommended!* area, verify that *Create incidents automatically from all alerts generated in this connected service* is **Enabled**. --->

### Tarefa 3: conector o conector de dados de Atividade do Azure

Nesta tarefa, você conectará o conector de dados de *Atividade do Azure*.

1. No menu esquerdo do Microsoft Sentinel, role para baixo até a seção *Gerenciamento de conteúdo* e selecione **Hub de conteúdos**.

1. No *Hub de conteúdo*, procure a solução de **Atividade do Azure** e selecione-a na lista.

1. Na página da solução *Atividade do Azure*, selecione **Instalar**.

1. Quando a instalação for concluída, selecione **Gerenciar**

    >**Observação:** A solução de *Atividade do Azure* instala o conector de dados de *Atividade do Azure*, 12 regras de análise, 14 consultas de busca, 1 pasta de trabalho.

1. Selecione um conector de dados de *Atividade do Azure* e depois clique no botão **Abrir página do conector**.

1. Na área *Configuração*, a guia *Instruções*, role a página para baixo até "2. Conecte suas assinaturas..." e, por fim, selecione **Iniciar assistente de atribuição do Azure Policy>**.

1. Na guia **Básico**, clique no botão de reticências (...) em **Escopo** e selecione sua assinatura "Azure Pass – Sponsorship" na lista suspensa e clique em **Selecionar**.

1. Selecione a guia **Parâmetros**, escolha o workspace *uniquenameDefender* na lista suspensa **Workspace principal do Log Analytics**. Essa ação aplicará a configuração de assinatura para enviar as informações ao workspace do Log Analytics.

1. Selecione a guia **Correção** e marque a caixa de seleção **Criar uma tarefa de correção**. Essa ação aplicará a política a recursos já existentes do Azure.

1. Selecione o botão **Examinar + criar** para examinar a configuração.

1. Selecione **Criar** para concluir.

## Prossiga para o Exercício 2
