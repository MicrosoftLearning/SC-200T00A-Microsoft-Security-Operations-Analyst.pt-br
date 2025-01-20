---
lab:
  title: 'Exercício 9: criar analisadores ASIM'
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 9 – Laboratório 1 – Exercício 9 – Implantar analisadores ASIM

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex9.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você precisa modelar analisadores ASIM para um evento de registro específico do Windows. Esses analisadores serão finalizados posteriormente seguindo a referência do esquema de normalização de eventos de registro [Advanced Security Information Model (ASIM)](https://docs.microsoft.com/azure/sentinel/registry-event-normalization-schema).

>**Importante:** os exercícios de laboratório para o Roteiro de Aprendizagem 9 estão em um ambiente *independente*. Se você sair do laboratório antes de concluí-lo, será necessário executar as configurações novamente.

### Tempo estimado para concluir este laboratório: 30 minutos

### Tarefa 1: Implantar os analisadores ASIM do esquema de registro

Nessa tarefa, você revisará os analisadores de esquema de registro incluídos na implantação do Microsoft Sentinel.

>**Observação:** o Microsoft Sentinel foi pré-implantado em sua assinatura do Azure com o nome **defenderWorkspace** e as soluções necessárias do *Hub de Conteúdo* foram instaladas.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Microsoft Edge, acesse o portal do Azure em <https://portal.azure.com>.

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o **defenderWorkspace** do Microsoft Sentinel.

<!--- 1. In the Edge browser, open a new tab (Ctrl+T) and navigate to the Microsoft Sentinel GitHub ASIM page <https://github.com/Azure/Azure-Sentinel/tree/master/ASIM>.

 1. On the right pane, select the **Onboard community content** link. This will open a new tab in the Edge Browser for Microsoft Sentinel GitHub content. **Hint:** You might need to scroll right to see the link. Alternatively, follow this link instead: [Microsoft Sentinel on GitHub](https://github.com/Azure/Azure-Sentinel).

    >**Note:** In the **ASIM** folder you can deploy templates that contain all ASIM parsers, but we will only focus on the Registry Schema.

1. Scroll down and next to **Registry Event**, select the **Deploy to Azure** button.

1. For *Resource Group*, select **RG-Defender** where your Sentinel workspace resides.

1. For *Workspace*, type your Sentinel workspace name, like *uniquenameDefender*.

1. Leave the other default values and select **Review + create**.

1. Select **Create** to deploy the template. Notice the Names of the different resources. 

1. After the deployment completes return to the *Microsoft Sentinel* tab. --->

1. Selecione **Logs** na seção *Geral* do menu de navegação.

1. Abra a folha *Esquema e filtro* selecionando **>>**, se necessário.

1. Selecione a guia **Funções** (ao lado das guias Tabelas e Consultas). **Dica:** talvez seja necessário selecionar o ícone de reticências **(...)** para selecionar a guia.

1. Na barra *Pesquisa* digite **registro** e role para baixo pelas funções do analisador ASIM até ver o seguinte *_Im_RegistryEvent_MicrosoftWindowsEventxxx*para Microsoft Windows sob o título *Microsoft Sentinel* .

    >**Observação:** Estamos usando xxx no nome da função do analisador ASIM para contabilizar alterações de versão. No momento em que esse laboratório foi atualizado, a função era _Im_RegistryEvent_MicrosoftWindowsEvent*V02*.

1. Passe o mouse sobre a função **_Im_RegistryEvent_MicrosoftWindowsEventxxx** ASIM e selecione **Carregar o código da função** na janela pop-up.

1. Revise o KQL que está analisando o ID de evento 4657 para simplificar sua análise dos dados no workspace do Microsoft Sentinel.

    >**Dica:** Digitar ctrl+f na janela de código traz *Find* e faz a busca por *EventID: 4657* muito fácil.

1. Em *Logs*, abra uma guia Nova consulta.

1. Volte para a folha *Esquema e Filtro* e agora passe o mouse sobre **_Im_RegistryEvent_MicrosoftWindowsEventxxx** *Analisador de filtragem ASIM de evento de registro para eventos do Microsoft Windows e eventos de segurança* e selecione **Usar no editor**.

1. **Execute** a consulta da função ASIM. Se você concluiu os exercícios de laboratório anteriores, verá resultados e mensagens noerror.

## Prossiga para o Exercício 10
