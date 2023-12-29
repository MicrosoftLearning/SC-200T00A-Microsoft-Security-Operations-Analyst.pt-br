---
lab:
  title: 'Exercício 1: modificar uma regra de segurança da Microsoft'
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 7, Laboratório 1, Exercício 1: modificar uma regra de segurança da Microsoft

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex1.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você deve aprender a detectar e mitigar ameaças usando o Microsoft Sentinel. Primeiro, você precisa filtrar os alertas vindos do Defender para Nuvem para o Microsoft Sentinel, por Severidade. 

>**Observação:** uma **[simulação de laboratório interativa](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Modify%20a%20Microsoft%20Security%20rule)** está disponível e permite que você clique neste laboratório no seu próprio ritmo. Você pode encontrar pequenas diferenças entre a simulação interativa e o laboratório hospedado, mas os principais conceitos e ideias que estão sendo demonstrados são os mesmos. 


### Tarefa 1: ativar uma regra de segurança da Microsoft

Nesta tarefa, você ativará uma regra de segurança da Microsoft.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Microsoft Edge, acesse o portal do Azure em (https://portal.azure.com).

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o workspace do Microsoft Sentinel que você criou nos laboratórios anteriores.

1. Na área Configurações, selecione **Análise**.

1. Clique no botão **+ Criar** na barra de comandos e selecione **Regra de criação de incidentes da Microsoft**.

1. Em *Nome*, insira **Criar incidentes com base no Defender para Ponto de Extremidade**.

1. Role para baixo e, em *Serviço de segurança da Microsoft*, selecione **Microsoft Defender para Ponto de Extremidade**.

1. Em *Filtrar por severidade*, selecione a opção *Personalizado* e selecione **Baixo**, **Médio** e **Alto** para o nível de severidade e volte para a regra.

1. Clique no botão **Avançar: resposta automatizada** e, em seguida, clique no botão **Avançar: Examinar e criar**.

1. Revise as alterações feitas e clique no botão **Salvar**. A regra de Análise será salva e os incidentes serão criados se houver um alerta no Defender para Ponto de Extremidade.

1. Agora você terá uma *Fusão* e dois tipos de alerta de *Segurança da Microsoft*.

## Prossiga para o Exercício 2
