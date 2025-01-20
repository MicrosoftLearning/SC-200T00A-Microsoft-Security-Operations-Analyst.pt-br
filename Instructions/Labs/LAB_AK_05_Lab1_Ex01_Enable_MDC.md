---
lab:
  title: 'Exercício 1: habilitar o Microsoft Defender para Nuvem'
  module: Learning Path 5 - Mitigate threats using Microsoft Defender for Cloud
---

# Roteiro de aprendizagem 5 — Laboratório 1 — Exercício 1 — Habilitar o Microsoft Defender para Nuvem

## Cenário do laboratório

Você é um analista de operações de segurança que trabalha em uma empresa que está implementando proteções de carga de trabalho na nuvem com o Microsoft Defender para Nuvem. Neste laboratório, você habilitará o Microsoft Defender para Nuvem.

>**Importante:** os exercícios de laboratório para o Roteiro de Aprendizagem 5 estão em um ambiente *independente*. Se você sair do laboratório antes de concluí-lo, será necessário executar as configurações novamente.

### Tempo estimado para concluir este laboratório: 15 minutos

### Tarefa 1: habilitar o Microsoft Defender para Nuvem

Neste tarefa, você habilitará e configurará o Microsoft Defender para Nuvem.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.

1. No navegador Microsoft Edge, acesse o portal do Azure em <https://portal.azure.com>.
  
1. Na caixa de diálogo **Entrar**, copie e cole a conta de email do locatário referente ao nome de usuário do administrador fornecido pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a senha de locatário do administrador fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de pesquisa do portal do Azure, digite *Defender* e selecione **Microsoft Defender para Nuvem**.

1. No menu de navegação esquerdo do Microsoft Defender para Nuvem, expanda a seção *Gerenciamento* e selecione **Configurações do ambiente**.

1. Selecione o botão **Expandir tudo** para visualizar todas as assinaturas e recursos.

1. Selecione a assinatura **MOC Subscription-lodxxxxxxxx** (ou nome equivalente em seu idioma).

1. Analise os recursos do Azure que agora estão protegidos com os planos do Defender para Nuvem.

    >**Importante:** Se todos os planos do Defender estiverem *Desativados*, selecione **Habilitar todos os planos**. Selecione o *Plano 1 do Microsoft Defender para APIs de US$ 200/mês* e selecione **Salvar**. Selecione **Salvar** na parte superior da página e aguarde que as notificações *"Os planos do Defender para sua assinatura foram salvos com sucesso!"* sejam exibidas.

1. Selecione a guia **Configurações e monitoramento** na área Configurações (ao lado de Salvar).

1. Revise as extensões de monitoramento. Elas incluem configurações para Máquinas virtuais, Contêineres e Contas de armazenamento.

1. Selecione o botão **Continuar** ou feche a página "Configurações e monitoramento" selecionando o 'X' no canto superior direito da página.

1. Feche a página de configurações selecionando o 'X' no canto superior direito da página para retornar às **Configurações do ambiente**.

<!---1. Select the Log analytics workspace you created earlier *uniquenameDefender* to review the available options and pricing.

1. Select **Enable all plans** (to the right of Select Defender plan) and then select **Save**. Wait for the *"Microsoft Defender plan for workspace uniquenameDefender were saved successfully!"* notification to appear.

    >**Note:** If the page is not being displayed, refresh your Edge browser and try again.

1. Close the Defender plans page by selecting the 'X' on the upper right of the page to go back to the **Environment settings**. --->

### Tarefa 2: Entender o painel do Microsoft Defender para Nuvem

1. Na barra de pesquisa do portal do Azure, digite *Defender* e selecione **Microsoft Defender para Nuvem**.

1. No menu de navegação à esquerda do Microsoft Defender para Nuvem, na seção *Geral*, selecione **Visão geral**.

1. A folha Visão geral apresenta uma exibição unificada da postura de segurança e inclui vários pilares independentes de segurança na nuvem, como Postura de segurança, Conformidade regulatória, Proteções de carga de trabalho, Gerenciador de Firewall, Inventário e Proteção de Informações (versão prévia). Cada um desses pilares também tem um painel dedicado, permitindo insights e ações mais detalhados sobre essa vertical, proporcionando fácil acesso e melhor visibilidade para os profissionais de segurança.

    >**Observação:** a barra de menu superior permite visualizar e filtrar assinaturas clicando no botão Assinaturas. Neste laboratório, usaremos apenas uma, mas escolher assinaturas diferentes/adicionais ajustará a interface para refletir a postura de segurança das assinaturas selecionadas

1. Clique no link do ícone **Novidades** – uma nova guia abrirá com as notas de versão mais recentes, onde você pode ficar a par dos novos recursos, correções de bugs e muito mais.

    >**Observação:** os números de alto nível no menu superior; essa exibição permite que você veja um resumo de suas assinaturas, recomendações ativas e alertas de segurança, além das contas de nuvem conectadas.

1. Na barra de menus superior, selecione **Assinaturas do Azure **. As configurações do ambiente abrirão e você poderá escolher entre as assinaturas disponíveis.

1. Retorne à página **Visão geral** e examine o bloco **Postura de segurança**. Você pode ver sua *Classificação de segurança* junto com o número de controles e recomendações concluídos. Selecionar esse bloco redirecionará você para uma exibição detalhada das assinaturas

1. No bloco **Conformidade regulatória**, você pode obter insights sobre sua postura de conformidade com base na avaliação contínua de ambientes de nuvem híbrida e do Azure. Este bloco mostra os seguintes padrões, que são o parâmetro de comparação de Segurança de Nuvem da Microsofte e o padrão regulatório de conformidade mais baixo. Para exibir os dados, primeiro precisamos adicionar políticas de segurança.

1. Selecionar este bloco irá redirecionar você para o painel de **Conformidade regulatória**, onde você pode adicionar padrões adicionais e explorar os atuais.

1. Continuaremos explorando a **Postura de segurança** do *Microsoft Defender para Nuvem* e a **Conformidade regulatória** no próximo exercício.

## Prossiga para o Exercício 2
