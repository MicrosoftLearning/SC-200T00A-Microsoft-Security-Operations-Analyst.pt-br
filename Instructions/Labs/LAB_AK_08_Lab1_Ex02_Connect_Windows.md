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

1. Na caixa **Pesquisar serviços e marketplace**, insira *Windows 11* e selecione **Windows 11** na lista suspensa.

1. Selecione a caixa para **Windows 11**.

1. Abra a lista suspensa *Plano* e selecione **Windows 11 Enterprise, versão 22H2**.

1. Selecione **Iniciar com uma configuração predefinida** para continuar.

1. Selecione **Desenvolvimento/Teste** e, em seguida, selecione **Continuar para criar uma VM**.

1. Selecione **Criar novo** em *Grupo de recursos*, insira RG-AZWIN01 em Nome e clique em **OK**.

    >**Observação:** esse será um novo grupo de recursos para fins de acompanhamento. 

1. Em *Nome da máquina virtual*, insira AZWIN01.

1. Mantenha **(EUA) Leste dos EUA** como valor padrão para *Região*.

1. Role para baixo e revise a *imagem* da máquina virtual. Se ele estiver vazio, selecione **Windows 11 Enterprise, versão 22H2**.

1. Revise o *Tamanho* da máquina virtual. Se estiver vazio, selecione **Ver todos os tamanhos**, escolha o primeiro tamanho de VM (série D) relacionado e selecione **Selecionar**.

    >**Observação:** se você vir a mensagem *Esta imagem não tem suporte para Gerenciamento automatizado do Azure. Para desabilitar esse recurso, navegue até a guia Gerenciamento. Caso contrário, selecione uma imagem com suporte.* Vá para a guia Gerenciamento e desabilite "Gerenciamento automatizado". O processo de criação progredirá depois.

1. Role para baixo e insira um *Nome de usuário* de sua escolha. **Dica:** Evite palavras reservadas como "admin" (administrador) ou "root" (raiz).

1. Insira uma *senha* de sua escolha. **Dica:** pode ser mais fácil reutilizar sua senha LabUser. A senha pode ser enconrada na guia de recursos. Pode ser necessário inseri-la duas vezes.

1. Role para baixo até a parte inferior da página e marque a caixa de seleção abaixo de *Licenciamento* para confirmar que você tem a licença qualificada.

1. Selecione **Examinar + criar** e aguarde até que a validação seja aprovada.

    >**Observação:** se houver uma falha de validação de *Sistema de rede*, selecione essa guia, revise seu conteúdo e depois selecione **Examinar + criar** novamente.

1. Selecione **Criar**. Aguarde até que o recurso seja criado, o que pode levar alguns minutos.

### Tarefa 2: Conectar um servidor local no Azure

Nesta tarefa, você conectará um servidor local à sua assinatura do Azure. O Azure Arc foi pré-instalado neste servidor. O servidor será usado nos próximos exercícios para executar ataques simulados que você irá detectar e investigar posteriormente no Microsoft Sentinel.

>**Importante:** as próximas etapas são feitas em uma máquina diferente daquela em que você estava trabalhando anteriormente.

1. Faça logon na máquina virtual **WINServer** como Administrador com a senha: **Passw0rd!** Se necessário.  

    >**Observação:** conforme descrito acima, o Azure Arc foi pré-instalado na máquina **WINServer**. Agora você conectará essa máquina à sua assinatura do Azure.

1. No computador *WINServer*, clique no ícone de *pesquisa* e digite **cmd**.

1. Nos resultados da pesquisa, clique com o botão direito do mouse em *Prompt de Comando* e selecione **Executar como administrador**.

1. Na janela do Prompt de comando, digite o seguinte comando. *Não pressione Enter*:

    ```cmd
    azcmagent connect -g "defender-RG" -l "EastUS" -s "Subscription ID string"
    ```

1. Substitua a **cadeia de caracteres da ID da assinatura** pela *ID da assinatura* fornecida pelo host do laboratório (*guia Recursos). Certifique-se de manter as aspas.

1. Digite **Enter** para executar o comando (isso pode levar alguns minutos).

    >**Observação**: se você vir a janela de seleção do navegador *Como deseja abrir isso?*, selecione **Microsoft Edge**.

