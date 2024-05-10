---
lab:
  title: Exercício 4 – Conectar o Defender XDR ao Microsoft Sentinel usando conectores de dados
  module: Learning Path 6 - Connect logs to Microsoft Sentinel
---

# Roteiro de Aprendizagem 6 – Laboratório 1 – Exercício 4 – Conectar o Defender XDR ao Microsoft Sentinel usando conectores de dados

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex4.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implantou o Microsoft Defender XDR e o Microsoft Sentinel. Você precisa se preparar para a Plataforma de Operações de Segurança Unificada conectando o Microsoft Sentinel ao Defender XDR. A próxima etapa será instalar a solução do Hub de Conteúdo do Defender XDR e implantar o conector de dados do Defender XDR no Microsoft Sentinel.

### Tarefa 1: Microsoft Defender XDR

Nesta tarefa, você implantará o conector do Microsoft Defender XDR.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Microsoft Edge, navegue até o portal do Azure em (<https://portal.azure.com>).

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o workspace do Microsoft Sentinel que você criou anteriormente.

1. No menu esquerdo do Microsoft Sentinel, role para baixo até a seção **Gerenciamento de conteúdo** e selecione **Hub de conteúdos**.

1. No *Hub de Conteúdo*, pesquise a solução do **Microsoft Defender XDR** e selecione-a na lista.

1. Na página de detalhes da solução do *Microsoft Defender XDR*, selecione **Instalar**.

1. Quando a instalação for concluída, pesquise a solução do **Microsoft Defender XDR** e selecione-a.

1. Na página de detalhes da solução do *Microsoft Defender XDR*, selecione **Gerenciar**

>**Observação:** A solução *Microsoft Defender XDR* instala o conector de dados *Microsoft Defender XDR*, consultas de busca, Pastas de Trabalho e regras de análise.

1. Marque a caixa de seleção do Conector de dados *Microsoft Defender XDR* e selecione **Abrir página do conector**.

1. Na seção de *Configuração*, na guia *Instruções*, **desmarque** a caixa de seleção *Desativar todas as regras de criação de incidentes da Microsoft para esses produtos. Recomendado* e selecione o botão **Conectar incidentes e alertas**.

1. Você deve ver uma mensagem informando que a conexão foi bem-sucedida.

## Você concluiu o laboratório
