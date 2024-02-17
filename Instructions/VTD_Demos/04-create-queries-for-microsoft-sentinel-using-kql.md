# Módulo 4: criar consultas para o Microsoft Sentinel usando a Linguagem de consulta Kusto (KQL)

**Observação** A conclusão bem-sucedida desta demonstração depende da conclusão de todas as etapas no [Documento de pré-requisitos](00-prerequisites.md). 

## Acessar a área de teste da KQL

Nesta tarefa, você acessará um ambiente do Log Analytics onde poderá praticar a escrita de instruções KQL.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador, acesse https://aka.ms/lademo. Faça logon com as credenciais de Administrador MOD. 

1. Explore as tabelas disponíveis listadas na guia no lado esquerdo da tela.

1. No editor de consultas, insira a consulta a seguir e clique no botão Executar.  Você deve ver os resultados da consulta na janela inferior.

    ```KQL
    SecurityEvent
    ```

1. Ao lado do primeiro registro, selecione o **>** para expandir as informações da linha.

### Tarefa 2: executar instruções básicas do KQL

Nesta tarefa, você compilará instruções básicas do KQL.

1. O operador `search` oferece uma experiência de pesquisa de várias tabelas/colunas. As consultas a seguir demonstram o uso do operador `search`.

```KQL
search "err" 

search in (SecurityEvent,SecurityAlert,A*) "err"
```

1. O operador `where` filtra uma tabela de acordo com o subconjunto de linhas que atende a um predicado. As consultas a seguir demonstram o uso do operador `where`.

```KQL
SecurityEvent | where EventID in (4624, 4625)

SecurityEvent 
| where TimeGenerated > ago(1d) 

SecurityEvent 
| where TimeGenerated > ago(1h) and EventID == "4624" 

SecurityEvent 
| where TimeGenerated > ago(1h) 
| where EventID == 4624 
| where AccountType =~ "user" 
```

1. A instrução a seguir demonstra o uso da instrução `let` para declarar variáveis. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

```KQL
let timeOffset = 7d;
let discardEventId = 4688;
SecurityEvent
| where TimeGenerated > ago(timeOffset*2) and TimeGenerated < ago(timeOffset)
| where EventID != discardEventId
```

1. A instrução a seguir demonstra o uso da instrução `let` para declarar uma lista dinâmica. Na janela Consulta, insira a instrução a seguir e selecione **Executar**: 

```KQL
let suspiciousAccounts = datatable(account: string) [
    @"\administrator", 
    @"NT AUTHORITY\SYSTEM"
];
SecurityEvent | where Account in (suspiciousAccounts)
```

1. A instrução a seguir demonstra a pesquisa em todas as tabelas e colunas por registros dentro do intervalo de tempo de consulta exibido na janela Consulta. Na janela Consulta, antes de executar este script, altere o intervalo de tempo para "Última hora". Insira a instrução a seguir e selecione **executar**:

```KQL
search "err"
```

**Aviso:** certifique-se de alterar novamente o intervalo de tempo para "Últimas 24 horas" para os próximos scripts.

### Criar visualizações em KQL com o operador render

Nesta tarefa, você usará a geração de visualizações com instruções KQL.

1. A instrução a seguir demonstra o operador render visualizando resultados com um gráfico de barras. Na janela Consulta. Insira a instrução a seguir e selecione **executar**: 

```KQL
SecurityEvent 
| summarize count() by Account
| render barchart
```

1. A instrução a seguir demonstra a função render visualizando resultados com uma série temporal.

A função bin() arredonda os valores para um múltiplo inteiro do tamanho de compartimento fornecido.  Usado frequentemente em combinação com summarize by... Se você tiver um conjunto disperso de valores, os valores serão agrupados em um conjunto menor de valores específicos.  Combinar a série temporal gerada e o pipe para um operador render com um tipo de gráfico de tempo fornece uma visualização da série temporal. Na janela Consulta. Insira a instrução a seguir e selecione **executar**: 

```KQL
SecurityEvent 
| summarize count() by bin(TimeGenerated, 1d) 
| render timechart
```

## Você concluiu a demonstração
