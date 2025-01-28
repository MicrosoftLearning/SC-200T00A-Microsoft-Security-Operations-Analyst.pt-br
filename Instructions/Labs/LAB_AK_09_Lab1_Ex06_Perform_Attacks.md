---
lab:
  title: 'Exercício 6: conduzir ataques'
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 9 – Laboratório 1 – Exercício 6 – Conduzir ataques

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex6.png)

Você vai simular os ataques que serão usados posteriormente para detectar e investigar no Microsoft Sentinel.

>**Importante:** os exercícios de laboratório para o Roteiro de Aprendizagem 9 estão em um ambiente *independente*. Se você sair do laboratório antes de concluí-lo, será necessário executar as configurações novamente.

### Tempo estimado para concluir este laboratório: 30 minutos

### Tarefa 1: ataque de persistência com adição de chave do Registro

>**Importante:** as próximas etapas são feitas em uma máquina diferente daquela em que você estava trabalhando anteriormente. Procure o nome da máquina virtual na guia de referências.

Nesta tarefa, você realizará ataques ao host conectado ao Azure Arc e que tenha o agente do Azure Monitor configurado.

1. Faça logon na máquina virtual WINServer como Administrador com a senha: **Pa55w.rd**.  

    >**Importante:** a funcionalidade *SALVAR* do laboratório pode fazer com que o WINServer seja desconectado do Azure Arc. Uma reinicialização resolverá o problema.  

1. Selecione **Iniciar** no Windows. Em seguida, clique em **Ligar**, próximo de **Reiniciar**.

1. Siga as instruções para iniciar a sessão novamente no WINServer.

1. Em Pesquisa da barra de tarefas, insira *Comando*. O prompt de comando será exibido nos resultados da pesquisa. Clique com o botão direito do mouse no prompt de comando e selecione **Executar como administrador**. Selecione **Sim** na janela Controle de conta de usuário que aparece para permitir a execução do aplicativo.

1. No Prompt de comando, crie uma pasta Temp no diretório raiz. Lembre-se de pressionar Enter após a última linha:

    ```CommandPrompt
    cd \
    mkdir temp
    cd temp
    ```

1. Copie e execute este comando para simular a persistência do programa:

    ```CommandPrompt
    REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "SOC Test" /t REG_SZ /F /D "C:\temp\startup.bat"
    ```


### Tarefa 2: ataque de elevação de privilégio com adição de usuário

1. Copie e execute este comando para simular a criação de uma conta de administrador. Lembre-se de pressionar Enter após a última linha:

    ```CommandPrompt
    net user theusernametoadd /add
    net user theusernametoadd ThePassword1!
    net localgroup administrators theusernametoadd /add
    ```


### Tarefa 3: ataque de comando e controle com DNS

1. Copie e execute este comando para criar um script que simulará uma consulta DNS para um servidor C2:

    ```CommandPrompt
    notepad c2.ps1
    ```

1. Selecione **Sim** para criar um novo arquivo e copie o seguinte script do PowerShell em *c2.ps1*.

    >**Observação:** colar no arquivo da máquina virtual poderá não mostrar o comprimento completo do script. Verifique se o script corresponde às instruções no arquivo *c2.ps1*.

    ```PowerShell
    param(
        [string]$Domain = "microsoft.com",
        [string]$Subdomain = "subdomain",
        [string]$Sub2domain = "sub2domain",
        [string]$Sub3domain = "sub3domain",
        [string]$QueryType = "TXT",
        [int]$C2Interval = 8,
        [int]$C2Jitter = 20,
        [int]$RunTime = 240
    )
    $RunStart = Get-Date
    $RunEnd = $RunStart.addminutes($RunTime)
    $x2 = 1
    $x3 = 1 
    Do {
        $TimeNow = Get-Date
        Resolve-DnsName -type $QueryType $Subdomain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
        if ($x2 -eq 3 )
        {
            Resolve-DnsName -type $QueryType $Sub2domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
            $x2 = 1
        }
        else
        {
            $x2 = $x2 + 1
        }    
        if ($x3 -eq 7 )
        {
            Resolve-DnsName -type $QueryType $Sub3domain".$(Get-Random -Minimum 1 -Maximum 999999)."$Domain -QuickTimeout
            $x3 = 1
        }
        else
        {
            $x3 = $x3 + 1
        }
        $Jitter = ((Get-Random -Minimum -$C2Jitter -Maximum $C2Jitter) / 100 + 1) +$C2Interval
        Start-Sleep -Seconds $Jitter
    }
    Until ($TimeNow -ge $RunEnd)
    ```

1. No menu Bloco de notas, selecione **Arquivo** e depois **Salvar**. 

1. Volte para a janela do Prompt de comando, insira o seguinte comando e pressione Enter. 

    >**Observação:** você verá erros de resolução de DNS. Isso é esperado.

    ```CommandPrompt
    Start PowerShell.exe -file c2.ps1
    ```

>**Importante:** não feche essas janelas. Deixe esse script do PowerShell ser executado em segundo plano. O comando precisa gerar entradas de log por algumas horas. Você pode prosseguir para a próxima tarefa e os próximos exercícios enquanto este script é executado. Os dados criados por essa tarefa serão usados no laboratório de Busca de ameaças posteriormente. Este processo não criará quantidades substanciais de dados ou processamento.

## Prossiga para o Exercício 7
