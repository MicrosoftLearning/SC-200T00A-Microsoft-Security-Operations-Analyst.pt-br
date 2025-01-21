---
lab:
  title: 'Exercício 2: conectar dispositivos Windows ao Microsoft Sentinel usando conectores de dados'
  module: Learning Path 8 - Connect logs to Microsoft Sentinel
---

# Roteiro de aprendizagem 8 — Laboratório 1 — Exercício 2 — Conectar dispositivos Windows ao Microsoft Sentinel usando conectores de dados

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex2.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você deve saber como conectar os dados de log de várias fontes de dados na organização. A próxima fonte de dados são máquinas virtuais do Windows dentro e fora do Azure, como ambientes locais ou outras nuvens públicas.

>**Importante:** os exercícios de laboratório para o Roteiro de Aprendizagem 8 estão em um ambiente *independente*. Se você sair do laboratório antes de concluí-lo, será necessário executar as configurações novamente.

### Tempo estimado para concluir este laboratório: 30 minutos

### Tarefa 1: criar uma máquina virtual do Windows no Azure

Nesta tarefa, você criará uma máquina virtual do Windows no Azure.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Microsoft Edge, acesse o portal do Azure em <https://portal.azure.com>.

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Selecione **+ Criar um Recurso**. **Dica:** se você já estiver no Portal do Azure, talvez seja necessário selecionar *Microsoft Azure* na barra superior para ir para a página inicial.

1. Na caixa **Pesquisar serviços e marketplace**, insira *Windows 10* e selecione **Microsoft Windows 10** na lista suspensa.

1. Selecione a caixa para **Microsoft Windows 10**.

1. Abra a lista suspensa *Plano* e selecione **Windows 10 Enterprise, versão 22H2**.

1. Selecione **Iniciar com uma configuração predefinida** para continuar.

1. Selecione **Desenvolvimento/Teste** e, em seguida, selecione **Continuar para criar uma VM**.

1. Selecione **Criar novo** para o *Grupo de recursos*, insira RG-AZWIN01 como Nome e selecione **OK**.

    >**Observação:** esse será um novo grupo de recursos para fins de acompanhamento. 

1. Em *Nome da máquina virtual*, insira AZWIN01.

1. Mantenha **(EUA) Leste dos EUA** como valor padrão para *Região*.

1. Role para baixo e revise a *imagem* da máquina virtual. Se ele estiver vazio, selecione **Windows 10 Enterprise, versão 22H2**.

1. Revise o *Tamanho* da máquina virtual. Se ele estiver vazio, selecione **Ver todos os tamanhos**, escolha o primeiro tamanho de VM em *Mais usado pelos usuários do Azure* e clique em **Selecionar**.

    >**Observação:** se você vir a mensagem *Esta imagem não tem suporte para Gerenciamento automatizado do Azure. Para desabilitar esse recurso, navegue até a guia Gerenciamento. Caso contrário, selecione uma imagem com suporte.* Vá para a guia Gerenciamento e desabilite "Gerenciamento automatizado". O processo de criação progredirá depois.

1. Role para baixo e insira um *Nome de usuário* de sua escolha. **Dica:** Evite palavras reservadas como "admin" (administrador) ou "root" (raiz).

1. Insira uma *senha* de sua escolha. **Dica:** pode ser mais fácil reutilizar sua senha de locatário. Ele pode ser encontrado na guia Recursos.

1. Role para baixo até a parte inferior da página e marque a caixa de seleção abaixo de *Licenciamento* para confirmar que você tem a licença qualificada.

1. Selecione **Examinar + criar** e aguarde até que a validação seja aprovada.

    >**Observação:** se houver uma falha de validação de *Sistema de rede*, selecione essa guia, revise seu conteúdo e depois selecione **Examinar + criar** novamente.

1. Selecione **Criar**. Aguarde até que o recurso seja criado, o que pode levar alguns minutos.

<!--- ### Task 2: Install Azure Arc on an On-Premises Server

In this task, you install Azure Arc on an on-premises server to make onboarding easier.

>**Important:** The next steps are done in a different machine than the one you were previously working. Look for the Virtual Machine name references.

1. Log in to **WINServer** virtual machine as Administrator with the password: **Passw0rd!** if necessary.  

1. Open the Microsoft Edge browser and navigate to the Azure portal at <https://portal.azure.com>.

1. In the **Sign in** dialog box, copy, and paste in the **Tenant Email** account provided by your lab hosting provider and then select **Next**.

1. In the **Enter password** dialog box, copy, and paste in the **Tenant Password** provided by your lab hosting provider and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Arc*, then select **Azure Arc**.

1. In the navigation pane under **Azure Arc resources** select **Machines**

1. Select **+ Add/Create**, then select **Add a machine**.

1. Select **Generate script** from the "Add a single server" section.

1. In the *Add a server with Azure Arc* page, select the Resource group you created earlier under *Project details*. **Hint:** *RG-Defender*

    >**Note:** If you haven't already created a resource group, open another tab and create the resource group and start over.

1. For *Region*, select **(US) East Us** from the drop-down list.

1. Review the *Server details* and *Connectivity method* options. Keep the default values and select **Next** to get to the Tags tab.

