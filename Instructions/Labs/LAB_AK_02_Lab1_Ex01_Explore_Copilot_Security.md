---
lab:
  title: Exercício 1 — Explorar casos de uso no Microsoft Security Copilot
  module: Learning Path 2 - Mitigate threats using Microsoft Security Copilot
---

# Roteiro de aprendizagem 2 — Laboratório 1 — Exercício 1 — Explorar o Microsoft Security Copilot

## Cenário do laboratório

A organização para a qual você trabalha deseja aumentar a eficiência e as capacidades de seus analistas de operações de segurança e melhorar os resultados de segurança. Para facilitar esse objetivo, o escritório do diretor de Segurança da Informação (CISO) determinou que implantar o Microsoft Security Copilot é um passo fundamental para atingir esse objetivo. Como administrador de segurança da sua organização, você tem a tarefa de configurar o Copilot.

Neste exercício, você passará pela *primeira experiência de execução* do Microsoft Security Copilot para provisionar o Copilot com uma SCU (unidade de computação de segurança).

>**Observação:** o ambiente para este exercício é uma simulação gerada a partir do produto. Como uma simulação limitada, os links em uma página podem não estar habilitados e pode não haver suporte para entradas baseadas em texto que estejam fora do script especificado. Uma mensagem pop-up será exibida informando: "Este recurso não está disponível na simulação". Quando isso ocorrer, selecione OK e continue com as etapas do exercício.  

![Mensagem de erro pop-up](../Media/simulation-pop-up-error.png)

### Tempo estimado para concluir este laboratório: 45 minutos

### Tarefa 1: Provisionar o Microsoft Security Copilot

Para esse exercício, você está conectado como Avery Howard e tem uma função de administrador global no Microsoft Entra. Você trabalhará no portal do Azure e no Microsoft Security Copilot.

Este exercício deve levar aproximadamente **15** minutos para ser concluído.

>**Observação:** quando uma instrução de laboratório solicita a abertura de um link para o ambiente simulado, geralmente é recomendável abrir o link em uma nova janela do navegador para que você possa visualizar simultaneamente as instruções e o ambiente do exercício. Para fazer isso, selecione a tecla do mouse à direita e selecione a opção.

Antes que os usuários possam começar a usar o Copilot, os administradores precisam provisionar e alocar a capacidade. Para provisionar a capacidade:

- Você deve ter uma assinatura do Azure.
- Você precisa ser um proprietário do Azure ou colaborador do Azure, em um nível de grupo de recursos, no mínimo.

Nesta tarefa, você percorre o processo de garantir que tenha as permissões de função apropriadas. Isso começa habilitando o gerenciamento de acesso para recursos do Azure.

Depois de receber a função de Administrador de Acesso do Usuário no Azure, você poderá atribuir a um usuário o acesso necessário para provisionar SCUs para o Copilot.  Apenas para o propósito deste exercício, que é mostrar as etapas envolvidas, você atribuirá a si mesmo o acesso necessário.  As etapas a seguir irão guiá-lo durante o processo.

1. Verifique se a função Administrador de Acesso de Usuário está atribuída à sua conta.

