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

### Tarefa 2: Instalar o Azure Arc em um servidor local

Nesta tarefa, você instalará o Azure Arc em um servidor local para facilitar a integração.

>**Importante:** As próximas etapas são feitas em uma máquina diferente daquela que você estava trabalhando anteriormente. Procure as referências de nome da máquina virtual.

1. Faça logon na máquina virtual **WINServer** como Administrador com a senha: **Passw0rd!** Se necessário.  

1. Abra o navegador Microsoft Edge e acesse o portal do Azure em <https://portal.azure.com>.

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Arc* e selecione **Azure Arc**.

1. No painel de navegação em **recursos do Azure Arc** selecione **Computadores**

1. Selecione **+ Adicionar/Criar** e, em seguida, selecione **Adicionar uma máquina**.

1. Na seção "Adicionar servidor único", selecione **Gerar script**.

1. Na página *Adicionar um servidor com o Azure Arc*, selecione o grupo de recursos criado anteriormente em *Detalhes do projeto*. **Dica:** *RG-Defender*

    >**Observação:** se você ainda não tiver criado um grupo de recursos, abra outra guia, crie o grupo de recursos e comece de novo.

1. Em *Região*, selecione **(EUA) Leste dos EUA** na lista suspensa.

1. Revise as opções de *Detalhes do servidor* e do *Método de conectividade*. Mantenha os valores padrão e selecione **Avançar** para acessar a guia Marcas.

1. Revise as marcas padrão disponíveis. Selecione **Avançar** para acessar a guia Baixar e executar script.

1. Role a página para baixo e clique no botão **Download**. **Dica:** se o seu navegador bloquear o download, execute uma ação no navegador para permiti-lo. No navegador Microsoft Edge, clique no botão de reticências (...) se necessário e depois em **Manter**.

1. Clique com o botão direito do mouse no botão Iniciar do Windows e selecione **Windows PowerShell (Administrador)**.

1. Insira *Administrador* em "Nome de usuário" e *Passw0rd!* em "Senha" se você receber um prompt do UAC.

1. Insira: cd C:\Users\Administrator\Downloads

    >**Importante:** Se não tiver esse diretório, provavelmente significa que você está na máquina errada. Volte para o início da Tarefa 4, mude para WINServer e comece de novo.

1. Insira *Set-ExecutionPolicy -ExecutionPolicy Unrestricted* e pressione Enter.

1. Insira **A** para Sim para todos e pressione Enter.

1. Insira *.\OnboardingScript.ps1* e pressione Enter.  

    >**Importante:** se você receber o erro *"O termo .\OnboardingScript.ps1 não é reconhecido..."*, verifique se está executando as etapas da Tarefa 4 na máquina virtual WINServer. Outro problema pode ser que o nome do arquivo foi alterado devido a vários downloads, procure por *".\OnboardingScript (1).ps1"* ou outros números de arquivo no diretório em execução.

1. Insira **R** para Executar uma vez e pressione Enter (isso pode levar alguns minutos).

1. O processo de instalação abrirá uma nova guia do navegador Microsoft Edge para autenticar o agente do Azure Arc. Selecione sua conta de administrador, aguarde a mensagem "Autenticação concluída" e volte para a janela do Windows PowerShell.

1. Quando a instalação for concluída, volte para a página do portal do Azure onde você baixou o script e selecione **Fechar**. Feche a página **Adicionar servidores com o Azure Arc** para voltar à página **Máquinas** do Azure Arc.

1. Selecione **Atualizar** até que o nome do servidor WINServer apareça e o Status seja *Conectado*.

    >**Observação:** este comando levará alguns minutos.

### Tarefa 3: Conectar uma máquina virtual do Azure Windows

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
