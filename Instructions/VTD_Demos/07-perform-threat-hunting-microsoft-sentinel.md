# Módulo 7 – Busca de ameaças no Microsoft Sentinel

**Observação** A conclusão bem-sucedida desta demonstração depende da conclusão de todas as etapas no [Documento de pré-requisitos](00-prerequisites.md).

**Importante:** esta demonstração não é necessária para o VTD-5002-FY25.

## Criar uma consulta de busca

Nesta tarefa, você criará uma consulta de busca, marcará um resultado e criará uma transmissão ao vivo.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Edge, acesse o portal do Azure em https://portal.azure.com.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione seu workspace do Microsoft Sentinel.

1. Selecione **Logs** 

1. Insira a instrução KQL a seguir no espaço Nova consulta 1:

```KQL
let lookback = 2d;
DeviceEvents | where TimeGenerated >= ago(lookback) 
| where ActionType == "DnsQueryResponse"
| extend c2 = substring(tostring(AdditionalFields.DnsQueryString),0,indexof(tostring(AdditionalFields.DnsQueryString),"."))
| where c2 startswith "sub"
| summarize count() by bin(TimeGenerated, 3m), c2
| where count_ > 5
| render timechart 
```

1. A meta desta instrução é fornecer uma visualização para verificar se há um beacon C2 em uma base consistente.  Reserve um tempo para ajustar a configuração de 3m para 30s e mais.  Altere a configuração count_ > 5 para outras contagens de limite para testemunhar o impacto.

1. Agora você identificou solicitações DNS que estão sinalizando para um servidor C2.  Em seguida, determine quais dispositivos estão sinalizando.  Insira a seguinte instrução KQL:

```KQL
let lookback = 2d;
DeviceEvents | where TimeGenerated >= ago(lookback) 
| where ActionType == "DnsQueryResponse"
| extend c2 = substring(tostring(AdditionalFields.DnsQueryString),0,indexof(tostring(AdditionalFields.DnsQueryString),".")) 
| where c2 startswith "sub"
| summarize cnt=count() by bin(TimeGenerated, 5m), c2, DeviceName
| where cnt > 15
```

**Observação** Os dados de log gerados são somente do dispositivo integrado.

1. Feche a janela *Logs* selecionando o **X** no canto superior direito da janela e selecione **OK** para descartar as alterações. 

1. Selecione a página **Busca** na área de Gerenciamento de Ameaças do portal do Microsoft Sentinel.

1. Escolha **Nova Consulta** na barra de comandos.

1. Na janela *Criar consulta personalizada*, para o tipo *Nome*, digite **Busca C2**

1. Para *Consulta personalizada*, insira a seguinte instrução KQL:

```KQL
let lookback = 2d;
DeviceEvents | where TimeGenerated >= ago(lookback) 
| where ActionType == "DnsQueryResponse"
| extend c2 = substring(tostring(AdditionalFields.DnsQueryString),0,indexof(tostring(AdditionalFields.DnsQueryString),"."))
| where c2 startswith "sub"
| summarize cnt=count() by bin(TimeGenerated, 5m), c2, DeviceName
| where cnt > 15
```

1. Role para baixo e, em *Mapeamento de entidade (versão prévia),* selecione:

    - Na lista suspensa *Tipo de entidade*, selecione **Host**.
    - Na lista suspensa *Identificador*, selecione **Nome do host**.
    - Para a lista suspensa *Valor*, selecione **DeviceName**.

1. Role para baixo e, em *Táticas e técnicas*, selecione **Comando e controle** e, em seguida, selecione **Criar** para criar a consulta de busca.

1. Na folha *"Microsoft Sentinel – Busca"*, pesquise a consulta que você acabou de criar na lista, *Busca C2*.

1. Selecione **Busca C2** na lista.

1. No painel direito, role para baixo e selecione o botão **Executar Consulta**.

1. O número de resultados é mostrado no painel central sob a coluna *Resultados*. Como alternativa, role para cima para ver a contagem na caixa *Resultados*.

1. Selecione **Exibir os resultados**.

1. Selecione a primeira linha nos resultados. 

1. Selecione **Adicionar indicador**.

1. Selecione **Criar** no painel exibido.

1. Retorne à página Busca no portal do Microsoft Sentinel.

1. Selecione a página **Indicadores**.

1. Selecione o indicador na lista de resultados.

1. Selecione **Investigar** no painel de submenu.

1. Explore o grafo de Investigação.

1. Retorne à página Busca no portal do Microsoft Sentinel.

1. Selecione a guia **Consultas**

1. Selecione a consulta **Busca C2**.

1. Selecione o **...** no final da linha para abrir o menu de contexto.

1. Selecione **Adicionar à transmissão ao vivo**.

## Você concluiu a Demonstração.