1. Abra o ambiente simulado selecionando este link: <https://app.highlights.guide/start/6d7270b9-7187-456a-ac16-97bc227d5c27?token=045faae1-1078-4eac-bf56-e12472eddaf9&link=1&azure-portal=true>.

    <!--- Open the simulated environment by selecting this link: **[Azure portal](https://app.highlights.guide/start/6d7270b9-7187-456a-ac16-97bc227d5c27?token=045faae1-1078-4eac-bf56-e12472eddaf9&link=1&azure-portal=true)**.--->

1. Você começará habilitando o gerenciamento de acesso para recursos do Azure. Para acessar essa configuração:
    1. No portal do Azure, selecione **Microsoft Entra ID**.
    1. No painel de navegação esquerdo, expanda **Gerenciar**.
    1. No painel de navegação esquerdo, role para baixo e selecione **Propriedades**.
    1. Habilite o botão de alternância para **Gerenciamento de acesso aos recursos do Azure** e selecione **Salvar**.

1. Agora que você pode exibir todos os recursos e atribuir acesso em qualquer assinatura ou grupo de gerenciamento no diretório, atribua a si mesmo a função Proprietário para a assinatura do Azure.
    1. Na faixa azul na parte superior da página, selecione **Microsoft Azure** para retornar à página de aterrissagem do portal do Azure.
    1. Selecione **Assinaturas** e, em seguida, selecione a assinatura listada **Woodgrove – Demonstrações GTP (Exerno/Patrocinado)**.
    1. Selecione **IAM (Controle de acesso)**.
    1. Selecione **Adicionar** e **Adicionar atribuição de função**.
    1. Na guia Função, selecione **Funções de administrador com privilégios**.
    1. Selecione **Proprietário** e, em seguida, selecione **Avançar**.
    1. Selecione **+ Selecionar membros**.
    1. Avery Howard é o primeiro nome desta lista, selecione o **+** à direita do nome.  Avery Howard está agora listado sob membros selecionados. Selecione o botão **Selecionar** e depois **Avançar**.
    1. Selecione **Permitir que o usuário atribua todas as funções, exceto funções de administrador privilegiado, Proprietário, UAA, RBAC (Recomendado)**.
    1. Selecione **Revisão + atribuir**e, em seguida, selecione **Revisão + atribuir** uma última vez.

Como proprietário da assinatura do Azure, agora você poderá provisionar a capacidade no Copilot.

#### Subtarefa 1: Capacidade de provisão

Nesta tarefa, você percorre as etapas do provisionamento de capacidade para sua organização. Há duas opções para provisionar a capacidade:

- Provisionar a capacidade dentro do Security Copilot (recomendado)
- Capacidade de provisionamento por meio do Azure

Para esse exercício, você vai provisionar a capacidade por meio do Security Copilot. Ao abrir o Security Copilot pela primeira vez, um assistente vai orientar você ao longo das etapas de configuração de capacidade para a sua organização.

1. Abra o ambiente simulado selecionando este link: **[Microsoft Security Copilot](https://app.highlights.guide/start/6d7270b9-7187-456a-ac16-97bc227d5c27?token=045faae1-1078-4eac-bf56-e12472eddaf9&azure-portal=true)**.

1. Siga as etapas no Assistente, selecione **Introdução**.
1. Nesta página, você configurará a sua capacidade de segurança. Para qualquer um dos campos listados abaixo, você pode selecionar o ícone de informações para obter mais informações.
    1. Assinatura do Azure: Na lista suspensa, selecione **Woodgrove — Demonstrações de GTP (Externo/Patrocinado)**.
    1. Grupo de recursos: Na lista suspensa, selecione **RG-1**.
    1. Nome da capacidade: Insira um nome de capacidade.
    1. Local de avaliação do Prompt [Geo]: Na lista suspensa, selecione sua região.
    1. Você pode escolher se deseja selecionar a opção "Se este local tiver muito tráfego, permitir que o Copilot avalie prompts em qualquer lugar do mundo (recomendado para um desempenho ideal).
    1. A região de capacidade é definida com base no local selecionado.
    1. Computação de segurança: Esse campo é preenchido automaticamente com o mínimo necessário de unidades de SCU, que é 1. Deixe o campo com o valor de **1**.
    1. Selecione a caixa: **"Reconheço que li, entendi e concordo com os Termos e Condições."**
    1. Selecione **Continuar** no canto inferior direito da página.

1. O assistente mostra as informações sobre onde os dados do seu cliente serão armazenados. A região exibida se baseia na região que você selecionou no campo de avaliação do Prompt. Selecione **Continuar**.

1. Você pode selecionar opções para ajudar a melhorar o Copilot. Você pode selecionar a alternância com base em suas preferências.  Selecione **Continuar**.

1. Como parte da configuração inicial, o Copilot fornece acesso de colaborador a todos por padrão e inclui administradores globais e administradores de segurança como proprietários do Copilot. No ambiente de produção, você pode alterar quem tem acesso ao Copilot depois de concluir a configuração inicial. Selecione **Continuar**.
1. Tudo pronto! Selecione **Concluir**.
1. Feche a guia do navegador, já que o próximo exercício usará um link separado para um ambiente semelhante ao de um laboratório.

### Tarefa 2: Explorar a experiência autônoma do Microsoft Security Copilot

O administrador de segurança da sua organização provisionou o Copilot. Como você é analista sênior da equipe, o administrador adicionou você como proprietário do Copilot e pediu que você se familiarizasse com a solução.

Neste exercício, você explorará todos os principais pontos de referência na página de aterrissagem da experiência autônoma do Microsoft Security Copilot.

Você está conectado como Avery Howard e tem a função de proprietário no Copilot. Você vai trabalhar na experiência autônoma do Microsoft Security Copilot.

Este exercício deve levar aproximadamente **15** minutos para ser concluído.

#### Subtarefa 1: Explorar as opções do menu

Nesta tarefa, você inicia a exploração no menu inicial.

1. Abra o ambiente simulado selecionando este link: **[Microsoft Security Copilot](https://app.highlights.guide/start/7608581a-ee3a-4fe0-be03-309a58b78c60?token=045faae1-1078-4eac-bf56-e12472eddaf9&azure-portal=true)**.

1. Selecione o ícone **Menu** ![ícone do menu da página inicial](../Media/home-menu-icon.png), que às vezes é chamado de ícone de hambúrguer.

1. Selecione **Minhas sessões** e anote as opções disponíveis.
    1. Selecione Recente para exibir as sessões mais recentes
    1. Selecione Filtrar, anote as opções disponíveis e feche o arquivador.
    1. Selecione o ícone de menu inicial para abrir o menu inicial.

1. Selecione **Biblioteca de promptbooks**.
    1. Selecione Meus promptbooks. Uma tarefa subsequente se aprofunda nos promptbooks.
    1. Selecione Woodgrove.
    1. Selecione Microsoft.
    1. Selecione Filtrar para exibir as opções disponíveis e, em seguida, selecione o X para fechar.
    1. Selecione o ícone de menu inicial para abrir o menu inicial.

1. Selecione **Configurações do proprietário**. Essas configurações estão disponíveis para você como proprietário do Copilot. Um colaborador do Copilot não tem acesso a essas opções de menu.
    1. Para os plugins do Security Copilot, selecione a lista suspensa "Quem pode adicionar e gerenciar seus próprios plugins personalizados" para ver as opções disponíveis.
    1. Selecione a lista suspensa para Quem pode adicionar e gerenciar plug-ins personalizados para todos na organização para exibir as opções disponíveis. Observe que esta opção fica acinzentada se Quem pode adicionar e gerenciar seus próprios plug-ins personalizados estiver definido como Apenas proprietários.
    1. Selecione o ícone de informações ao lado de "Permitir que o Security Copilot acesse dados dos seus Serviços do Microsoft 365".  Essa configuração deve ser habilitada se você quiser usar o plug-in do Microsoft Purview. Você trabalhará com esta configuração em um exercício posterior.
    1. Selecione a lista suspensa para Quem pode carregar arquivos para exibir as opções disponíveis.
    1. Selecione o ícone de menu inicial para abrir o menu inicial.

1. Selecione **Atribuição de função**.
    1. Selecione Adicionar membros e feche.
    1. Expanda Proprietário.
    1. Expanda Colaborador.
    1. Selecione o ícone de menu inicial para abrir o menu inicial.

1. Selecione **Monitoramento de uso**.
    1. Selecione o filtro de data para exibir as opções disponíveis.
    1. Selecione o ícone de menu inicial para abrir o menu inicial.

1. Selecione **Configurações**.
    1. Selecione Preferências. Role para baixo para exibir as opções disponíveis.
    1. Selecione Dados e privacidade.
    1. Selecione Sobre.
    1. Selecione o X para fechar a janela de preferências.

1. Selecione o local em que está escrito **Woodgrove** na parte inferior esquerda do menu inicial.
    1. Ao selecionar essa opção, você verá seus locatários. Isso é conhecido como seletor de locatários. Nesse caso, Woodgrove é o único locatário disponível.
    1. Selecione a **Página Inicial** para retornar à página de aterrissagem.

#### Subtarefa 2: Explorar o acesso às sessões recentes

No centro da página de aterrissagem, há cartões que representam suas sessões mais recentes.

1. O maior cartão é sua última sessão. Selecionar o título de qualquer cartão de sessão leva você para a respectiva sessão.
1. Selecione **Exibir todas as sessões** para ir para a página Minhas sessões.
1. Selecione **Microsoft Copilot para Segurança**, ao lado do ícone de menu inicial, para retornar à página de aterrissagem.

#### Subtarefa 3: Explorar o acesso aos promptbooks

A próxima seção da página de aterrissagem do Copilot gira em torno de promptbooks. A página de aterrissagem mostra blocos para alguns promptbooks da Segurança da Microsoft. Aqui você explora o acesso aos promptbooks e à biblioteca de promptbooks. Em um exercício subsequente, você explora a criação e a execução de um promptbook.

1. À direita de onde se lê "Introdução a esses promptbooks" há as teclas de seta para a esquerda e para a direita, que permitem rolar pelos blocos dos promptbooks de segurança da Microsoft. Selecione a **seta para a direita >**

1. Cada bloco mostra o título do promptbook, uma breve descrição, o número de prompts e um ícone de execução. Selecione o título de qualquer um dos blocos da sequência de solicitações para abrir essa página. Selecione a **Avaliação de impacto de vulnerabilidade**, como exemplo.
    1. A janela do promptbook selecionado fornece informações, incluindo quem criou o promptbook, marcas, uma breve descrição, entradas necessárias para executar o promptbook e uma listagem dos prompts.
    1. Observe que as informações sobre a sequência de solicitações e as opções disponíveis. Para esta simulação, você não pode iniciar uma nova sessão, você fará isso em um exercício subsequente. 
    1. Selecione **X** para fechar a janela.

1. Selecione **Exibir a biblioteca de promptbook**.
    1. Para exibir promptbooks que você possui, selecione Meus promptbooks.
    1. Selecione Woodgrove para obter uma listagem de promptbooks pertencentes ao Woodgrove, o nome de uma organização fictícia.
    1. Para exibir promptbooks internos de propriedade da Microsoft ou desenvolvidos por ela, selecione Microsoft.
    1. Selecione o ícone de filtro. Aqui você pode filtrar com base nas marcas atribuídas à pasta de trabalho. Feche a janela de filtro selecionando o X na guia Novo filtro.
    1. Selecione **Microsoft Copilot para Segurança**, ao lado do ícone de menu inicial, para retornar à página de aterrissagem.

#### Subtarefa 4: Explorar o ícone de prompts e fontes na barra de solicitação

No centro inferior da página está a barra de prompts. A barra de solicitação inclui o ícone de prompts e fontes, que você vai explorar nesta tarefa. No exercícios subsequentes, você vai inserir informações diretamente na barra de solicitação.

1. Na barra de solicitação, selecione o ícone de prompts para selecionar um prompt interno ou uma sequência de solicitações. Selecione o **ícone de prompts**![ícone de prompts](../Media/prompt-icon.png).
    1. Selecione **Ver todos os promptbooks**
        1. Role para exibir todos os promptbooks disponíveis.
        1. Selecione a **seta para trás** ao lado da barra de pesquisa para voltar.
    1. Selecione **Ver todos os recursos do sistema**. A lista mostra todos os recursos do sistema disponíveis (esses recursos são, na verdade, prompts que você pode executar). Muitos recursos do sistema são associados a plug-ins específicos e, como tal, só serão listados se o plug-in correspondente estiver habilitado.
        1. Role para exibir todos os promptbooks disponíveis.
        1. Selecione a **seta para trás** ao lado da barra de pesquisa para voltar.

1. Selecione o **ícone de fontes**![ícone de fontes](../Media/sources-icon.png).
    1. O ícone de fontes abre a janela Gerenciar fontes. A partir daqui, você pode acessar Plug-ins ou Arquivos. A guia **Plug-ins** é selecionada por padrão.
        1. Selecione se deseja exibir todos os plug-ins, aqueles que estão habilitados (ativados) ou aqueles que estão desabilitados (desativados).
        1. Expanda/recolha a lista de plug-ins que não são da Microsoft, plug-ins da Microsoft e plug-ins personalizados.
        1. Alguns plug-ins exigem a configuração de parâmetros. Selecione o botão **Configurar** do plug-in do Microsoft Sentinel para exibir a janela de configurações. Selecione **cancelar** para fechar a janela de configurações. Em um exercício separado, você configura o plug-in.
    1. Você ainda deverá estar na janela Gerenciar fontes. Selecionar **Arquivos**.
        1. Examine a descrição.
        1. Os arquivos podem ser carregados e usados como uma base de conhecimento pelo Copilot. Em um exercício subsequente, você vai trabalhar com uploads de arquivos.
        1. Selecione **X** para fechar a janela de gerenciamento de fontes.

#### Subtarefa 5: Explorar o recurso de ajuda

No canto inferior direito da janela está o ícone de ajuda, onde você pode acessar a documentação facilmente e encontrar soluções para problemas comuns. A partir do ícone de ajuda, você também pode enviar um caso de suporte para a equipe de suporte da Microsoft se tiver as permissões de função apropriadas.

1. Selecione o ícone **Ajuda (?)**.
    1. Selecione **Documentação**. Esta seleção abre uma nova aba do navegador para a documentação do Microsoft Security Copilot. Retorne à guia do navegador para o Microsoft Security Copilot.
    1. Selecione **Ajuda**.
        1. Qualquer pessoa com acesso ao Security Copilot pode acessar o widget de autoajuda selecionando o ícone de ajuda e, a seguir, selecionando a guia Ajuda. Aqui você pode encontrar soluções para problemas comuns inserindo algo sobre o problema.
        1. Usuários com no mínimo a função Administrador do suporte de serviços ou a função Administrador da assistência técnica podem enviar um caso de suporte para a equipe de suporte da Microsoft. Se você tiver esta função, um ícone de fone de ouvido será exibido. Feche a página de suporte de contato.

### Tarefa 3: Explorar a experiência incorporada do Microsoft Security Copilot

Neste exercício, você investigará um incidente no Microsoft Defender XDR. Como parte da investigação, você explora os principais recursos do Microsoft Copilot no Microsoft Defender XDR, incluindo resumo de incidentes, resumo de dispositivos, análise de script e muito mais. Você também dinamiza sua investigação para a experiência autônoma e usa o pin board como uma maneira de compartilhar detalhes de sua investigação com seus colegas.

Você está conectado como Avery Howard e tem a função de proprietário no Copilot. Você trabalhará no Microsoft Defender, usando a nova plataforma de operações de segurança unificada, para acessar as funcionalidades do Copilot inserido no Microsoft Defender XDR. Perto do final do exercício, você passa para a experiência autônoma do Microsoft Security Copilot.

Este exercício deve levar aproximadamente **30** minutos para ser concluído.

#### Subtarefa 1: Explorar o resumo do incidente e as respostas guiadas

1. Abra o ambiente simulado selecionando este link: **[Portal do Microsoft Defender](https://app.highlights.guide/start/be8a91c3-3979-4048-ad38-fd38deaf7117?token=045faae1-1078-4eac-bf56-e12472eddaf9&azure-portal=true)**.

1. No portal do Microsoft Defender:
    1. Expanda **Investigação e resposta**.
    1. Expanda **Incidentes e alertas**.
    1. Selecione **Incidentes**.

1. Selecione o primeiro incidente na lista, **ID do incidente: 185856**, chamado Ataque de ransomware operado por humanos, foi iniciado por meio de um ativo comprometido (interrupção de ataque).

1. Esse é um incidente complexo. O Defender XDR fornece uma grande quantidade de informações, porém, com 50 alertas, pode ser um desafio saber onde se concentrar. No lado direito da página de incidentes, o Copilot gera automaticamente um **Resumo de incidentes** que ajuda a orientar seu foco e resposta. Selecione **Ver mais**.
    1. O resumo do Copilot descreve como esse incidente evoluiu, incluindo acesso inicial, movimento lateral, coleção, acesso de credenciais e exfiltração. Ele identifica dispositivos específicos, indica que a ferramenta PsExec foi usada para inicializar arquivos executáveis e muito mais.
    1. Esses são todos os itens que você pode aproveitar para uma investigação mais aprofundada. Você explora algumas delas em tarefas subsequentes.

1. Role para baixo no painel do Copilot e logo abaixo do resumo há **Respostas guiadas**. As respostas guiadas recomendam ações em suporte à triagem, à contenção, à investigação e à correção.
    1. O primeiro item na categoria de triagem é Classificar esse incidente. Selecione **Classificar** para exibir as opções. Examine as respostas guiadas nas outras categorias.
    1. Selecione o botão **Status** acima do *Resumo* e filtre por **Concluído**. Quatro atividades concluídas aparecem rotuladas como *Interrupção de ataque*. A interrupção automática de ataque foi projetada para conter ataques em andamento, limitar o impacto nos ativos de uma organização e fornecer mais tempo para as equipes de segurança mitigarem totalmente o ataque.
1. Mantenha a página de incidentes aberta, pois você vai usá-la na próxima tarefa.

#### Subtarefa 2: Explorar o resumo do dispositivo e da identidade

1. Na página incidente, na guia *História do ataque*, role para baixo pelos alertas e selecione o alerta de **Sessão RDP suspeita**.

1. O Copilot gera automaticamente um **Resumo de alerta**, que fornece uma riqueza de informações para análise posterior. Por exemplo, o resumo identifica atividades suspeitas, de coleta de dados, acesso a credenciais, malware, atividades de descoberta e muito mais.

1. Há muitas informações na página, portanto, para obter uma visão melhor desse alerta, selecione **Abrir página do alerta**. Ele está no terceiro painel na página de alertas, ao lado do grafo de incidentes e abaixo do título do alerta.

1. Na parte superior da página está o cartão para o dispositivo **parkcity-win10v**. Selecione as reticências e anote as opções. Selecione **Resumir**. O Copilot gera um **Resumo do dispositivo**. Não vale nada que haja várias maneiras de acessar o resumo do dispositivo e dessa forma é apenas um método conveniente. O resumo mostra que o dispositivo é uma VM, identifica o proprietário do dispositivo, mostra seu status de conformidade em relação às políticas do Intune e muito mais.

1. Ao lado do cartão do dispositivo, há um cartão para o proprietário do dispositivo. Selecione **PARKCITY\jonaw**. O terceiro painel da página deixa de mostrar detalhes do alerta e passa a fornecer informações sobre o usuário Jonathan Wolcott, um executivo de contas, cujo risco Microsoft Entra ID e gravidade do risco Insider são classificados como altos. Isso não é surpreendente, dado o que você aprendeu com os resumos do alerta e do incidente do Copilot. Selecione os três pontos e selecione **Resumir** para obter um resumo de identidade gerado pelo Copilot.

1. Mantenha essa página aberta, pois você vai usá-la na próxima tarefa.

#### Subtarefa 3: Explorar a análise do script

1. Vamos nos concentrar na história do alerta. Selecione **Maximizar ![ícone maximizar](../Media/maximize-icon.png)**, localizado no painel principal do alerta, logo abaixo do cartão rotulado 'partycity\jonaw' para obter uma melhor visualização da árvore de processos. Do modo de exibição maximizado, você começa a ter uma visão mais clara de como esse incidente ocorreu. Muitos itens de linha indicam que powershell.exe executou um script. Como o usuário Jonathan Wolcott é um executivo de conta, é razoável supor que executar scripts do PowerShell não é algo que esse usuário provavelmente esteja fazendo regularmente.

1. Expanda a primeira instância de **powershell.exe executar um script**, é aquela que mostra o carimbo de data/hora de 4:57:11. O Copilot tem a capacidade de analisar scripts. Selecione **Analisar**.
    1. O Copilot gera uma análise do script e sugere que ele pode ser uma tentativa de phishing ou usado para uma entregar um software de exploração de vulnerabilidades baseado na Web.
    1. Selecione **Mostrar código**. O código mostra uma URL cujo potencial de causar dano foi eliminado.

1. Há vários outros itens que indicam que powershell.exe executou um script. Expanda aquele rotulado como **powershell.exe -EncodedCommand...**. O script original foi codificado em base 64, mas o Defender o decodificou para você. Para a versão decodificada, selecione **Analisar**. A análise destaca a sofisticação do script usado neste ataque.

1. Na análise Script do Copilot, você tem botões para mostrar código e mostrar técnicas MITRE

1. Selecione o botão **Mostrar Técnicas do MITRE** e selecione o link rotulado: T1105: Transferência de ferramenta de entrada

1. Isso abre a página do site *MITRE | ATT&CK* que descreve a técnica em detalhes.

1. Feche a página de história do alerta selecionando o **X** (o X à esquerda do painel do Copilot). Agora use a trilha para retornar ao incidente. Selecione **O ataque de ransomware operado por humanos foi iniciado a partir de um ativo comprometido (interrupção de ataque)**.

#### Subtarefa 4: Explorar análise de arquivo

1. Você está de volta à página de incidentes. No resumo do alerta, o Copilot identificou o arquivo mimikatz.exe, associado ao malware "Mimikatz". Você pode usar a funcionalidade de análise de arquivo no Defender XDR para ver quais outros insights você pode obter. Há várias maneiras de acessar arquivos. Na parte superior da página, selecione a guia **Evidências e Resposta**.

1. No lado esquerdo da tela, selecione **Arquivos**.
1. Selecione o primeiro item da lista com a entidade chamada **mimikatz.exe**.
1. Na janela que é aberta, selecione **Abrir página de arquivo**.
1. Selecione o ícone do Copilot (se a análise de arquivo não for aberta automaticamente), e o Copilot gerará uma análise de arquivo.
1. Examine a análise de arquivo detalhada gerada pelo Copilot.
1. Feche a página Arquivo e use a trilha para retornar ao incidente. Selecione **O ataque de ransomware operado por humanos foi iniciado a partir de um ativo comprometido (interrupção de ataque)**.

#### Subtarefa 5: Mudar para a experiência autônoma

Essa tarefa é complexa e requer o envolvimento de analistas mais experientes. Nesta tarefa, você dinamizará sua investigação e executará o promptbook de incidentes do Defender para que os outros analistas tenham as informações iniciais da investigação. Você fixa respostas ao quadro informativo e gera um link para essa investigação, que você pode compartilhar com membros mais avançados da equipe para ajudar a investigar.

1. Retorne à página de incidentes selecionando a guia **História do ataque** na parte superior da página.

1. Selecione as reticências ao lado do resumo do incidente do Copilot e selecione **Abrir no Security Copilot**.

1. O Copilot é aberto na experiência autônoma e mostra o resumo do incidente. Você também pode executar mais prompts. Nesse caso, você executará a sequência de solicitações para um incidente. Selecione o **ícone de prompt**![ícone de prompt](../Media/prompt-icon.png). 
    1. Selecione **Ver todos os promptbooks**.
    1. Selecione **Investigação de incidentes do Microsoft 365 Defender**.
    1. A página do promptbook é aberta e solicita a ID de Incidente do Defender. Insira **185856** e selecione **Enviar**.
    1. Examine as informações fornecidas. Ao dinamizar para a experiência autônoma e executar o promptbook, a investigação é capaz de invocar recursos de uma solução de segurança de conjunto mais amplo, além apenas do Defender XDR, com base nos plug-ins habilitados.

1. Selecione o **ícone de caixa ![ícone de caixa](../Media/box-icon.png)** ao lado do ícone de alfinete para selecionar todos os prompts e as respostas correspondentes e, em seguida, selecione o **ícone de alfinete ![ícone de alfinete](../Media/pin-icon.png)** para salvar essas respostas no quadro de avisos.

1. O painel de fixação é aberto automaticamente. O quadro de fixação contém os prompts e respostas salvos, juntamente com um resumo de cada um deles. Você pode abrir e fechar o quadro de avisos selecionando o **ícone do quadro de avisos ![ícone do quadro de avisos](../Media/pinboard-icon.png)**.

1. Na parte superior da página, selecione **Compartilhar** para exibir suas opções. Ao compartilhar o incidente por meio de um link ou email, as pessoas em sua organização com acesso ao Copilot podem ver esta sessão. Feche a janela selecionando o **X**.

#### Subtarefa 6: Criar e executar uma consulta KQL

Em seguida, usaremos o Copilot para nos ajudar a criar uma consulta KQL (Linguagem de Consulta Kusto) para usar com a busca avançada no Defender XDR.

1. Enquanto ainda estiver no Copilot de Segurança autônomo, insira a solicitação a seguir no formulário de solicitação: *Com base nesse incidente, crie uma consulta para procurar proativamente esse tipo de ataque de malware. Use o woodgrove-loganalyticsworkspace.*

1. Clique no ícone Enviar solicitação para executar a solicitação.
O Copilot escolhe a linguagem natural para KQL para a busca avançada.

1. O Copilot gera uma consulta KQL e uma resposta:

    1. Leia a explicação da consulta Kusto.

    1. Examine o detalhamento da consulta Kusto. Isso será muito útil se você estiver apenas começando a usar o KQL.

1. Copie a consulta KQL gerada pelo Copilot e retorne ao portal do Defender XDR.
***É recomendável primeiro copiar a consulta para o Bloco de Notas ou outro editor para reduzir problemas de formatação***.

1. O Defender XDR ainda deve ter a seção Investigações e resposta aberta. Selecione **Busca** e **Busca avançada** no menu de navegação.

1. Na Busca avançada, selecione **Nova consulta +** para abrir uma janela e colar a consulta KQL gerada pelo Copilot no formulário.
***É recomendável primeiro copiar a consulta para o Bloco de Notas ou outro editor para reduzir problemas de formatação***.

1. Depois de executar a consulta KQL, volte ao Copilot para refiná-la ou selecione o ícone do Copilot na página consulta de Busca avançada para ajustar as consultas de busca.

1. Agora você pode fechar a guia do navegador para sair da simulação.

## Resumo e recursos adicionais

Neste exercício, você explorou a primeira experiência de execução do Microsoft Security Copilot, a capacidade provisionada e explorou as experiências autônomas e incorporadas do Copilot. Você investigou um incidente no Microsoft Defender XDR, explorou o resumo do incidente, o resumo do dispositivo, a análise de script e muito mais. Você também adaptou sua investigação para a experiência autônoma e usou o quadro de avisos como uma forma de compartilhar detalhes de sua investigação com seus colegas.

Para executar simulações de casos de uso adicionais do Microsoft Security Copilot, navegue até [Explorar simulações de casos de uso do Microsoft Security Copilot](/training/modules/security-copilot-exercises/)
