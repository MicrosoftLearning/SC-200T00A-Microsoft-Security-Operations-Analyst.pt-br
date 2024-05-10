---
lab:
  title: 'Exercício 1: habilitar o Microsoft Defender para Nuvem'
  module: Learning Path 3 - Mitigate threats using Microsoft Defender for Cloud
---

# Roteiro de aprendizagem 3, Laboratório 1, Exercício 1: habilitar o Microsoft Defender para Nuvem

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod3_L1_Ex1.png)

Você é um analista de operações de segurança e trabalha em uma empresa que está implementando a proteção de cargas de trabalho de nuvem com o Microsoft Defender para Nuvem.  Neste laboratório, você habilitará o Microsoft Defender para Nuvem.

>**Observação:** uma **[simulação de laboratório interativa](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Enable%20Microsoft%20Defender%20for%20Cloud)** está disponível e permite que você clique neste laboratório no seu próprio ritmo. Você pode encontrar pequenas diferenças entre a simulação interativa e o laboratório hospedado, mas os principais conceitos e ideias que estão sendo demonstrados são os mesmos. 


### Tarefa 1: acessar o portal do Azure e configurar uma assinatura

Nesta tarefa, você configurará uma assinatura do Azure necessária para concluir este laboratório e laboratórios futuros.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.  

1. Abra o navegador Microsoft Edge ou uma nova guia, caso ela já estiver aberta.