1. Review the default available tags. Select **Next** to get to the Download and run script tab.

1. Scroll down and select the **Download** button. **Hint:** if your browser blocks the download, take action in the browser to allow it. In Microsoft Edge Browser, select the ellipsis button (...) if needed and then select **Keep**.

1. Right-click the Windows Start button and select **Windows PowerShell (Admin)**.

1. Enter *Administrator* for "Username" and *Passw0rd!* for "Password" if you get a UAC prompt.

1. Enter: cd C:\Users\Administrator\Downloads

    >**Important:** If you do not have this directory, most likely means that you are in the wrong machine. Go back to the beginning of Task 4 and change to WINServer and start over.

1. Type *Set-ExecutionPolicy -ExecutionPolicy Unrestricted* and press enter.

1. Enter **A** for Yes to All and press enter.

1. Type *.\OnboardingScript.ps1* and press enter.  

    >**Important:** If you get the error *"The term .\OnboardingScript.ps1 is not recognized..."*, make sure you are doing the steps for Task 4 in the WINServer virtual machine. Other issue might be that the name of the file changed due to multiple downloads, search for *".\OnboardingScript (1).ps1"* or other file numbers in the running directory.

1. Enter **R** to Run once and press enter (this may take a couple minutes).

1. The setup process opens a new Microsoft Edge browser tab to authenticate the Azure Arc agent. Select your admin account, wait for the message "Authentication complete" and then go back to the Windows PowerShell window.

1. When the installation finishes, go back to the Azure portal page where you downloaded the script and select **Close**. Close the **Add servers with Azure Arc** to go back to the Azure Arc **Machines** page.

1. Select **Refresh** until WINServer server name appears and the Status is *Connected*.

    >**Note:** This could take a couple of minutes. --->

### Tarefa 2: conectar uma máquina virtual do Windows do Azure

Nesta tarefa, você conectará uma máquina virtual do Windows do Azure ao Microsoft Sentinel.

>**Observação:** o Microsoft Sentinel foi pré-implantado em sua assinatura do Azure com o nome **defenderWorkspace** e as soluções necessárias do *Hub de Conteúdo* foram instaladas.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o **defenderWorkspace** do Microsoft Sentinel.

1. No menu de navegação à esquerda do Microsoft Sentinel, role para baixo até a seção *Gerenciamento de conteúdo* e selecione **Hub de conteúdo**.

1. No *Hub de conteúdo*, procure a solução **Eventos de Segurança do Windows** e selecione-a na lista.

1. Na página da solução *Eventos de Segurança do Windows*, selecione **Gerenciar**.

    >**Observação:** A solução *Eventos de Segurança do Windows* instala os conectores de dados *Eventos de Segurança do Windows via AMA* e *Eventos de Segurança via agente herdado*. Mais 2 pastas de trabalho, 20 regras de análise e 43 consultas de busca.

1. Selecione o conector de dados *Eventos de Segurança do Windows via AMA* e selecione **Abrir página do conector** na folha de informações do conector.

1. Na seção *Configuração*, na guia *Instruções*, selecione a opção **Criar regra de coleta de dados**.

1. Insira **AZWINDCR** para Nome da regra e depois selecione **Avançar: Recursos**.

1. Selecione **+Adicionar recurso(s)** para selecionar a Máquina Virtual que criamos.

1. Expanda **RG-AZWIN01** e selecione **AZWIN01**.

1. Selecione **Aplicar** e depois **Avançar: Coletar**.

1. Revise a opção de coleta diferente de Evento de Segurança. Manter *Todos os Eventos de Segurança* e selecione **Avançar: Examinar + criar**.

1. Selecione **Criar** para salvar uma regra de coleta de dados.

1. Aguarde um minuto e selecione **Atualizar** para ver a nova regra de coleta de dados listada.

### Tarefa 4: Conectar uma máquina Windows que não seja do Azure

Nesta tarefa, você adicionará uma máquina virtual Windows que não seja do Azure conectada ao Azure Arc ao Microsoft Sentinel.  

   >**Observação:** o conector de dados *Eventos de Segurança do Windows via AMA* exige o Azure Arc para dispositivos que não sejam do Azure.

1. Verifique se você está na configuração do conector de dados *Eventos de Segurança do Windows via AMA* em seu workspace do Microsoft Sentinel.

1. Na guia **Instruções**, na seção *Configuração*, edite a *regra de coleta de dados* **AZWINDCR** selecionando o ícone de *lápis*.

1. Selecione **Avançar: Recursos** e expanda sua *Assinatura* em *Escopo* na guia *Recursos*.

    >**Dica:** Você pode expandir toda a hierarquia *Escopo* selecionando o ">" antes da coluna *Escopo*.

1. Expanda o **RG-Defender** (ou o Grupo de recursos que você criou) e selecione **WINServer**.

    >**Importante:** Se você não vir o WINServer, consulte o Roteiro de aprendizagem 3, Exercício 1 e Tarefa 4 onde você instalou o Azure Arc neste servidor.

1. Selecione **Aplicar**.

1. Selecione **Avançar: Coletar**, depois **Avançar: Examinar + criar**.

1. Depois que a mensagem *Validação aprovada* for exibida, selecione **Criar**.

## Prossiga para o Exercício 3
