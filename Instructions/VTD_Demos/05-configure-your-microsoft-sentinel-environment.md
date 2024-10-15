# Módulo 5: configurar seu ambiente do Microsoft Sentinel

**Observação** A conclusão bem-sucedida desta demonstração depende da conclusão de todas as etapas no [Documento de pré-requisitos](00-prerequisites.md).

**Importante:** esta demonstração não é necessária para o VTD-5002-FY25.

## Explorar a interface do Microsoft Sentinel

1. Retorne à instância do Microsoft Sentinel que você criou anteriormente enquanto concluiu a [seção de pré-requisitos](00-prerequisites.md#deploy-azure-sentinel-workspace-for-demo-in-module-4).

1. Navegue pelo workspace recém-criado do Microsoft Sentinel para se familiarizar com as opções da interface do usuário.

## Criação uma Watchlist

Nesta tarefa, você criará uma watchlist.

1. Na caixa de pesquisa, na parte inferior da tela, insira `Notepad`.  Selecione **Bloco de notas** nos resultados.

1. Insira `Hostname` e clique no Enter para criar uma nova linha.

1. Nas linhas 2 a 6, adicione os seguintes nomes de host:
    ```
    Host1
    Host2
    Host3
    Host4
    Host5
    ```

1. No menu, selecione **Arquivo – Salvar** como e nomeie o arquivo como `HighValue.csv`.  Em seguida, altere o tipo de arquivo para **Todos os arquivos(*.*)**.  Em seguida, selecione **Salvar**.

1. Feche o Bloco de notas.

1. No Microsoft Sentinel, selecione a opção **Watchlist** na área **Minhas watchlists**.

1. Na barra de comandos, selecione **Adicionar novo**.

1. No assistente Watchlist, insira o seguinte: Nome: HighValueHosts, Descrição: Hosts de alto valor, Alias da watchlist: HighValueHosts

1. Selecione **Avançar: Fonte >**.

1. Procure o arquivo `HighValue.csv` que você acabou de criar. 

1. Depois que o arquivo CSV for carregado, selecione **Nome do host** na caixa suspensa do campo **SearchKey**.

1. Clique em **Avançar: Examinar e criar >**.

1. Selecione **Criar**.

1. A tela retornará à lista de watchlist.

1. Selecione sua nova watchlist.  Na guia direita, selecione **Exibir no Log Analytics**.

1. A instrução KQL a seguir é executada automaticamente com os resultados exibidos.

```KQL
_GetWatchlist('HighValueHosts')
```
**Observação** Pode levar um minuto para que a importação seja concluída.

Agora você pode usar o _GetWatchlist('HighValueHosts') em suas próprias instruções KQL para acessar a lista. A coluna a ser referenciada seria *Nome do host*.

## Crie um indicador de ameaças.

Nesta tarefa, você criará um indicador.

1. No Microsoft Sentinel, selecione a opção **Inteligência contra ameaças** na área **Gerenciamento de ameaças**.

1. Na barra de comandos, selecione **Adicionar novo**.

1. Analise os diferentes tipos de indicadores disponíveis na lista suspensa Tipos.  Em seguida, selecione **domain-name**. Insira suas iniciais na caixa Domínio. Um exemplo poderia ser fmg.com.

1. Para o tipo de ameaça, selecione **+ Adicionar** e copie e cole **malicious-activity** no campo.

1. Para o nome, insira o mesmo valor usado para o Domínio. Um exemplo poderia ser fmg.com.

1. Defina o campo **Válido de** como a data de hoje.

1. Selecione **Aplicar**.

**Observação** pode levar um minuto para que o indicador apareça.

1. Selecione a opção **Logs** na área Geral.  Talvez seja necessário desabilitar a opção "Sempre mostrar consultas" para acessar a janela Consulta.

1. Execute a seguinte instrução KQL.

```KQL
ThreatIntelligenceIndicator 
```
Role os resultados para a direita para ver a coluna DomainName. Você também pode executar a seguinte instrução KQL para ver apenas a coluna DomainName.  

```KQL
ThreatIntelligenceIndicator 
| project DomainName
```
## Você concluiu a demonstração.