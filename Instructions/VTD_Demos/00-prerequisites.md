
# Analista de operações de segurança da Microsoft
Guia de preparação do instrutor

## Finalidade

Este documento destina-se aos apresentadores que se preparam para ensinar o Microsoft Virtual Training Day para `Defend Against Threats with Extended Detection and Response` e `Configure Security Operations Using Microsoft Sentinel`. Este material é um subconjunto do curso de certificação SC-200: Analista de operações de segurança da Microsoft.

## Pré-requisitos da demonstração

Os laboratórios deste curso exigem um locatário licenciado do Microsoft 365 E5, bem como uma assinatura do Azure.

* Você pode solicitar Azure Passes do Microsoft Learning para seu próprio benefício.
* Certifique-se de solicitar esses passes pelo menos duas semanas antes de realizar as demonstrações. Depois de receber o passe, você precisará ativá-lo. 
* O Azure Pass funciona efetivamente da mesma forma que a Assinatura de avaliação do Microsoft Azure disponível ao público. Isso significa que há limitações sobre o que você pode fazer com o passe.
* As instruções do laboratório estão presentes no [repositório GitHub do SC-200 Microsoft Learning.](https://github.com/MicrosoftLearning/SC-200T00A-Microsoft-Security-Operations-Analyst/tree/master/Instructions/VTD_Demos/)
* Verifique se o computador que usará para as demonstrações tem o novo navegador Microsoft Edge instalado.

## Ativar o Azure Pass

## Implantar o Defender para Ponto de Extremidade

### Obter suas credenciais do Microsoft 365

Depois de iniciar o laboratório, um locatário de avaliação gratuita será disponibilizado para você acessar no ambiente de laboratório virtual da Microsoft. Esse locatário receberá automaticamente um nome de usuário e uma senha exclusivos. Você deve recuperar esse nome de usuário e senha para poder entrar no Azure e no Microsoft 365 no ambiente de laboratório virtual da Microsoft.

Como esse curso pode ser oferecido por parceiros de aprendizagem que usam qualquer um dos vários provedores de hospedagem de laboratório autorizados, as etapas reais envolvidas para recuperar o ID do locatário associado ao seu locatário podem variar de acordo com o provedor de hospedagem de laboratório. Portanto, seu instrutor fornecerá as instruções necessárias sobre como recuperar essas informações para o seu curso. As informações que você deve observar para uso posterior incluem:

    - **ID do sufixo do locatário.** Essa ID é para as contas onmicrosoft.com que você usará para entrar no Microsoft 365 em todos os laboratórios. Isso está no formato de **{username}@M365xZZZZZZ.onmicrosoft.com**, em que ZZZZZZ é o ID de sufixo de locatário exclusivo fornecido pelo provedor de hospedagem do laboratório. Grave esse valor ZZZZZZ para usar mais tarde. Quando qualquer uma das etapas do laboratório direcioná-lo para entrar em portais do Microsoft 365, você deve inserir o valor ZZZZZZ que obtido aqui.
    - **Senha do locatário.** Essa é a senha da conta de administrador fornecida pelo provedor de hospedagem do laboratório.
    

### Inicializar o Microsoft Defender para Ponto de Extremidade

Nesta tarefa, você executará a inicialização do Microsoft Defender para Ponto de Extremidade.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Edge, vá para o portal do Microsoft 365 Defender em (https://security.microsoft.com).

1. Na caixa de diálogo **Entrar**, copie e cole a conta de email do locatário referente ao nome de usuário do administrador fornecido pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a senha de locatário do administrador fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

No portal **Microsoft 365 Defender**, no menu de navegação, selecione **Início** à esquerda.

    >**Note:** You may need to scroll all the way to the menu top.

1. Na página de **Início** do portal, é exibida a mensagem **Bem-vindo ao Microsoft 365 Defender**.

1. Role para baixo nos blocos até encontrar o bloco denominado **Microsoft 365 Defender** com a mensagem **Ativar o Microsoft 365 Defender.**

    >**Dica:** Deve estar na parte inferior direita dos blocos.

1. Selecione o botão que diz **Ativar novos recursos.**

1. Você verá mensagens dizendo *Carregando e inicializando* exibidas brevemente na parte superior da página e, em seguida, verá uma imagem de uma caneca de café e uma mensagem que diz: **Aguarde! Estamos preparando novos espaços para seus dados e conectando-os.** A conclusão levará aproximadamente 5 minutos. *Deixe a página aberta e certifique-se de que ela conclua, pois ela será necessária para o próximo laboratório.*

    >**Observação:** se a mensagem "Espere! Estamos preparando novos espaços para seus dados e conectando-os" não aparecer, ou a página "Configurações > Microsoft 365 Defender > Conta" for aberta, mas você vir a mensagem "Falha ao carregar o local de armazenamento de dados. Tente novamente mais tarde", selecione "Configurações do serviço de alerta" no menu "Geral" ou vá para o menu de navegação, role para baixo até a seção "Ativos" e selecione "Dispositivos".

1. Quando o novo espaço for concluído com êxito, você verá as configurações gerais do Microsoft 365 Defender para Conta, Notificações por email, Configurações do serviço de alerta, Permissões e funções e API de streaming. Você também verá a **Visualização dos recursos** ativada.

**Observação**: no ambiente de laboratório hospedado, seu local de armazenamento de dados deve estar selecionado para você. Além disso, ele deve estar na área geográfica apropriada para o local onde esse locatário de treinamento é gerenciado. Você ainda pode selecionar a duração da Retenção de dados, mas isso não é necessário.

1. Em **Configurações**, selecione **Pontos de extremidade**.

1. Selecione **Integração** na seção Gerenciamento de dispositivo.

    >**Observação:** você também pode executar a integração de dispositivos na seção **Ativos** da barra de menus à esquerda. Expanda Ativos e selecione Dispositivos. Na página Inventário de dispositivos, com a opção Computadores e dispositivos móveis selecionada, role para baixo até **Dispositivos integrados.** Isso levará você à página **Configurações > Pontos de extremidade**.

1. Na área "1. Integrar um dispositivo", certifique-se de que "Script local (para até 10 dispositivos)" seja exibido no menu suspenso Método de implantação e clique no botão **Baixar pacote de integração**.

1. Extraia o arquivo zip baixado para uma pasta local, como a pasta Documentos.

1. Clique com o botão direito do mouse no arquivo extraído WindowsDefenderATPLocalOnboardingScript.cmd e escolha **Executar como administrador**.  Se você encontrar o Windows SmartScreen, escolha Executar mesmo assim.

**Observação** Por padrão, o arquivo deve estar no diretório c:\users\admin\downloads.
    
1. Responda **S** às perguntas apresentadas pelo script. Quando terminar, você deverá ver uma mensagem na tela de comando que diz algo como "Máquina integrada com sucesso..." 

1. Na página Integração no portal, copie o script do teste de detecção e execute-o em uma janela de comando aberta.  Talvez seja necessário abrir uma nova janela **Administrador: prompt de comando** digitando *CMD* na barra de pesquisa do Windows e optar por **executar como Administrador**.

1. No menu do portal Microsoft 365 Defender, selecione **Inventário de dispositivos**. Agora será possível ver seu dispositivo na lista.

**Observação** Pode levar até 5 minutos para que o dispositivo seja exibido no portal.


### Configurar as funções

Nesta tarefa, você configurará funções para usar em grupos de dispositivos.

1. No portal Microsoft 365 Defender, selecione **Configurações** na barra de menus à esquerda. 

1. Selecione **Pontos de extremidade** e, em seguida, selecione **Funções** na área de permissões.

1. Selecione o botão **Ativar funções**.

1. Selecione **Adicionar item**.

1. Na caixa de diálogo Adicionar função, insira as seguintes informações:

    |Configurações gerais|Valor|
    |---|---|
    |Nome da função|**Suporte de Nível 1**|
    |Permissões|Recursos de Resposta imediata – Avançado|

1. Selecione **Avançar**.

1. Na guia Grupos de usuários atribuídos, selecione **sg-IT** e, em seguida, selecione **Adicionar grupos selecionados**.

1. Selecione **Salvar**.

### Configurar grupos de dispositivos

Nesta tarefa, você configurará grupos de dispositivos que permitem o controle de acesso e a configuração de automação.

1. Selecione **Configurações** na barra de menus à esquerda. 

1. Selecione **Pontos de extremidade** e, na área de permissões, selecione **Grupos de dispositivos**.

1. Selecione **Adicionar grupo de dispositivos**.

1. Na guia Geral, insira as seguintes informações:

    |Configurações gerais|Valor|
    |---|---|
    |O nome do grupo de dispositivos|**Regular**|
    |Nível de automação|Completo – corrija ameaças automaticamente|

1. Selecione **Avançar**.

1. . Na guia Dispositivos, para a condição do sistema operacional, selecione **Windows 10** e selecione **Avançar**.

1. Na guia Visualização dos dispositivos, selecione **Mostrar visualização** para ver a máquina virtual WIN1. Selecione **Avançar**. 
**Dica:** Se você não vir a máquina virtual na lista de visualização, volte e selecione também *Nenhum* para a condição do sistema operacional. Os dados da VM ainda não foram preenchidos.

1. Na guia Acesso do usuário, selecione **sg-IT** e, em seguida, selecione **Adicionar grupos selecionados**

1. Selecione **Concluído**.

1. A configuração do grupo de dispositivos foi alterada. Selecione **Aplicar alterações** para verificar correspondências e recalcular agrupamentos.

1. Você terá dois grupos de dispositivos agora; o grupo "Regular" que você acabou de criar e o grupo "Dispositivos desagrupados (padrão)" com o mesmo nível de correção.

<!--- 
## Deploy sample alerts for Demo in Module 3

In this task, you will load sample security alerts and review the alert details.

1. In the Edge browser, open the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Tenant Email** account provided by your lab hosting provider and then select **Next**.

1. In the **Enter password** dialog box, copy and paste in the **Tenant Password** provided by your lab hosting provider and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Defender*, then select **Microsoft Defender for Cloud**.

1. In the **Getting Started** menu the default selection is **Upgrade**, select or **Skip** for now.

1. Select **Security alerts** in the portal menu.

1. Select **Sample Alerts** from the command bar.

1. In the Create sample alerts (Preview) pane make sure your subscription is selected.  Make sure all sample alerts are selected and select **Create sample alerts**.  

**Note** This may take a few minutes to complete. --->

## Implantar o workspace do Microsoft Sentinel para demonstração no módulo 4

Nesta tarefa, você criará um workspace do Microsoft Sentinel.

 >**Observação:** você precisará ter um Azure Pass ou outra assinatura do Azure ativa para a demonstração a seguir.

1. No navegador Edge, acesse o portal do Azure em https://portal.azure.com.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione **+ Criar**.

1. Depois, selecione **+ Criar um novo workspace**.

**Observação** Primeiro, crie um novo workspace do Log Analytics.

1. Selecione sua Assinatura correta.

1. Selecione o link **Criar novo** para o Grupo de recursos e insira um novo nome de grupo de recursos de sua escolha.

1. Em Detalhes da instância no campo de nome, insira um nome da sua escolha para o workspace do Log Analytics.

**Observação:** esse nome deve ser exclusivo e também será o nome do workspace do Microsoft Sentinel.

1. Selecione uma opção adequada para você.  A região apropriada pode ser padrão ou seu instrutor pode ter orientações específicas sobre qual região selecionar.  

1. Selecione **Examinar + criar**.

1. Selecione **Criar**. Aguarde até que o novo workspace do Log Analytics apareça na lista na página Adicionar Microsoft Sentinel a um workspace.  Isso pode levar alguns minutos.

1. Selecione o workspace recém-criado quando ele aparecer e selecione **Adicionar**.

## Implantar soluções e conectores de dados do Hub de conteúdos para o Microsoft Sentinel

### Tarefa 1: acessar o workspace do Microsoft Sentinel

Nesta tarefa, você acessará seu workspace do Microsoft Sentinel.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. Abra o navegador, pesquise, baixe e instale o novo navegador Microsoft Edge. Inicie o novo navegador Edge.

1. No navegador Edge, acesse o portal do Azure em https://portal.azure.com.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o workspace do Microsoft Sentinel que você criou no laboratório anterior.

### Tarefa 2: usar o conector de dados de Atividade do Azure.

Nesta tarefa, você conectará o conector de dados de *Atividade do Azure*.

1. No menu esquerdo do Microsoft Sentinel, role para baixo até a seção *Gerenciamento de conteúdo* e selecione **Hub de conteúdos**.

1. No *Hub de conteúdo*, procure a solução de **Atividade do Azure** e selecione-a na lista.

1. Na página da solução *Microsoft Defender para Nuvem*, selecione **Instalar**.

1. Quando a instalação for concluída, selecione **Gerenciar**

    >**Observação:** A solução de *Atividade do Azure* instala o conector de dados de *Atividade do Azure*, 12 regras de análise, 14 consultas de busca, 1 pasta de trabalho.

1. Selecione um conector de dados de *Atividade do Azure* e depois clique no botão **Abrir página do conector**.

1. Na área *Configuração*, a guia *Instruções*, role a página para baixo até "2. Conecte suas assinaturas..." e, por fim, selecione **Iniciar assistente de atribuição do Azure Policy>**.

1. Na guia **Básico**, clique no botão de reticências (...) em **Escopo** e selecione sua assinatura "Azure Pass – Sponsorship" na lista suspensa e clique em **Selecionar**.

1. Selecione a guia **Parâmetros** e escolha seu workspace na lista suspensa **Workspace principal do Log Analytics**. Essa ação aplicará a configuração de assinatura para enviar as informações ao workspace do Log Analytics.

1. Selecione a guia **Correção** e marque a caixa de seleção **Criar uma tarefa de correção**. Essa ação aplicará a política a recursos já existentes do Azure.

1. Selecione o botão **Examinar + criar** para examinar a configuração.

1. Selecione **Criar** para concluir.

### Tarefa 3: criar uma máquina virtual do Windows no Azure

Nesta tarefa, você criará uma máquina virtual do Windows no Azure.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Microsoft Edge, acesse o portal do Azure em https://portal.azure.com.

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Selecione **+ Criar um Recurso**. **Dica:** se você já estiver no Portal do Azure, talvez seja necessário selecionar *Microsoft Azure* na barra superior para ir para a página inicial.

1. Na caixa **Pesquisar serviços e marketplace**, insira *Windows 10* e selecione **Microsoft Windows 10** na lista suspensa.

1. Selecione a caixa para **Microsoft Windows 10**.

1. Abra a lista suspensa *Plano* e selecione **Windows 10 Enterprise, versão 22H2**.

1. Selecione **Iniciar com uma configuração predefinida** para continuar.

1. Selecione **Desenvolvimento/Teste** e, em seguida, selecione **Continuar para criar uma VM**.

1. Selecione **Criar novo** para o *Grupo de recursos*, insira `RG-AZWIN01` como Nome e selecione **OK**.

    >**Observação:** esse será um novo grupo de recursos para fins de acompanhamento. 

1. Em *Nome da máquina virtual*, insira `AZWIN01`.

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

### Tarefa 4: conectar uma máquina virtual do Windows do Azure

Nesta tarefa, você conectará uma máquina virtual do Windows do Azure ao Microsoft Sentinel.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o workspace do Microsoft Sentinel que você criou anteriormente.

1. 1. No menu esquerdo do Microsoft Sentinel, role para baixo até a seção *Gerenciamento de conteúdo* e selecione **Hub de conteúdos**.

1. No *Hub de conteúdo*, procure a solução **Eventos de Segurança do Windows** e selecione-a na lista.

1. Na página da solução *Eventos de Segurança do Windows*, selecione **Instalar**.

1. Quando a instalação for concluída, selecione **Gerenciar**

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

### Tarefa 5: instalar o Azure Arc e conectar um servidor local

Nesta tarefa, você instalará o Azure Arc em um servidor local para facilitar a integração.

>**Importante:** As próximas etapas são feitas em uma máquina diferente daquela que você estava trabalhando anteriormente. Procure as referências de nome da máquina virtual.

1. Faça logon na máquina virtual **WINServer** como Administrador com a senha: **Passw0rd!** se necessário.  

1. Abra o navegador Microsoft Edge e acesse o portal do Azure em https://portal.azure.com.

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Arc* e selecione **Azure Arc**.

1. No painel de navegação, em **Infraestrutura** , selecione **Máquinas**

1. Selecione **+ Adicionar/Criar** e, em seguida, selecione **Adicionar uma máquina**.

1. Na seção "Adicionar servidor único", selecione **Gerar script**.

1. Leia a guia *Pré-requisitos* e selecione **Avançar** para continuar.

1. Na página *Adicionar um servidor com o Azure Arc*, selecione o grupo de recursos criado anteriormente em *Detalhes do projeto*. **Dica:** *RG-Defender*

    >**Observação:** se você ainda não tiver criado um grupo de recursos, abra outra guia, crie o grupo de recursos e comece de novo.

1. Revise as opções de *Detalhes do servidor* e do *Método de conectividade*. Mantenha os valores padrão e selecione **Avançar** para acessar a guia Marcas.

1. Revise as marcas padrão disponíveis. Selecione **Avançar** para acessar a guia Baixar e executar script.

1. Role a página para baixo e clique no botão **Download**. **Dica:** se o seu navegador bloquear o download, execute uma ação no navegador para permiti-lo. No Navegador Edge, clique no botão de reticências (...) se necessário e depois selecione **Manter**.

1. Clique com o botão direito do mouse no botão Iniciar do Windows e selecione **Windows PowerShell (Administrador)**.

1. Insira *Administrador* em "Nome de usuário" e *Passw0rd!* em "Senha" se você receber um prompt do UAC.

1. Insira: cd C:\Users\Administrator\Downloads

    >**Importante:** Se não tiver esse diretório, provavelmente significa que você está na máquina errada. Volte para o início da Tarefa 4, mude para WINServer e comece de novo.

1. Insira *Set-ExecutionPolicy -ExecutionPolicy Unrestricted* e pressione Enter.

1. Insira **A** para Sim para todos e pressione Enter.

1. Insira *.\OnboardingScript.ps1* e pressione Enter.  

    >**Importante:** se você receber o erro *"O termo .\OnboardingScript.ps1 não é reconhecido..."*, verifique se está executando as etapas da Tarefa 4 na máquina virtual WINServer. Outro problema pode ser que o nome do arquivo foi alterado devido a vários downloads, procure por *".\OnboardingScript (1).ps1"* ou outros números de arquivo no diretório em execução.

1. Insira **R** para Executar uma vez e pressione Enter (isso pode levar alguns minutos).

1. O processo de instalação abrirá uma nova guia do navegador Edge para autenticar o agente do Azure Arc. Selecione sua conta de administrador, aguarde a mensagem "Autenticação concluída" e volte para a janela do Windows PowerShell.

1. Quando a instalação for concluída, volte para a página do portal do Azure onde você baixou o script e selecione **Fechar**. Feche a página **Adicionar servidores com o Azure Arc** para voltar à página **Máquinas** do Azure Arc.

1. Selecione **Atualizar** até que o nome do servidor WINServer apareça e o Status seja *Conectado*.

    >**Observação:** este comando levará alguns minutos.


### Tarefa 6: proteger um servidor local

Nesta tarefa, você adicionará uma máquina virtual Windows que não seja do Azure conectada ao Azure Arc ao Microsoft Sentinel.  

   >**Observação:** o conector de dados *Eventos de Segurança do Windows via AMA* exige o Azure Arc para dispositivos que não sejam do Azure.

1. Verifique se você está na configuração do conector de dados *Eventos de Segurança do Windows via AMA* em seu workspace do Microsoft Sentinel.

1. Na guia **Instruções**, na seção *Configuração*, edite a *regra de coleta de dados* **AZWINDCR** selecionando o ícone de *lápis*.

1. Selecione **Avançar: Recursos** e **+Adicionar recurso(s).**

1. Expanda o Grupo de recursos criado e selecione **WINServer**.

    >**Importante:** Se você não vir o WINServer, consulte o Roteiro de aprendizagem 3, Exercício 1 e Tarefa 4 onde você instalou o Azure Arc neste servidor.

1. Selecione **Aplicar**.

1. Selecione **Avançar: Coletar**, depois **Avançar: Examinar + criar**.

1. Depois que a mensagem *Validação aprovada* for exibida, selecione **Criar**.


<!--- ### Task 4: Connect the Microsoft Defender for Cloud connector.

In this task, you will connect the Microsoft Defender for Cloud connector.

1. From the Data Connectors tab, select the **Microsoft Defender for Cloud** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Review the Connecting Options. Don't connect. This is for informational purposes only.

### Task 5: Connect the Microsoft Defender for Cloud Apps connector.

In this task, you will connect theMicrosoft Defender for Cloud Apps connector.

1. From the Data Connectors Tab, select the **Microsoft Defender for Cloud Apps** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. In the **Instructions** tab in the **Configuration** section, select **Alerts** and then select **Apply Changes**.

### Task 6: Connect the Microsoft Defender for Office 365 connector.

In this task, you will connect the Microsoft Defender for Office 365 connector.

1. From the Data Connectors tab, select the **Microsoft Defender for Office 365** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Select **Connect**.

### Task 7: Connect the Microsoft Defender for Identity connector.

In this task, you will connect the Microsoft Defender for Identity connector.

1. From the Data Connectors Tab, select the **Microsoft Defender for Identity** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Review the Connecting Options. Don't connect. This is for informational purposes only.

### Task 8: Connect the Microsoft Defender for Endpoint connector.

In this task, you will connect the Microsoft Defender for Endpoint connector.

1. From the Data Connectors Tab, select the **Microsoft Defender for Endpoint** connector from the list.

1. Select Open connector page on the connector information blade.

1. Select **Connect**.

### Task 9: Connect the Microsoft 365 Defender connector.

In this task, you will connect the Microsoft 365 Defender connector.

1. From the Data Connectors Tab, select the **Microsoft 365 Defender** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. Select all the checkboxes for Microsoft Defender for Endpoint.

1. Select **Apply Changes**. 

### Task 3: Connect a non-Azure Windows Machine.

In this task, you will connect a non-Azure Windows virtual machine to Microsoft Sentinel.

1. Login to WIN2 virtual machine as Admin with the password: **Pa55w.rd**.  

1. Open the browser, search for, download, and install the new Microsoft Edge browser. Start the new Edge browser.

1. Open a browser and log into the Azure Portal at https://portal.azure.com with your credentials.

1. In the Search bar of the Azure Portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace.

1. From the Data Connectors tab, select the **Security Events via Legacy Agent** connector from the list.

1. Select **Open connector page** on the connector information blade.

1. In the Select which events to stream area, select **All Events**, then select **Apply Changes**.

1. Select the **Install agent on a non-Azure Windows  Machine**.

**Note:** The instructions for Install agent on a Windows Virtual Machine and Install agent on a non-Azure Windows Machine may be reversed. The links take you to the proper location even with the reversed text.

1. Select **Download & install agent for non-Azure Windows machines**. 

1. Select the link for **Download Windows Agent (64 bit)**.

1. Run the .exe file that is downloaded and confirm and User Account Control prompt that may appear.

1. Select **Next** on the Welcome dialog.

1. Select **I Agree** on the Microsoft Software License Terms page.  On the Destination prompt select **Next**.

1. On the Agent Setup Options prompt, select **Connect the agent to Azure Log Analytics (OMS)** option, then select **Next**.

1. In the browser, copy the **Workspace ID** from the Agents Management page and paste into the Workspace ID in the dialog. 

1. In the browser, copy the **Primary key** from the Agents Management page and paste into the Primary key in the dialog. 

1. Select **Next**.

1. Select **Next** on the Microsoft Update page.

2. Then select **Install**.

### Task 4: Install and collect Sysmon logs.

In this task, you will install and collect Sysmon logs.

You should still be connected to the WIN2 virtual machine.  The following instructions will install Sysmon with the default configuration.  You should research community based configurations for Sysmon to be used on production machines.

1. In the browser, go to https://docs.microsoft.com/sysinternals/downloads/sysmon

1. Download Sysmon from the page by select **Download Sysmon**.

1. Open the downloaded file and extract the files to a new directory c:\sysmon

1. In the Windows Taskbar for WIN2 search box, enter *command*.  The search results will show command prompt app.  Right-click on the command prompt app and select **Run as Administrator**.  Confirm any User Account Control prompts that appear.

1. Enter *cd \sysmon*

1. type *notepad sysmon.xml* to create a new file.

1. Open a tab in the browser and navigate to: https://github.com/SwiftOnSecurity/sysmon-config/blob/master/sysmonconfig-export.xml

1. Copy the contents of that file from Github to the sysmon.xml notepad file you just created and save the file.

1. In the command prompt type the following and press enter:
    sysmon.exe -accepteula -i sysmon.xml

1. In the browser, navigate to the Azure portal at https://portal.azure.com 

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. In Microsoft Sentinel, select **Settings** from the Configuration area and then select **Workspace settings** tab.

1. Make sure your Microsoft Sentinel Workspace is selected.

1. Select **Agents configuration** in Settings.

1. Select the **Windows Event logs** tab.

1. Select **Add windows event log** button.

1. Enter **Microsoft-Windows-Sysmon/Operational** in the Log name field.

1. Select **Apply**. --->

## Conduzir ataques

### Tarefa 1: atacar o Windows configurado com o Defender para Ponto de Extremidade

Nesta tarefa, você realizará ataques em um host com o Microsoft Defender para Ponto de Extremidade configurado.

1. Faça logon na máquina virtual `WIN1` como Administrador com a senha: **Pa55w.rd**.  

1. Em Pesquisa da barra de tarefas, insira *Comando*.  O prompt de comando será exibido nos resultados da pesquisa.  Clique com o botão direito do mouse no prompt de comando e selecione **Executar como administrador**. Confirme todos os prompts do Controle de conta de usuário exibidos.

1. No prompt de comando, insira o comando em cada linha pressionando a tecla Enter após cada linha:

    ```CommandPrompt
    cd \
    mkdir temp
    cd temp
    ```

1. Copie e execute este comando:

    ```CommandPrompt
    REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "SOC Test" /t REG_SZ /F /D "C:\temp\startup.bat"
    ```

### Tarefa 2: criar ataque C2 (comando e controle)

1. Faça logon na máquina virtual `WIN1` como Administrador com a senha: **Pa55w.rd**.  

1. Em Pesquisa da barra de tarefas, insira *Comando*.  O prompt de comando será exibido nos resultados da pesquisa.  Clique com o botão direito do mouse no prompt de comando e selecione **Executar como administrador**. Confirme todos os prompts do Controle de conta de usuário exibidos.

1. Ataque 2 – Copie e execute este comando:

    ```CommandPrompt
    notepad c2.ps1
    ```

Selecione **Sim** para criar um novo arquivo e copie o seguinte script do PowerShell em c2.ps1 e selecione **Salvar**.

>**Observação:** Colar na Máquina Virtual pode ter um comprimento limitado.  Cole isso em três seções para garantir que todo o script seja colado na Máquina virtual.  Certifique-se de que o script tenha a mesma aparência nestas instruções dentro do arquivo c2.ps1 do Bloco de notas.

    ```PowerShell
    
    param(
        [string]$Domain = "microsoft.com",
        [string]$Subdomain = "subdomain",
        [string]$Sub2domain = "sub2domain",
        [string]$Sub3domain = "sub3domain",
        [string]$QueryType = "TXT",
            [int]$C2Interval = 8,
            [int]$C2Jitter = 20,
            [int]$RunTime = 240
    )
    
    
    $RunStart = Get-Date
    $RunEnd = $RunStart.addminutes($RunTime)
    
    $x2 = 1
    $x3 = 1 
    Do {
        $TimeNow = Get-Date
        Resolve-DnsName -type $QueryType $Subdomain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
    
        if ($x2 -eq 3 )
        {
            Resolve-DnsName -type $QueryType $Sub2domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
            
            $x2 = 1
    
        }
        else
        {
            $x2 = $x2 + 1
        }
        
        if ($x3 -eq 7 )
        {
    
            Resolve-DnsName -type $QueryType $Sub3domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
    
            $x3 = 1
            
        }
        else
        {
            $x3 = $x3 + 1
        }
    
    
        $Jitter = ((Get-Random -Minimum -$C2Jitter -Maximum $C2Jitter) / 100 + 1) +$C2Interval
        Start-Sleep -Seconds $Jitter
    }
    Until ($TimeNow -ge $RunEnd)
    ```

No prompt de comando, insira o comando em cada linha pressionando a tecla Enter após cada linha:

    ```PowerShell
    .\c2.ps1
    ```

>**Observação:** você verá erros de resolução. Isso é normal.
Deixe esse script command/powershell ser executado em segundo plano. Não feche a janela.  O comando precisa gerar entradas de log por algumas horas.  Você pode prosseguir para a próxima tarefa e os próximos exercícios enquanto este script é executado.  Os dados criados por essa tarefa serão usados no laboratório de Busca de ameaças posteriormente.  Este processo não criará quantidades substanciais de dados ou processamento.

### Tarefa 2: atacar o Windows configurado com o Agente do Azure Monitor (AMA)

Nesta tarefa, você realizará ataques em um host com o conector Eventos de Segurança configurado e o Sysmon configurado.

1. Selecione a máquina virtual `AZWIN01` que você criou anteriormente.  

1. No menu à esquerda, role para baixo até **Operações** e selecione **Executar comando**

1. No painel **Executar comando**, selecione **RunPowerShellScript**

1. Copie os comandos abaixo para simular a criação de uma conta de administrador no formulário `PowerShell Script` e selecione **Executar**

    ```CommandPrompt
    net user theusernametoadd /add
    net user theusernametoadd ThePassword1!
    net localgroup administrators theusernametoadd /add
    ```

    >**Observação**: certifique-se de que há apenas um comando por linha e você pode executar novamente os comandos alterando o nome de usuário.

1. Na janela `Output`, você deve ver `The command completed successfully` três vezes
