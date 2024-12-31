---
lab:
  title: 'Exercício 4: explorar a análise de comportamento da entidade'
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 9 — Laboratório 1 — Exercício 4 — Explorar análise de comportamento de entidade

## Cenário do laboratório

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você já criou as regras Agendado e Análise de segurança da Microsoft.

Você precisa configurar o Microsoft Sentinel para executar a Análise de comportamento de entidade para descobrir anomalias e fornecer páginas de análise de entidade.

>**Importante:** os exercícios de laboratório para o Roteiro de Aprendizagem 9 estão em um ambiente *independente*. Se você sair do laboratório antes de concluí-lo, será necessário executar as configurações novamente.

### Tempo estimado para concluir este laboratório: 15 minutos

### Tarefa 1: explorar o comportamento da entidade

Nesta tarefa, você explorará a Análise de comportamento da entidade no Microsoft Sentinel.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Edge, acesse o portal do Azure em <https://portal.azure.com>.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione seu workspace do Microsoft Sentinel.

1. Selecione a página **Comportamento da entidade**.

1. No pop-up de *Configurações de comportamento da entidade*, selecione **Definir UEBA**.

1. Na aba *Configurações* em *Análise de comportamento da entidade*, role para baixo na seção *Anomalias*, leia o parágrafo e verifique que o *botão* está *Ligado*.

1. Selecione o link **Ir para análise para configurar as anomalias**.

### Tarefa 2: confirmar e revisar regras de anomalias

Nesta tarefa, você confirmará se as regras de análise de anomalias estão habilitadas.

1. Você deve estar agora na página *Análise*, na guia *Anomalias*.

1. Confirme se a coluna de status das regras é *Habilitado*.

1. Selecione qualquer regra e, em seguida, selecione **Editar** na folha da regra.

1. Revise as informações da guia *Geral*. Observe que o *Modo* é **Produção** e, em seguida, selecione **Avançar: Configuração**.

1. Revise as informações da guia *Configuração*. Observe que você não pode alterar o **Limite de pontuação de anomalias**.

1. Em seguida, selecione **X** no canto superior direito para sair do assistente de regras de Análise.

1. Role para a direita até a regra de análise selecionada até ver e selecionar o ícone de reticências **(...)**.

1. Selecione **Duplicar** e role para a esquerda para revisar a nova regra com a guia **FLGT** no início do nome.

1. Selecione a regra **FLGT** e, em seguida, selecione **Editar** na folha da regra.

1. Revise as informações da guia *Geral*. Observe que o *Modo* é **Disponibilizar versão piloto** e, em seguida, selecione **Avançar: Configuração**.

1. Revise as informações da guia *Configuração*. Observe que você agora pode alterar o **Limite de pontuação de anomalias**.

1. Defina o valor como **1** e então selecione **Avançar: Enviar comentários**.

1. Selecione **Avançar: Revisar e criar** e depois **Salvar** para atualizar a regra.

    >**Observação:** você pode atualizar a regra **Disponibilizar versão piloto** para **Produção** alterando a configuração dessa regra e salvando as alterações. A regra de **Produção** se tornará a regra **Disponibilizar versão piloto** posteriormente.

## Prossiga para o Exercício 5
