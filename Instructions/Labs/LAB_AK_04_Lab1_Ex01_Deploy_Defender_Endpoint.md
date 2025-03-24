---
lab:
  title: 'Exercício 1: implantar o Microsoft Defender para Ponto de Extremidade'
  module: Learning Path 4 - Mitigate threats using Microsoft Defender for Endpoint
---

# Roteiro de aprendizagem 4 – Laboratório 1 – Exercício 1 – Implantar o Microsoft Defender para Ponto de Extremidade

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod2_L1_Ex1.png)

Você é analista de operações de segurança e trabalha em uma empresa que está implantando o Microsoft Defender para Ponto de Extremidade. Seu gerente planeja integrar alguns dispositivos para fornecer informações sobre as alterações necessárias nos procedimentos de resposta da equipe de Operações de segurança (SecOps).

Você começa inicializando o ambiente do Defender para Ponto de Extremidade. Em seguida, integre os dispositivos iniciais para sua implantação executando o script de integração nos dispositivos. Configure a segurança para o ambiente. Por último, crie grupos de dispositivos e atribua os dispositivos apropriados.

>**Importante:** as máquinas virtuais de laboratório são usadas em diferentes módulos. SALVE suas máquinas virtuais. Se você sair do laboratório sem salvar, será necessário executar novamente algumas configurações.

>**Observação:** certifique-se de ter concluído com sucesso a Tarefa 3 do primeiro módulo.

### Tempo estimado para concluir este laboratório: 30 minutos

### Tarefa 1: inicializar o Microsoft Defender para Ponto de Extremidade

Nesta tarefa, você vai executar a inicialização do Microsoft Defender para Ponto de Extremidade.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.  

1. Se você ainda não estiver no portal do Microsoft Defender XDR, inicie o navegador Microsoft Edge.

1. No navegador Microsoft Edge, acesse o portal do Defender XDR em <https://security.microsoft.com>.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de email do locatário referente ao nome de usuário do administrador fornecido pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a senha de locatário do administrador fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

    >**Dica:** a conta de email e a senha de locatário do administrador podem ser encontradas na guia Recursos.

1. No portal do **Defender XDR** , no menu de navegação à esquerda, role para baixo e expanda a seção **Sistema** e selecione **Configurações**.

    >**Observação:** algumas versões do portal podem não ter a opção **Configurações** na seção **Sistema**. As **configurações** podem ser agrupadas com *Relatórios* e *Auditoria*.

1. Na página Configurações, selecione **Descoberta de dispositivo**.

    >**Observação:** se você não encontrar a opção **Detecção de dispositivo** em **Configurações**, faça logoff selecionando o círculo superior direito com as iniciais da sua conta e selecione **Sair**. Outras opções que você talvez queira testar é atualizar a página com Ctrl+F5 ou abrir a página InPrivate. Entre mais uma vez com as credenciais de **Email do Locatário**.

1. Na configuração da Descoberta, verifique se a opção **Descoberta padrão (recomendada)** está selecionada. 

    >**Dica:** se não encontrar esta opção, atualize a página.

### Tarefa 2: integrar um dispositivo

Nesta tarefa, você integrará um dispositivo ao Microsoft Defender para Ponto de Extremidade usando um script de integração.

1. No portal do **Defender XDR**, no menu de navegação à esquerda, role para baixo, expanda a seção **Sistema**, selecione **Configurações** e, na página Configurações, selecione **Pontos de Extremidade**.

1. Selecione **Integração** na seção Gerenciamento de dispositivo.

    >**Observação:** você também pode executar a integração de dispositivos na seção **Ativos** da barra de menus à esquerda. Expanda Ativos e selecione Dispositivos. Na página Inventário de dispositivos, com a opção Computadores e dispositivos móveis selecionada, role para baixo até **Dispositivos integrados.** Isso levará você à página **Configurações > Pontos de extremidade**.

1. Na área "1. Integrar um dispositivo", certifique-se de que "Script local (para até 10 dispositivos)" seja exibido no menu suspenso Método de implantação e clique no botão **Baixar pacote de integração**.

1. No pop-up *Downloads*, realce o arquivo "WindowsDefenderATPOnboardingPackage.zip" com o mouse e selecione o ícone de pasta **Mostrar na pasta**. **Dica:** caso você não o veja, o arquivo deve estar no diretório c:\users\admin\downloads.

    >**Dica:** se o seu navegador bloquear o download, execute uma ação no navegador para permiti-lo. No navegador Microsoft Edge, você pode ver a mensagem "*WindowsDefenderATPOnboardingPackage.zip não é baixado com frequência. Certifique-se de que confia...*", clique no botão de reticências (...) se necessário e, em seguida, selecione **Manter**. No Microsoft Edge, um segundo pop-up aparece com a mensagem "*Certifique-se de confiar em WindowsDefenderATPOnboardingPackage.zip antes de abri-lo*", selecione **Mostrar mais** para expandir as seleções e selecione depois **Manter mesmo assim**.