1. Na caixa de diálogo *Entrar*, digite o **Email do locatário** e a **Senha do locatário** fornecida pelo provedor de hospedagem do laboratório e clique em **Entrar**. Aguarde a mensagem *Autenticação concluída*, feche a guia do navegador e retorne à janela do *Prompt de comando*.

1. Quando os comandos concluírem a execução, deixe a janela do *Prompt de comando* aberta e digite o seguinte comando para confirmar se a conexão ocorreu:

    ```cmd
    azcmagent show
    ```

1. Na saída do comando, verifique se o *Status do agente* é **Conectado**.

### Tarefa 3: Conectar uma máquina virtual do Azure Windows

Nesta tarefa, você conectará uma máquina virtual do Windows do Azure ao Microsoft Sentinel.

>**Observação:** o Microsoft Sentinel foi pré-implantado em sua assinatura do Azure com o nome **defenderWorkspace** e as soluções necessárias do *hub de conteúdo* foram instaladas.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.  

1. Se necessário, abra o navegador Microsoft Edge, navegue até o portal do Azure em <https://portal.azure.com> e entre com as credenciais fornecidas.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o **defenderWorkspace** do Microsoft Sentinel.

1. No menu de navegação à esquerda do Microsoft Sentinel, role para baixo até a seção *Gerenciamento de conteúdo* e selecione **Hub de conteúdo**.

1. No *Hub de conteúdo*, procure a solução **Eventos de Segurança do Windows** e selecione-a na lista.

1. Na página da solução *Eventos de Segurança do Windows*, selecione **Gerenciar**.

    >**Observação:** A solução *Eventos de Segurança do Windows* instala os conectores de dados *Eventos de Segurança do Windows via AMA* e *Eventos de Segurança via agente herdado*. Mais 2 pastas de trabalho, 20 regras de análise e 43 consultas de busca.

1. Selecione o conector de dados *Eventos de Segurança do Windows via AMA* e selecione **Abrir página do conector** na folha de informações do conector.

1. Na seção *Configuração*, clique no botão **+ Criar regra de coleta de dados**.

1. Insira **AZWINDCR** para Nome da regra e depois selecione **Avançar: Recursos**.

1. Expanda sua *Assinatura do MOC* em *Escopo* na guia *Recursos*.

    >**Dica:** Você pode expandir toda a hierarquia *Escopo* selecionando o ">" antes da coluna *Escopo*.

1. Expanda **RG-AZWIN01** e selecione **AZWIN01**.

1. Selecione **Avançar: coletar**.

1. Revise a opção de coleta diferente de Evento de Segurança. Manter *Todos os Eventos de Segurança* e selecione **Avançar: Examinar + criar**.

1. Selecione **Criar** para salvar uma regra de coleta de dados.

1. Aguarde um minuto e selecione **Atualizar** para ver a nova regra de coleta de dados listada.

### Tarefa 4: Conectar uma máquina Windows que não seja do Azure

Nesta tarefa, você adicionará uma máquina virtual Windows que não seja do Azure conectada ao Azure Arc ao Microsoft Sentinel.  

   >**Observação:** o conector de dados *Eventos de Segurança do Windows via AMA* exige o Azure Arc para dispositivos que não sejam do Azure.

1. Verifique se você está na configuração do conector de dados *Eventos de Segurança do Windows via AMA* em seu workspace do Microsoft Sentinel.

1. Na seção *Configuração*, edite a *regra de coleta de dados* **AZWINDCR** selecionando o ícone de *lápis*.

1. Selecione **Avançar: Recursos** e expanda sua *Assinatura do MOC* em *Escopo* na guia *Recursos*.

    >**Dica:** Você pode expandir toda a hierarquia *Escopo* selecionando o ">" antes da coluna *Escopo*.

1. Expanda o **defender-RG** (ou o Grupo de recursos que você criou) e selecione **WINServer**.

    >**Importante:** Se você não vir o WINServer, consulte o Roteiro de aprendizagem 3, Exercício 1 e Tarefa 4 onde você instalou o Azure Arc neste servidor.

1. Selecione **Avançar: Coletar**, depois **Avançar: Examinar + criar**.

1. Depois que a mensagem *Validação aprovada* for exibida, selecione **Criar**.

## Prossiga para o Exercício 3
