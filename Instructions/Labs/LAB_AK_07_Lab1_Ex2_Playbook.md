---
lab:
  title: 'Exercício 2: criar um guia estratégico'
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 7, Laboratório 1, Exercício 2: criar um guia estratégico

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex2.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você deve aprender a detectar e mitigar ameaças usando o Microsoft Sentinel. Agora, você deseja responder e corrigir ações que podem ser executadas pelo Microsoft Sentinel como uma rotina.

Com um guia estratégico, você pode ajudar a automatizar e orquestrar sua resposta a ameaças, integrar-se a outros sistemas internos e externos e pode ser configurado para ser executado automaticamente em resposta a alertas ou incidentes específicos, quando disparado por uma regra de análise ou uma regra de automação, respectivamente. 

>**Observação:** uma **[simulação de laboratório interativa](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Create%20a%20playbook)** está disponível e permite que você clique neste laboratório no seu próprio ritmo. Você pode encontrar pequenas diferenças entre a simulação interativa e o laboratório hospedado, mas os principais conceitos e ideias que estão sendo demonstrados são os mesmos.

### Tarefa 1: criar uma equipe do Centro de operações de segurança no Microsoft Teams

Nesta tarefa, você criará uma equipe do Microsoft Teams para uso no laboratório.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Microsoft Edge, abra uma nova guia e navegue até o portal do Microsoft Teams em (https://teams.microsoft.com).

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Feche todos os pop-ups do Teams que possam aparecer.

1. Se ainda não estiver selecionado, selecione **Teams** no menu esquerdo e, na parte superior, selecione o ícone de ![sinal de mais](../Media/plus-sign-icon-lab.png).

1. Selecione a opção **Criar uma equipe**.

1. Clique no botão **Do zero**.

1. Clique no botão **Particular**.

1. Dê o nome à equipe: digite **SOC** e clique no botão **Criar**.

1. Na tela Adicionar membros ao SOC, clique no botão **Ignorar**. 

1. Role a folha do Teams para baixo para localizar a equipe SOC recém-criada, selecione as reticências **(...)** no lado direito do nome e selecione **Adicionar canal**.

1. Insira um nome de canal de *Novos alertas* e selecione o botão **Adicionar**.


### Tarefa 2: criar um guia estratégico do Microsoft Sentinel

Nesta tarefa, você criará um Aplicativo lógico que será usado como um Guia estratégico no Microsoft Sentinel.

1. No navegador Microsoft Edge, navegue até [Microsoft Sentinel no GitHub](https://github.com/Azure/Azure-Sentinel).

<!--- the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Tenant Email** account provided by your lab hosting provider and then select **Next**.

1. In the **Enter password** dialog box, copy and paste in the **Tenant Password** provided by your lab hosting provider and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace you created earlier.

1. Select the **Community** page under the *Content management* area on the left side of the page.

1. On the right pane, select the **Onboard community content** link. This opens a new tab in the Microsoft Edge Browser for Microsoft Sentinel GitHub content. **Hint:** You might need to scroll right to see the link. Alternatively, follow this link instead: [Microsoft Sentinel on GitHub](https://github.com/Azure/Azure-Sentinel). --->

1. Role a página para baixo e clique na pasta **Soluções**.

1. Em seguida, selecione a pasta **SentinelSOARessentials** e, em seguida, a pasta **Guias estratégicos**.

1. Selecione a pasta **Post-Message-Teams**.

1. Na caixa readme.md, role para baixo até a seção *Implantação rápida*, **Implantar com gatilho de incidente (recomendado)** e clique no botão **Implantar no Azure**.  

1. A Assinatura do Azure deve estar selecionada.

1. Para Grupo de recursos, selecione **Criar novo**, insira *RG-Playbooks* e selecione **OK**.

1. Mantenha **(EUA) Leste dos EUA** como valor padrão para *Região*.

1. Renomeie o *Nome do guia estratégico* para "PostMessageTeams-OnIncident" e selecione **Examinar + criar**.

1. Agora, selecione **Criar**. 

    >**Observação:** aguarde a conclusão da implantação antes de prosseguir para a próxima tarefa.

### Tarefa 3: atualizar um guia estratégico no Microsoft Sentinel

Nesta tarefa, você atualizará o novo guia estratégico criado com as informações de conexão adequadas.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione seu workspace do Microsoft Sentinel.

1. Selecione **Automação** na área *Configuração* e, em seguida, selecione a guia **Guias estratégicos ativos**.

1. Selecione **Atualizar** na barra de comandos, caso não veja nenhum guia estratégico. Você deve ver o guia estratégico criado na etapa anterior com a *variante Gatilho* do **Incidente do Microsoft Sentinel**.

1. Selecione o nome do guia estratégico **PostMessageTeams-OnIncident**.

1. Na página Aplicativo lógico para *PostMessageTeams-OnIncident*, no menu de comando, selecione **Editar**.

    >**Observação:** talvez seja necessário atualizar a página.

1. Selecione o *primeiro* bloco, **Incidente do Microsoft Sentinel (Visualização)**.

1. Selecione o link **Alterar conexão**.

1. Selecione **Adicionar novo** e selecione **Entrar**. Na nova janela, selecione suas credenciais de administrador da assinatura do Azure quando solicitado. A última linha do bloco agora deve ser " Conectado ao seu nome de usuário-administrador".

1. Agora selecione o *segundo* bloco, **Conexões**.

1. Selecione **Adicionar novo** e depois selecione suas credenciais de administrador do Azure quando solicitado. A última linha do bloco agora deve ser " Conectado ao seu nome de usuário-administrador".

1. O bloco agora foi renomeado para **Publicar uma mensagem (V3) (Visualização)**, no final do campo *Equipe*, então selecione o **X** para limpar o conteúdo. O campo é alterado para um menu suspenso com uma listagem das Equipes disponíveis no Microsoft Teams. Selecione **SOC**.

1. Faça o mesmo para o campo *Canal* e selecione o **X** no final do campo para limpar o conteúdo. O campo é alterado para um menu suspenso com uma listagem dos canais das Equipes SOC. Selecione **Novos alertas**.

1. Selecione **Salvar** na barra de comandos. O Aplicativo lógico será usado em um laboratório futuro.

## Prossiga para o Exercício 3
