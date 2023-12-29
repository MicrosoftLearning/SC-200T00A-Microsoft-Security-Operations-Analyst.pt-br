---
lab:
  title: 'Exercício 11: usar repositórios no Microsoft Sentinel'
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 7, Laboratório 1, Exercício 11: usar repositórios no Microsoft Sentinel

## Cenário do laboratório

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você já criou as regras Agendado e Análise de segurança da Microsoft.  Você precisa centralizar as regras analíticas em um repositório do Azure DevOps.  Em seguida, conecte o Sentinel ao repositório do Azure DevOps e importe o conteúdo. 

>**Observação:** uma **[simulação de laboratório interativa](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Use%20repositories%20in%20Microsoft%20Sentinel)** está disponível e permite que você clique neste laboratório no seu próprio ritmo. Você pode encontrar pequenas diferenças entre a simulação interativa e o laboratório hospedado, mas os principais conceitos e ideias que estão sendo demonstrados são os mesmos. 


### Tarefa 1: criar e exportar uma regra analítica

Nesta tarefa, você habilitará a análise do comportamento da entidade no Microsoft Sentinel.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione seu workspace do Microsoft Sentinel.

1. Selecione **Análise** na área de *Configuração*, na folha esquerda.

1. Selecione a regra **RegKey de inicialização** criada anteriormente.

1. Selecione **Exportar** na barra de ferramentas. **Dica:** talvez seja necessário selecionar o ícone de reticências **(...)** para exibi-la.

1. A regra é exportada para um arquivo de texto chamado *Azure_Sentinel_analytic_rule.json*.

1. Selecione **Abrir arquivo** abaixo do nome do arquivo baixado e, em seguida, selecione **Mais aplicativos**.

1. Selecione **Bloco de notas** e depois selecione **OK**.

1. Revise o modelo do Azure Resource Manager e feche-o quando terminar.


### Tarefa 2: criar nosso ambiente do Azure DevOps

Nesta tarefa, você criará um repositório do Azure DevOps.

1. Abra outra guia no navegador e navegue até (https://aexprodcus1.vsaex.visualstudio.com/me?mkt=en-US).

1. Na página *Precisamos de mais alguns detalhes*, selecione **Continuar**.

1. Na página *Introdução ao Azure DevOps*, selecione **Criar nova organização** e, em seguida, selecione **Continuar**.

1. Na página *Quase concluído...*, insira um nome para sua organização do DevOps que você não gostaria de usar no futuro, como o prefixo do locatário. **Dica:** ele pode ser encontrado na guia Recursos do seu laboratório (WWLx...).

1. *Insira os caracteres que você vê* e, em seguida, clique em **Continuar**.

1. Na página *Criar um projeto para começar*, insira **Meu conteúdo do Sentinel** e então selecione **Criar projeto**.

1. Navegue até **Repos** no painel esquerdo.

1. Na parte inferior da página, na área *Inicializar ramificação principal com LEIAME ou gitignore*, selecione **Inicializar**.

1. A página deve mostrar os Arquivos para o Repo.  o único arquivo é LEIAME.me.

1. Na folha Arquivos (ao lado direito da página), a barra de ferramentas inclui as opções *Configurar compilação*, *Clonar*... Selecione o ícone de dois pontos **(:)** para mostrar mais opções.

1. Selecione **Carregar Arquivos**.

1. Selecione **Navegar** e depois selecione o arquivo **Azure_Sentinel_analytic_rule.json** no diretório *Downloads* .

1. Selecione **Confirmar**.

1. Selecione **Azure DevOps** no canto superior esquerdo da página.  Isso exibe sua organização e projetos.

1. Selecione **Configurações da organização** no canto inferior esquerdo da página.

1. Selecione **Políticas** na área *Segurança* da folha esquerda.

1. **Ative** o *Acesso a aplicativos de terceiros via OAuth* na área *Políticas de conexão de aplicativo*.


### Tarefa 3: conectar o Sentinel ao Azure DevOps.

1. Selecione a guia *Portal do Azure*/*Microsoft Sentinel* em seu navegador.

1. No Microsoft Sentinel, selecione **Repositórios (Visualização)** na seção *Gerenciamento de conteúdo*.

1. Selecione o botão **+ Adicionar novo** na barra de ferramentas.

1. Para o nome, insira **Meu conteúdo**.

1. Para Controle do código-fonte, selecione **Azure DevOps**.

1. Selecione **Autorizar**. Role a solicitação de permissões para baixo e selecione **Aceitar**.

1. Selecione a organização que você criou anteriormente (por exemplo, WWLx...).

1. Selecione o Projeto que você criou anteriormente, *Meu conteúdo do Sentinel*.

1. Selecione o Repositório que você criou anteriormente, *Meu conteúdo do Sentinel*. **Dica:** talvez seja necessário rolar para baixo na lista suspensa para ver o repositório.

1. Selecione a ramificação **principal**. **Dica:** talvez seja necessário rolar para baixo na lista suspensa para ver a ramificação.

1. Selecione todos os tipos de conteúdo.

1. Em seguida, selecione **Criar**.

1. Volte para o workspace do Microsoft Sentinel, se necessário

1. Vá para a página *Repositórios (Visualização)* e selecione **Atualizar**. Aguarde até que o *Status da última implantação* seja *Falha*.  

    >**Observação:** o status *Falha* é devido a limitações no ambiente de laboratório hospedado. Você normalmente veria *Sucedido*. Em seguida, você pode ver em *Análise* a regra importada *Regra do Azure DevOps*.


## Você concluiu o laboratório.
