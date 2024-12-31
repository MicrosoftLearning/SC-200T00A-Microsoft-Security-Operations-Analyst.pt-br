---
lab:
  title: 'Exercício 8: investigar incidentes'
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 9 – Laboratório 1 – Exercício 8 – Investigar Incidentes

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex8.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você já criou as regras Agendado e Análise de segurança da Microsoft. As regras de Análise de anomalias e fusão também estão habilitadas em seu ambiente. Agora é a hora de investigar os Incidentes criados por eles.

Um incidente pode incluir vários alertas. El é uma agregação de todas as evidências relevantes para uma investigação específica. As propriedades relacionadas aos alertas, como severidade e status, são definidas no nível do incidente. Depois de informar ao Microsoft Sentinel quais tipos de ameaças você está procurando e como encontrá-las, você pode monitorar as ameaças detectadas investigando incidentes.

>**Importante:** os exercícios de laboratório para o Roteiro de Aprendizagem 9 estão em um ambiente *independente*. Se você sair do laboratório antes de concluí-lo, será necessário executar as configurações novamente.

### Tempo estimado para concluir este laboratório: 30 minutos

### Tarefa 1: investigar um incidente

Nesta tarefa, você investigará um incidente.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Edge, acesse o portal do Azure em <https://portal.azure.com>.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione seu workspace do Microsoft Sentinel.

1. Selecione a página **Incidentes**.

1. Revise a lista de incidentes.

    >**Observação:** as regras de Análise estão gerando alertas e incidentes na mesma entrada de log específica. Lembre-se de que isso foi feito na configuração do *Agendamento de consultas* para gerar mais alertas e incidentes a serem utilizados no laboratório.
  
1. Selecione um dos incidentes do **RegKey de inicialização**.

1. Analise os detalhes do incidente na folha direita que foi aberta. Role a página para baixo e clique no botão **Exibir todos os detalhes**.

1. Se o pop-up "Nova experiência de incidente" for exibido, siga os prompts lendo as informações que aparecem ao clicar no botão **Avançar**.

1. Na folha esquerda do incidente, altere o Status para **Ativo** e selecione **Aplicar**.

1. Role para baixo até a área *Tags*, selecione **+**, digite **RegKey** e selecione **OK**.

1. Role para baixo e, na caixa *Escreva um comentário...*, digite: *Vou pesquisar isso* e selecione o ícone **>** para enviar o novo comentário.

1. Oculte a folha esquerda selecionando o ícone **<<** ao lado do proprietário.

1. Revise a janela **Linha do tempo do incidente**. Selecione o botão **Ações de Incidente** no canto superior direito e, em seguida, **Executar guia estratégico**. Você verá o guia estratégico *PostMessageTeams-OnIncident*. Esta opção vai ajudar a executar guias estratégicos manualmente.

1. Feche a folha *Executar guia estratégico no incidente* selecionando o ícone **x** no canto superior direito.

1. Revise a janela **Entidades**. Pelo menos a entidade *Host* que mapeamos na consulta KQL do exercício anterior deve aparecer. **Dica:** se nenhuma entidade aparecer, atualize a página.

1. Selecione o novo botão **Tarefas** na barra de comandos.

1. Selecione **+ Adicionar tarefa**, digite **Revisar quem é o proprietário da máquina** na caixa Título e selecione **Salvar**.

1. Feche a folha *Tarefas de incidente* clicando no ícone **x** no canto superior direito.

1. Selecione o novo botão **Log de atividades** na barra de comandos.

1. Analise as ações que você tomou durante este exercício.

1. Feche a folha *Log de atividades do incidente* selecionando o ícone **x** no canto superior direito.

1. Na folha esquerda quase oculta, selecione o ícone do usuário chamado **Não atribuído**. A nova experiência de incidente permite mudanças rápidas a partir daqui.

1. Selecione **Atribuir a mim** e, em seguida, role para baixo para selecionar **Aplicar** a fim de salvar as alterações.

1. Expanda a folha esquerda selecionando o ícone **>>**. Depois, selecione o botão **Investigar**.

    >**Dica:** se os ícones forem muito pequenos para a tela, selecione **(+)** para ampliá-los.

1. **Passe o mouse** sobre o ícone da entidade WINServer e aguarde até que novas *consultas de exploração* sejam exibidas. Parece que a opção *Alertas relacionados* têm mais dados sobre ela. Selecione o nome da consulta de exploração **Alertas relacionados** para trazê-los para o gráfico de investigação ou selecione **Eventos >** para investigá-los com uma consulta KQL.

1. Feche a janela Consulta selecionando o ícone **X** no canto superior direito para voltar à página *Investigação*.

1. Agora selecione a entidade **WINServer**, em que uma janela à direita abrirá para exibir informações mais detalhadas. Revise a página **Informações**.

1. Selecione o botão **Linha do tempo**. Passe o mouse sobre os incidentes para ver quais eventos no gráfico ocorreram em que ponto no tempo.

1. Selecione o botão **Entidades** e examine as *Entidades* e os *Alertas* relacionados ao *WINServer*.

1. Feche o gráfico de investigação selecionando o ícone **X** no canto superior direito da página.

1. De volta à página do incidente, no painel esquerdo, selecione **Status ativo** e selecione **Fechado**. 

1. Na lista suspensa *Selecionar classificação*, revise as diferentes opções. Depois disso, selecione **Verdadeiro positivo – atividade suspeita** e, em seguida, selecione **Aplicar**.

## Prossiga para o Exercício 9