1. No navegador Edge, acesse o portal do Azure em (https://portal.azure.com).

1. Na caixa de diálogo **Entrar**, copie e cole a conta de email do locatário referente ao nome de usuário do administrador fornecido pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a senha de locatário do administrador fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de pesquisa do portal do Azure, digite *Assinatura* e selecione **Assinaturas**. 

1. Selecione a assinatura *"Azure Pass – Sponsorship"* mostrada (ou nome equivalente no idioma selecionado).

    >**Observação:** se a assinatura não for exibida, pergunte ao seu instrutor sobre como criar a assinatura do Azure com suas credenciais de usuário administrador de locatário. **Observação:** o processo de criação da assinatura pode levar até 10 minutos. 

1. Selecione **Controle de acesso (IAM)** e, em seguida, selecione **Adicionar atribuição de função** na caixa *Conceder acesso a este recurso*.

1. Selecione a guia **Funções de administrador privilegiadas** e, em seguida, selecione **Proprietário**. Selecione **Avançar** para continuar.

1. Na guia *Membros*, selecione **+ Selecionar membros** e depois a conta de **Administrador do MOD**. Em seguida, clique em **Selecionar** para continuar.

    >**Observação:** Se a guia **Condições** mostrar um ponto vermelho, selecione **Avançar** e escolha **Não restrito**, se for exibido o tipo *Delegação*, ou selecione **Permitir que o usuário atribua todas as funções (altamente privilegiado)**, se for exibida a opção *O que o usuário pode fazer*.

1. Clique em **Examinar + atribuir** duas vezes para atribuir a função de proprietário à sua conta de administrador.

>**Importante:** esses laboratórios foram projetados para usar menos de USD 10 em serviços do Azure durante a aula.


### Tarefa 2: criar um workspace do Log Analytics

Nesta tarefa, você criará um workspace do Log Analytics para uso com o Microsoft Defender para Nuvem.

1. Na barra de pesquisa do portal do Azure, digite *workspace do Log Analytics* e selecione o mesmo nome de serviço.

1. Na barra de comandos, selecione **+Criar**.

1. Selecione **Criar novo** para o Grupo de recursos.

1. Insira *RG-Defender* e selecione **OK**.

1. Para o Nome, insira algo exclusivo como: *uniquenameDefender*.

1. Selecione **Examinar + criar**.

1. Quando a validação do workspace for aprovada, selecione **Criar**. Aguarde até que o novo workspace seja provisionado, o que pode levar alguns minutos.


### Tarefa 3: habilitar o Microsoft Defender para Nuvem

Neste tarefa, você habilitará e configurará o Microsoft Defender para Nuvem.

1. Na barra de pesquisa do portal do Azure, digite *Defender* e selecione **Microsoft Defender para Nuvem**.

1. Na página **Introdução**, na guia **Upgrade**, certifique-se de que a sua assinatura esteja selecionada e, em seguida, clique no botão **Fazer upgrade** na parte inferior da página. Aguarde até que a notificação *A avaliação começou* apareça, o que levará cerca de 2 minutos. 

    >**Dica:** você pode clicar no botão de sino na barra superior para revisar suas notificações do portal do Azure.

    >**Observação:** se você vir o erro *"Não foi possível iniciar a avaliação do Azure Defender na assinatura"*, prossiga para as próximas etapas para habilitar todos os planos do Defender na Etapa 5.

1. No menu esquerdo do Microsoft Defender para Nuvem, em Gerenciamento, selecione **Configurações do ambiente**.

1. Selecione a assinatura **"Azure Pass – Sponsorship"** (ou o nome equivalente no seu idioma). 

1. Analise os recursos do Azure que agora estão protegidos com os planos do Defender para Nuvem.

    >**Importante:** se todos os planos do Defender estiverem *desativados*, selecione **Habilitar todos os planos** e clique em **Salvar**. Aguarde até que a notificação *"O planejamento de recursos na assinatura do Azure Pass foi salvo com êxito!"* seja exibida.

1. Selecione a guia **Configurações e monitoramento** na área Configurações (ao lado de Salvar).

1. Revise as extensões de monitoramento. Elas incluem configurações para Máquinas virtuais, Contêineres e Contas de armazenamento. Feche a página "Configurações e monitoramento" selecionando "X" no canto superior direito da página.

1. Feche a página de configurações selecionando o "X" no canto superior direito da página para voltar às **Configurações do ambiente** e selecione o ">" à esquerda da sua assinatura.

1. Selecione o workspace do Log Analytics *uniquenameDefender* que você criou anteriormente para analisar as opções e os preços disponíveis.

1. Selecione **Habilitar todos os planos** (à direita de Selecionar plano Defender) e, em seguida, selecione **Salvar**. Aguarde até que a notificação *"Plano do Microsoft Defender para workspace uniquenameDefender foram salvos com êxito!"* seja exibida.

    >**Observação:** se a página não for exibida, atualize o navegador Edge e tente novamente.

1. Feche a página de planos do Defender selecionando o "X" no canto superior direito da página para voltar às **Configurações do ambiente**


### Tarefa 4: instalar o Azure Arc em um servidor local

Nesta tarefa, você instalará o Azure Arc em um servidor local para facilitar a integração.

>**Importante:** As próximas etapas são feitas em uma máquina diferente daquela que você estava trabalhando anteriormente. Procure as referências de nome da máquina virtual.

1. Faça logon na máquina virtual **WINServer** como Administrador com a senha: **Passw0rd!** se necessário.  

1. Abra o navegador Microsoft Edge e acesse o portal do Azure em https://portal.azure.com.

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Arc* e selecione **Azure Arc**.

1. No painel de navegação em **recursos do Azure Arc** selecione **Computadores**

1. Selecione **+ Adicionar/Criar** e, em seguida, selecione **Adicionar uma máquina**.

1. Na seção "Adicionar servidor único", selecione **Gerar script**.

    <!--- 1. Read through the *Prerequisites* tab and then select **Next** to continue.--->

1. Na página *Adicionar um servidor com o Azure Arc*, selecione o grupo de recursos criado anteriormente em *Detalhes do projeto*. **Dica:** *RG-Defender*

    >**Observação:** se você ainda não tiver criado um grupo de recursos, abra outra guia, crie o grupo de recursos e comece de novo.

1. Em *Região*, selecione **(EUA) Leste dos EUA** na lista suspensa.

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


### Tarefa 5: proteger um servidor local

Nesta tarefa, você instalará manualmente o *Agente do Azure Monitor* adicionando uma *Regra de coleta de dados (DCR)* na máquina virtual **WINServer**.

1. Vá para **Microsoft Defender para Nuvem** e selecione a página **Introdução** no menu esquerdo.

1. Selecione a guia **Introdução**.

1. Role para baixo e selecione **Configurar** na seção *Adicionar servidores que não sejam do Azure*.

1. Selecione **Upgrade** ao lado do workspace criado anteriormente. Isso pode levar alguns minutos, então aguarde até que você veja a notificação *"Plano do Microsoft Defender para workspace uniquenameDefender foi salvo com êxito!"*.

1. Selecione **+ Adicionar servidores** ao lado do workspace criado anteriormente.

1. Selecione **Regras de coleta de dados**

1. Selecione **+ Criar**.

1. Insira **WINServer** para Nome da regra.

1. Selecione sua assinatura *Azure Pass – Sponsorship* e selecione um grupo de recursos. **Dica:** *RG-Defender*

1. Você pode manter a região padrão *Leste dos EUA* ou selecionar outro local preferencial.

1. Selecione o botão de opção do **Windows** para *Tipo de plataforma* e selecione **Avançar: Recursos**.

1. Na guia **Recursos**, selecione **+ Adicionar recursos**.

1. Na página **Selecionar um escopo**, expanda a coluna *Escopo* para **RG-Defender** (ou o Grupo de recursos criado), selecione **WINServer** e, em seguida, clique em **Aplicar**.

    >**Observação:** talvez seja necessário definir o filtro de coluna para *Tipo de recurso* como *Server-Azure Arc* se o **WINServer** não for exibido.

1. Selecione **Avançar: Coletar e entregar**

1. Na guia **Coletar e entregar**, selecione **+ Adicionar fonte de dados**

1. Na página **Adicionar uma fonte de dados**, selecione **Contadores de desempenho** em *Tipo de fonte de dados*.

    >**Observação:** para a finalidade deste laboratório, você pode selecionar *Logs de eventos do Windows*. Essas seleções podem ser revisadas posteriormente.

1. Clique na guia **Destino**

1. Selecione **Logs do Azure Monitor** no menu suspenso **Tipo de destino**

1. Selecione sua assinatura do *Azure Pass – Sponsorship* na lista suspensa **Assinatura**

1. Selecione o nome do workspace **Dica:** *RG-Defender* do menu suspenso da **conta ou do namespace**

1.  Selecione **Adicionar fonte de dados** e depois **Examinar + criar**

1. Depois que a mensagem *Validação aprovada* for exibida, selecione **Criar**.

1. A criação da **Regra de coleta de dados** inicia a instalação da extensão *AzureMonitorWindowsAgent* no **WINServer**.

1. Quando a criação da *Regra de coleta de dados* for concluída, insira **WINServer** na barra de pesquisa *Pesquisar recursos, serviços e documentos* e selecione **WINServer** em *Recursos*.

1. No **WINServer**, role para baixo pelo menu esquerdo até *Configurações* e *Extensões*.

1. O **AzureMonitorWindowsAgent** deve ser listado com um *Status* de **Bem-sucedido**.

1. Você pode passar para o próximo laboratório e retornar mais tarde para revisar a seção **Inventário** do **Microsoft Defender para Nuvem** para verificar se o **WINServer** está incluído.

## Prossiga para o Exercício 2
