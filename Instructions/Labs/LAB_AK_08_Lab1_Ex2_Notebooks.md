---
lab:
  title: 'Exercício 2: busca de ameaças usando notebooks com o Microsoft Sentinel'
  module: Learning Path 8 - Perform threat hunting in Microsoft Sentinel
---

# Roteiro de aprendizagem 8, Laboratório 1, Exercício 2: busca de ameaças usando notebooks com o Microsoft Sentinel

## Cenário do laboratório

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você precisa explorar os benefícios da busca de ameaças com os Notebooks do Microsoft Sentinel. Você pode usar notebooks para:

- Realizar análises que não são fornecidas de forma imediata no Microsoft Sentinel, como alguns recursos de machine learning do Python.
- Criar visualizações de dados que não são fornecidas de forma imediata no Microsoft Sentinel, como linhas de tempo personalizadas e árvores de processo.
- Integrar fontes de dados fora do Microsoft Sentinel, como um conjunto de dados local.

>**Observação:** uma **[simulação de laboratório interativa](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Hunt%20for%20threats%20using%20notebooks%20in%20Microsoft%20Sentinel)** está disponível e permite que você clique neste laboratório no seu próprio ritmo. Você pode encontrar pequenas diferenças entre a simulação interativa e o laboratório hospedado, mas os principais conceitos e ideias que estão sendo demonstrados são os mesmos. 

### Tarefa 1: explorar notebooks

Nesta tarefa, você explorará o uso de notebooks no Microsoft Sentinel.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Edge, acesse o portal do Azure em https://portal.azure.com.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione seu workspace do Microsoft Sentinel.

1. No workspace do Microsoft Sentinel, selecione **Notebooks** na área *Gerenciamento de ameaças*.

1. Agora, você precisa criar um workspace do AzureML. Selecione **Configurar o Azure Machine Learning** e, em seguida, clique no botão **Criar novo workspace do Azure ML** na barra de comandos.

1. Na caixa Assinatura, selecione sua assinatura.

1. Selecione **Criar novo** para o Grupo de recursos e insira *RG-MachineLearning* para Nome e selecione **OK**. 

1. Na seção Detalhes do workspace, faça o seguinte:

     - Dê um nome exclusivo ao workspace.
     - Mantenha **Leste dos EUA** como valor padrão para *Região*.
     - Mantenha as informações padrão da Conta de armazenamento, do Key Vault e do Application Insights.
     - A opção de Registro de contêiner pode permanecer como **Nenhum**.

1. Na parte inferior da página, selecione **Examinar + criar**. Quando vir a mensagem *"Validação aprovada"*, selecione **Criar**. 

     >**Observação:** pode levar alguns minutos para implantar o workspace do Machine Learning.

1. Depois que a mensagem *Sua implantação está concluída* for exibida, retorne ao portal do Microsoft Sentinel.

1. Selecione **Notebooks** novamente e depois selecione a guia **Modelos** na barra de comandos do meio. 

1. Selecione **Um guia de introdução para notebooks de ML do Microsoft Sentinel**. 

1. No painel direito, role para baixo e selecione o botão **Criar do modelo**. Revise as opções padrão e depois selecione **Salvar**.

1. Quando o salvamento estiver concluído, selecione o botão **Iniciar notebook**. Isso o levará ao estúdio do Microsoft Azure Machine Learning.

1. Selecione **Fechar** se uma janela informativa aparecer no estúdio do Microsoft Azure Machine Learning.

1. Na barra de comandos, à direita do seletor **Instância de computação:**, selecione o símbolo **+** para criar uma nova instância de computação. **Dica:** ele pode estar escondido dentro do ícone de reticências **(...)**.

     >**Observação:** você pode ter mais espaço na tela ocultando a folha esquerda do estúdio do Azure ML selecionando as 3 linhas no canto superior esquerdo, bem como os Arquivos de notebooks selecionando o ícone **<<**.

1. No campo *Nome da computação*, digite um nome exclusivo. Isso identificará sua instância de computação.

1. Role para baixo e selecione a primeira opção disponível. **Dica:** tipo de carga de trabalho: desenvolvimento em notebooks e testes leves.

1. Selecione o botão **Criar** na parte inferior da tela. Feche qualquer janela de comentário que possa aparecer. Isso levará alguns minutos, você verá uma notificação (ícone de sino) depois da conclusão, e o ícone esquerdo da *Instância de computação* passará de azul para verde.

1. Depois que a computação tiver sido criada e executada, verifique se o kernel a ser usado é *Python 3.8 – AzureML*. **Dica:** isso é mostrado à direita da barra de comandos.

1. Clique no botão **Autenticar** e aguarde até a conclusão da autenticação.

1. Limpe todos os resultados do notebook selecionando **Limpar todas as saídas** da barra de comandos e siga o tutorial de *Introdução*. **Dica:** isso pode ser encontrado selecionando as reticências (...) na barra de comandos.

>**Observação:** se não for possível concluir as etapas acima para acessar o notebook, você poderá segui-lo em sua página de visualização do GitHub. [Introdução aos notebooks do Azure ML e ao Microsoft Sentinel](https://nbviewer.org/github/Azure/Azure-Sentinel-Notebooks/blob/master/A%20Getting%20Started%20Guide%20For%20Azure%20Sentinel%20ML%20Notebooks.ipynb) 

## Você concluiu o laboratório.
