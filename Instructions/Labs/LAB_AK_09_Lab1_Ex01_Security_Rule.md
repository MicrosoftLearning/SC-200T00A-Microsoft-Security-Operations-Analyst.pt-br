---
lab:
  title: 'Exercício 1: modificar uma regra de segurança da Microsoft'
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 9 — Laboratório 1 — Exercício 1 — Modificar uma regra de segurança da Microsoft

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex1.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você deve aprender a detectar e mitigar ameaças usando o Microsoft Sentinel. Primeiro, você precisa filtrar os alertas vindos do Defender para Nuvem para o Microsoft Sentinel, por Severidade.

>**Importante:** os exercícios de laboratório para o Roteiro de Aprendizagem 9 estão em um ambiente *independente*. Se você sair do laboratório antes de concluí-lo, será necessário executar as configurações novamente.

### Tempo estimado para concluir este laboratório: 10 minutos

### Tarefa 1: ativar uma regra de segurança da Microsoft

Nesta tarefa, você ativará uma regra de segurança da Microsoft.

>**Observação:** o Microsoft Sentinel foi pré-implantado em sua assinatura do Azure com o nome **defenderWorkspace** e as soluções necessárias do *hub de conteúdo* foram instaladas.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Microsoft Edge, navegue até o portal do Azure em (<https://portal.azure.com>).

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o **defenderWorkspace** do Microsoft Sentinel.

1. Na área Configurações, selecione **Análise**.

1. Clique no botão **+ Criar** na barra de comandos e selecione **Regra de criação de incidentes da Microsoft**.

1. Em *Nome*, insira **Criar incidentes com base no Defender para Nuvem**.

1. Role para baixo e em *Serviço de segurança da Microsoft* selecione **Microsoft Defender para Nuvem**.

1. Em *Filtrar por severidade*, selecione a opção *Personalizado* e selecione **Baixo**, **Médio** e **Alto** para o nível de severidade e volte para a regra.

1. Clique no botão **Avançar: resposta automatizada** e, em seguida, clique no botão **Avançar: Examinar e criar**.

1. Revise as alterações feitas e clique no botão **Salvar**. A regra do Analytics será salva e incidentes serão criados se houver um Alerta no Defender para Nuvem.

1. Agora você terá um tipo de alerta *Fusion* e um *Segurança da Microsoft*.

## Prossiga para o Exercício 2
