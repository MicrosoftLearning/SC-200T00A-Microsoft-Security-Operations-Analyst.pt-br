---
lab:
  title: 'Exercício 3: criar uma consulta agendada de um modelo'
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 9 — Laboratório 1 — Exercício 3 — Criar uma consulta agendada de um modelo

## Cenário do laboratório

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você deve aprender a detectar e mitigar ameaças usando o Microsoft Sentinel. Depois de conectar as fontes de dados com o Microsoft Sentinel, crie regras de análise personalizadas para ajudar a descobrir ameaças e comportamentos anômalos no ambiente.

As regras de análise procuram eventos ou conjuntos de eventos específicos no ambiente, emitem alertas quando determinados limites ou condições de evento são atingidos, geram incidentes para que o SOC faça a triagem e a investigação e respondem às ameaças com processos automatizados de acompanhamento e correção.

>**Importante:** os exercícios de laboratório para o Roteiro de Aprendizagem 9 estão em um ambiente *independente*. Se você sair do laboratório antes de concluí-lo, será necessário executar as configurações novamente.

### Tempo estimado para concluir este laboratório: 30 minutos

### Tarefa 1: criar uma consulta agendada

Nesta tarefa, você irá criar uma consulta agendada e a conectá-la ao canal do Teams que criou no exercício anterior.

>**Observação:** o Microsoft Sentinel foi pré-implantado em sua assinatura do Azure com o nome **defenderWorkspace** e as soluções necessárias do *Hub de Conteúdo* foram instaladas.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. Na caixa de diálogo **Entrar**, copie e cole a conta de **email do locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o **defenderWorkspace** do Microsoft Sentinel.

1. Na área Configurações, selecione **Análise**.

1. Verifique se você está na guia *Modelos de regra* na barra de comandos e procure a regra **Novo usuário do CloudShell**.

1. Na folha de resumo da regra, verifique se você está recebendo dados revisando o ícone verde em *Fontes de dados: Atividade do Azure*.

    >**Observação:** se você não vê-lo em um estado conectado, certifique-se de ter concluído a Tarefa 3 do Laboratório do Roteiro de aprendizagem 6, Exercício 1.

1. Selecione **Criar regra** para continuar.

1. No Assistente de regra de análise, na guia *Geral*, altere a *Severidade* para **Média**.

1. Clique no botão **Avançar: Definir lógica da regra >**:

1. Para a consulta de regra, selecione **Exibir resultados da consulta**. Você não deve receber nenhum resultado nem erro.

1. Feche a janela *Logs* selecionando o **X** o canto superior direito e selecione **OK** para descartar para salvar as alterações e voltar ao assistente.

1. Role para baixo e, em *Agendamento de consulta*, defina o seguinte:

    |Configuração|Valor|
    |---|---|
    |Executar consulta a cada|5 minutos|
    |Dados de pesquisa a partir do último|1 dia|

    >**Observação:** estamos gerando propositalmente muitos incidentes para os mesmos dados. Isso permite que o Laboratório use esses alertas.

1. Na área *Limite de alerta*, deixe o valor inalterado, pois queremos que o alerta registre todos os eventos.

1. Na área *Agrupamento de eventos*, deixe a opção **Agrupar todos os eventos em um único alerta** selecionada, pois queremos gerar um único alerta sempre que ele for executado, desde que a consulta retorne mais resultados do que o limite de alerta especificado acima.

1. Selecione o botão **Próximo: Configurações do incidente >**.

1. Na guia *Configurações de incidente*, revise as opções padrão.

1. Selecione o botão **Próximo: Resposta automatizada >**.

1. Clique no botão **Avançar: Examinar e criar >**.
  
1. Selecione **Salvar**.

### Tarefa 2: Edite sua nova regra

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione seu workspace do Microsoft Sentinel.

1. Na área Configurações, selecione **Análise**.

1. Certifique-se de estar na aba *Regras ativas* na barra de comandos e selecione a regra **Novo usuário do CloudShell**.

1. Clique com o botão direito do mouse na regra e selecione **Editar** no menu *pop-up*.

1. Clique no botão **Avançar: Definir lógica da regra >**.

1. Selecione o botão **Próximo: Configurações do incidente >**.

1. Selecione o botão **Próximo: Resposta automatizada >**.

1. Na guia *Resposta automatizada*, em *Regras de automação*, selecione **+ Adicionar novo**.

1. Para *Nome da regra de automação*, insira **Nível 2**.

1. Para *Ações*, selecione **Atribuir proprietário**.

1. Em seguida, selecione **Atribuir para mim**.

1. Selecione **Aplicar**

1. Clique no botão **Avançar: Examinar e criar >**.
  
1. Selecione **Salvar**.

### Tarefa 3: Testar sua nova regra

Nesta tarefa, você testará sua nova regra de consulta agendada.

1. Na barra superior do portal do Azure, selecione o ícone **>_** que corresponde ao Cloud Shell. Talvez seja necessário selecionar o ícone de reticências primeiro **(...)** se a resolução da tela for muito baixa.

1. Na janela de *Boas vindas ao Azure Cloud Shell*, selecione **PowerShell**.

1. Na página *Introdução*, selecione **Montar conta de armazenamento** e, em seguida, selecione o seu **Azure Pass – Sponsorship** no menu suspenso *Assinatura da conta de armazenamento* e clique no botão **Aplicar**.

    >**Importante:** Não selecione o botão de opção *Não é necessária conta de armazenamento*. Isso causará uma falha na criação do incidente.

1. Na página *Montar conta de armazenamento*, escolha **Vamos criar uma conta de armazenamento para você** e, em seguida, selecione **Avançar**.

1. Aguarde até que o Cloud Shell seja provisionado e depois feche a janela do Azure Cloud Shell.

1. Na barra de Pesquisa do portal do Azure, digite *Atividade* e selecione **Log de atividades**.

1. Certifique-se de que os seguintes itens de *Nome da operação* sejam exibidos: **Listar chaves da conta de armazenamento** e **Atualizar conta de armazenamento criada**. Essas são as operações que a consulta KQL que você analisou anteriormente corresponderá para gerar o alerta. **Dica:** talvez seja necessário selecionar **Atualizar** para atualizar a lista.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione seu workspace do Microsoft Sentinel.

1. Selecione a opção de menu **Incidentes** em *Gerenciamento de ameaças*.

1. Selecione o botão de alternância **Atualização automática de incidentes**.

1. Você deverá ver o Incidente recém-criado.

    >**Observação:** o evento que dispara o incidente pode levar mais de cinco minutos para ser processado. Prossiga para o próximo exercício, pois você voltará a essa visualização mais tarde.

1. Selecione o Incidente e revise as informações na folha direita.

## Prossiga para o Exercício 4