1. Clique com o botão direito do mouse no arquivo zip baixado e selecione **Extrair tudo...**, certifique-se de que *Mostrar arquivos extraídos depois da conclusão* esteja marcado e selecione **Extrair**.

1. Clique com o botão direito do mouse no arquivo extraído "WindowsDefenderATPLocalOnboardingScript.cmd" e selecione **Propriedades**. Marque a caixa de seleção **Desbloquear** no canto inferior direito da janela Propriedades e selecione **OK**.

1. Clique com o botão direito do mouse no arquivo extraído "WindowsDefenderATPLocalOnboardingScript.cmd" novamente e escolha **Executar como administrador**.  **Dica:** se você encontrar a janela SmartScreen do Windows, selecione **Mais informações** e escolha **Executar mesmo assim**.

1. Quando a janela "Controle de conta de usuário" for exibida, selecione **Sim** para permitir que o script seja executado, responda **S** à pergunta apresentada pelo script e pressione **Enter**. Quando concluído, você verá uma mensagem na tela de comando dizendo *Máquina integrada com êxito para o Microsoft Defender para Ponto de Extremidade*.

1. Pressione qualquer tecla para continuar. Isso fechará a janela do prompt de comando.

### Tarefa 3: configurar funções

Nesta tarefa, você configurará funções para usar em grupos de dispositivos.

1. Na barra de menus esquerda do portal do Microsoft Defender XDR, expanda a seção **Sistema**, selecione **Configurações** e, em seguida, selecione **Pontos de extremidade**.

1. Selecione **Funções** na área de permissões.

1. Selecione o botão **Ativar funções**.

1. Selecione **+ Adicionar função**.

1. No diálogo Adicionar função, insira as seguintes informações:

    |Configurações gerais|Valor|
    |---|---|
    |Nome da função|**Suporte de Nível 1**|
    |Permissões|Recursos de Resposta imediata – Avançado|

1. Selecione **Avançar**.

1. Na página **Grupos de usuários atribuídos**, digite **sg-IT** no formulário *Filtrar grupos de usuários* e selecione **Adicionar grupos selecionados**. Verifique se ele aparece em *Grupos de usuários do Azure AD com essa função*.

1. Selecione **Enviar** e, em seguida, **Concluído** quando terminar.

    >**Observação:** se você receber o erro *"O usuário não pode executar esta ação porque seu UserAuthEnforcementMode é Rbac e esta ação requer um dos seguintes: RbacV2"*, selecione **OK** e tente novamente.

### Tarefa 4: configurar grupos de dispositivos

Nesta tarefa, você configurará grupos de dispositivos que permitem o controle de acesso e a configuração de automação.

1. Na barra de menus esquerda do portal do Microsoft Defender XDR, expanda a seção **Sistema**, selecione **Configurações** e, em seguida, selecione **Pontos de extremidade**.

1. Selecione **Grupos de dispositivos** na área de permissões.

1. Selecione o ícone **+ Adicionar grupo de dispositivos**.

1. Na guia Geral, insira as seguintes informações:

    |Configurações gerais|Valor|
    |---|---|
    |O nome do grupo de dispositivos|**Regular**|
    |Nível de correção|Completo – corrija ameaças automaticamente|

1. Selecione **Avançar**.

1. Na guia Dispositivos, para a condição do sistema operacional, selecione **Windows 11** e **Avançar**.

    >**Observação:** alguns provedores de hospedagem de laboratório podem ter imagens do *Windows 10* para WIN1. Você pode selecionar um ou ambos.

1. Na guia Visualizar dispositivos, o botão *Mostrar visualização* pode mostrar a máquina virtual WIN1, mas provavelmente os dados ainda não estão preenchidos. Selecione **Avançar** para continuar.

1. Na guia Acesso do usuário, selecione **sg-IT** e, em seguida, clique no botão **Adicionar grupos selecionados**. Certifique-se de que ele apareça em *Grupos de usuários do Azure AD com acesso a esse grupo de dispositivos*.

1. Selecione **Enviar** e, em seguida, **Concluído** quando terminar.

1. A configuração do grupo de dispositivos foi alterada. Selecione **Aplicar alterações** para verificar correspondências e recalcular agrupamentos.

1. Você terá dois grupos de dispositivos agora; o grupo "Regular" que você acabou de criar e o grupo "Dispositivos desagrupados (padrão)" com o mesmo nível de correção.

## Prossiga para o Exercício 2
