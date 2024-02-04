---
lab:
  title: 'Exercício 2: mitigar os ataques com o Microsoft Defender para Ponto de Extremidade'
  module: Learning Path 2 - Mitigate threats using Microsoft Defender for Endpoint
---

# Roteiro de aprendizagem 2, Laboratório 1, Exercício 2: mitigar os ataques com o Microsoft Defender para Ponto de Extremidade

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod2_L1_Ex2_10_19.png)

Você é um analista de operações de segurança que trabalha em uma empresa que está implantando o Microsoft Defender para Ponto de Extremidade. Seu gerente planeja integrar alguns dispositivos para fornecer informações sobre as alterações necessárias nos procedimentos de resposta da equipe de Operações de segurança (SecOps).

Para explorar os recursos de mitigação de ataques do Defender para Ponto de Extremidade, você executará dois ataques simulados.

>**Observação:** uma **[simulação de laboratório interativa](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20attacks%20with%20Microsoft%20Defender%20for%20Endpoint)** está disponível e permite que você clique neste laboratório no seu próprio ritmo. Você pode encontrar pequenas diferenças entre a simulação interativa e o laboratório hospedado, mas os principais conceitos e ideias que estão sendo demonstrados são os mesmos.


### Tarefa 1: verificar integração de dispositivos

Nesta tarefa, você confirmará se o dispositivo foi integrado com êxito e criará um alerta de teste.

1. Se você ainda não estiver no portal do Microsoft Defender XDR em seu navegador Microsoft Edge, acesse (https://security.microsoft.com) e faça logon como Administrador do seu locatário.

1. No menu à esquerda, na área **Ativos** , selecione **Dispositivos**. Aguarde até que WIN1 apareça na página Dispositivos antes de continuar. Caso contrário, talvez seja necessário repetir essa tarefa para ver os alertas que serão gerados posteriormente.

    >**Observação:** se você tiver concluído o processo de integração e não vir dispositivos na lista de dispositivos após uma hora, isso pode indicar um problema de integração ou de conectividade.

1. Selecione **Configurações** na barra de menus à esquerda e, na página Configurações, selecione **Pontos de extremidade**.

1. Selecione **Integração** na seção Gerenciamento de dispositivo e verifique se *"Windows 10 e 11"* está selecionado como sistema operacional. A mensagem *"Primeiro dispositivo integrado"* agora mostra *Concluído*.

1. Role para baixo e, na seção *"2. Executar um teste de detecção"*, copie o script do teste de detecção selecionando o botão **Copiar**.  

1. Na barra de pesquisa do Windows da máquina virtual WIN1, digite **CMD** e escolha **Executar como Administrador** no painel direito do aplicativo Prompt de comando. 

1. Quando a janela "Controle de conta de usuário" for exibida, selecione **Sim** para permitir que o aplicativo seja executado. 

1. Cole o script clicando com o botão direito do mouse na janela **Administrador: Prompt de comando** e pressione **Enter** para executá-lo.

    >**Observação:** a janela fecha automaticamente após a execução do script.

### Tarefa 2: ataques simulados

>**Observação:** O laboratório de avaliação e a seção Tutoriais e simulações do portal não estão mais disponíveis. As etapas a seguir são fornecidas somente para referência. Consulte a **[simulação de laboratório interativo](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20attacks%20with%20Microsoft%20Defender%20for%20Endpoint)** para ver uma demonstração dos ataques simulados. Estamos trabalhando para encontrar um substituto para os ataques simulados.

1. No menu esquerdo, em **Pontos de extremidade**, selecione **Avaliação e tutoriais** e depois clique em **Tutoriais e simulações** no lado esquerdo.

1. Selecione a guia **Tutoriais**.

1. Em *Investigação automatizada (backdoor)*, você verá uma mensagem descrevendo o cenário. Abaixo deste parágrafo, clique em **Ler o passo a passo**. Uma nova guia do navegador é aberta, que inclui instruções para executar a simulação.

1. Na nova guia do navegador, localize a seção chamada **Executar a simulação** (página 5, começando na etapa 2) e siga as etapas para executar o ataque. **Dica:** o arquivo de simulação *RS4_WinATP-Intro-Invoice.docm* pode ser encontrado no portal, logo abaixo de **Ler o passo a passo** que você selecionou na etapa anterior, clicando no botão **Obter arquivo de simulação**.

    <!--- 1. Repeat the last 3 steps to run another tutorial, *Automated investigation (fileless attack)*. This is no longer working due to win1 AV --->

### Tarefa 3: investigar os ataques

1. No portal do Microsoft Defender XDR, selecione **Incidentes e alertas** na barra de menus à esquerda e selecione **Incidentes**.

1. Um novo incidente chamado "Várias famílias de ameaças foram detectadas em um ponto de extremidade" está no painel direito. Selecione o nome do incidente para carregar seus detalhes.

    <!---    >**Note:** You should see both *Bloodhound* and Mimikatz* alerts in the **Alerts** pane. In **Assets/Devices**, the *win1* computer will now have a **Risk level** of *High*. --->

1. Selecione o botão **Gerenciar incidente** e uma nova folha de janela será exibida. 

1. Em **Marcas de incidente**, digite "Simulação" e selecione **Simulação (Criar)** para criar uma marca. 

1. Selecione o botão de alternância **Atribuir a** e adicione sua conta de usuário (Eu) como proprietário do incidente. 

1. Em **Classificação**, expanda o menu suspenso. 

1. Em **Atividade esperada e informativa**, selecione **Teste de segurança**. 

1. Adicione quaisquer comentários, se desejar, e selecione **Salvar** para atualizar o incidente e concluir.

1. Analise o conteúdo das guias *História de ataque, Alertas, Ativos, Investigações, Evidência e resposta* e *Resumo*. Dispositivos e Usuários estão na guia *Ativos*. A guia *História do ataque* exibe o *gráfico Incidente*. **Dica:** algumas guias podem estar ocultas devido ao tamanho da tela. Selecione a guia de reticências (...) para que elas apareçam.

    >**Aviso**: Os ataques simulados aqui são uma excelente fonte de aprendizado por meio da prática. Execute apenas os ataques nas instruções fornecidas para este laboratório ao usar o locatário do Azure fornecido pelo curso.  Você pode executar outros ataques simulados *após* este curso de treinamento ser concluído com esse locatário.

## Você concluiu o laboratório.
