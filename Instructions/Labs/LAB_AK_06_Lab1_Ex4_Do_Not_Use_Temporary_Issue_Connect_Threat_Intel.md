 **Não usar. Temporariamente não operacional.**

# Roteiro de aprendizagem 6, Laboratório 1, Exercício 4: conectar a inteligência contra ameaças ao Microsoft Sentinel usando conectores de dados

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex4.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você deve saber como conectar os dados de log de várias fontes de dados na organização. Por fim, conecte um feed de inteligência contra ameaças para aprimorar sua capacidade de detectar e priorizar ameaças conhecidas.

### Tarefa 1: conectar a inteligência contra ameaças

Nesta tarefa, você conectará um provedor de Inteligência contra ameaças com o conector de Inteligência contra ameaças – TAXII.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Edge, acesse o portal do Azure em (<https://portal.azure.com>).

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o workspace do Microsoft Sentinel que você criou anteriormente.

1. Na guia Conectores de dados, procure o conector **Inteligência contra ameaças – TAXII**.

1. Selecione a **página Abrir conector** na folha de informações do conector.

1. Na área *Configuração*, no campo **Nome amigável (para servidor)**, insira *PhishURLs*

1. Para a URL raiz da API, insira <https://limo.anomali.com/api/v1/taxii2/feeds/>

1. Insira **107** para ID da coleção.

1. Insira **guest** para nome de usuário.

1. Insira **guest** para a senha.

1. Agora selecione o botão **Adicionar**.  As URLs de phishing serão extraídas e preencherão a tabela ThreatIntelligenceIndicator.

>**Observação:** se você quiser adicionar outra coleção, abra <https://limo.anomali.com/api/v1/taxii2/feeds/collections/> no navegador Edge e use o nome de usuário e a senha de convidado para revisar os diferentes IDs disponíveis.

## Você concluiu o laboratório
