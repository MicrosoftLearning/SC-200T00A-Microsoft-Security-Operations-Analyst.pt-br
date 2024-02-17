---
lab:
  title: 'Exercício 10: criar pastas de trabalho'
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 7, Laboratório 1, Exercício 10: criar pastas de trabalho

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex10.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Depois de conectar suas fontes de dados ao Microsoft Sentinel, você pode visualizar e monitorar os dados usando a adoção do Microsoft Sentinel dos workbooks do Azure Monitor, que oferece versatilidade na criação de painéis personalizados. 

O Microsoft Sentinel permite que você crie pastas de trabalho personalizadas em seus dados e também vem com modelos de pasta de trabalho internos para que você possa obter insights rapidamente em seus dados assim que você conectar uma fonte de dados.

>**Observação:** uma **[simulação de laboratório interativa](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Create%20workbooks)** está disponível e permite que você clique neste laboratório no seu próprio ritmo. Você pode encontrar pequenas diferenças entre a simulação interativa e o laboratório hospedado, mas os principais conceitos e ideias que estão sendo demonstrados são os mesmos. 


### Tarefa 1: explorar modelos de pasta de trabalho

Nesta tarefa, você explorará os modelos de pasta de trabalho do Microsoft Sentinel.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Edge, acesse o portal do Azure em https://portal.azure.com.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione seu workspace do Microsoft Sentinel.

1. Selecione **Pastas de trabalho** na folha esquerda *Gerenciamento de ameaças*. A guia *Modelos* é selecionada por padrão.

1. Pesquise e selecione a pasta de trabalho de modelo de **Atividade do Azure**. No painel direito, role para baixo e selecione o botão **Exibir modelo**.

1. Revise o conteúdo da pasta de trabalho. Ele mostra insights de suas operações de assinatura do Azure coletando e analisando os dados do Log de atividades.

1. Feche a pasta de trabalho selecionando o **X** no canto superior direito.


### Tarefa 2: salvar e modificar um modelo de pasta de trabalho

Nesta tarefa, você salvará um modelo de pasta de trabalho e o modificará.

1. Você deve estar de volta à guia **Microsoft Sentinel – Pastas de trabalho – Modelos**. Role para baixo novamente e clique no botão **Salvar** da pasta de trabalho *Atividade do Azure*. 

1. Mantenha **Leste dos EUA** como valor padrão para *Região* e selecione **OK**.

1. Selecione o botão **Ver a pasta de trabalho salva**.

1. Selecione **Editar** na barra de comandos para habilitar alterações na pasta de trabalho.

1. Role para baixo até a área *Atividades do chamador ao longo do tempo*, observe a cor da coluna *Atividades*, pois vamos formatar essas colunas. Selecione o botão **Editar** abaixo da grade.

1. Selecione o botão **Configurações de coluna**, localizado à direita da barra de comandos *Executar consulta*. **Dica:** este botão só aparece se houver dados da consulta KQL.

1. Na folha *Editar configurações de coluna* exibida, em *Colunas*, selecione **Atividades**.

1. Altere o valor de *Renderizador de coluna* para **Mapa de calor**. Em *Paleta de cores*, role para baixo até selecionar a **categoria de 32 cores**.

1. Selecione **Salvar e fechar**. Observe a alteração na coluna *Atividades*.

1. Selecione **Edição concluída** na parte inferior da consulta (não no menu superior).

1. Agora selecione **Edição concluída** no menu superior e selecione o ícone **Salvar**. 

1. Feche a pasta de trabalho selecionando o **X** no canto superior direito.


### Tarefa 3: criar uma pasta de trabalho

Nesta tarefa, você criará uma nova pasta de trabalho com visualizações avançadas.

1. Você deve estar de volta à área **Pastas de trabalho** do portal do Microsoft Sentinel.

1. Selecione **+ Adicionar pasta de trabalho** para criar uma nova pasta de trabalho do zero. 

    >**Observação:** embora seja uma nova pasta de trabalho, um modelo de inicialização é usado.

1. Para editar a pasta de trabalho, selecione **Editar**.

1. Selecione o botão **Editar** abaixo do primeiro parágrafo da pasta de trabalho.

1. Digite *# Minha pasta de trabalho* em uma nova linha na parte superior de *## Nova pasta de trabalho*.

1. Selecione **Edição concluída** na parte inferior desta seção *Editando item de texto: texto – 2*. Observe que o cabeçalho aumentou de tamanho e o nome foi alterado.

1. Selecione **Editar** abaixo do único gráfico de barras visível.

1. Revise a instrução KQL que fornece uma instrução *union* de contagens em todas as tabelas.

1. Role para baixo e selecione **Edição concluída** no menu inferior para o novo *Item de consulta de edição: consulta – 2*.

1. Selecione as reticências **...** ao lado do botão *Editar* do gráfico de barras, selecione **+ Adicionar** e depois **Adicionar consulta**.

1. Digite **SecurityEvent** na caixa de consulta.

1. Altere o *Intervalo de tempo* para a **Última hora**.

1. Mude a *Visualização* para **Gráfico de tempo**.

1. Selecione a guia **Estilo** na barra de comandos da consulta.

1. Selecione a caixa **Personalizar a largura deste link**.

1. Defina a *Largura percentual* como **25** e a *Largura máxima* como **25**.

1. Agora selecione a guia **Configurações avançadas** na barra de comandos da consulta.

1. Selecione a caixa **Mostrar ícone de atualização quando não estiver editando**. 

1. Role para baixo e selecione **Edição concluída** no menu inferior, para o novo *Item de consulta de edição: consulta – 2*.

1. Role para baixo e, na parte inferior da pasta de trabalho, selecione **+ Adicionar** e, em seguida, **Adicionar consulta**.

1. Digite **SecurityEvent** na caixa de consulta.

1. Altere o *Intervalo de tempo* para a **Última hora**.

1. Altere *Visualização* para **Grade**.

1. Na barra de comandos da consulta, selecione **Estilo**.

1. Selecione a caixa **Personalizar a largura deste link**.

1. Defina a *Largura percentual* como **75** e a *Largura máxima* como **75**.

1. Role para baixo e selecione **Edição concluída** no menu inferior, para o novo *Item de consulta de edição: consulta – 3*.

1. Selecione **Edição concluída** na barra de comandos superior da pasta de trabalho.

1. Selecione o ícone **Salvar**, altere o *Título* para **Minha pasta de trabalho**.

1. Selecione o grupo de recursos **RG-Defender**, se necessário, e deixe outros valores como padrão.

1.  Selecione **Aplicar** para confirmar as alterações. 

1. Feche a pasta de trabalho selecionando o **X** no canto superior direito ou selecione **Pastas de trabalho** no portal do Microsoft Sentinel.

1. Na página *Pastas de trabalho*, selecione a guia **Minhas pastas de trabalho**.

1. Selecione a pasta de trabalho que você acabou de criar, **Minha pasta de trabalho**.

1. No painel direito, selecione **Exibir pasta de trabalho salva** para revisar sua pasta de trabalho.

## Prossiga para o Exercício 11
