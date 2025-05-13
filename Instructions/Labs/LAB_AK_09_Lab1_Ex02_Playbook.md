---
lab:
  title: 'Exercício 2: criar um guia estratégico'
  module: Learning Path 9 - Create detections and perform investigations using Microsoft Sentinel
---

# Roteiro de aprendizagem 9 — Laboratório 1 — Exercício 2 — Criar um guia estratégico no Microsoft Sentinel

## Cenário do laboratório

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Sentinel. Você deve aprender a detectar e mitigar ameaças usando o Microsoft Sentinel. Agora, você deseja responder e corrigir ações que podem ser executadas pelo Microsoft Sentinel como uma rotina.

Com um guia estratégico, você pode ajudar a automatizar e orquestrar sua resposta a ameaças, integrar-se a outros sistemas internos e externos e ele pode ser configurado para ser executado automaticamente em resposta a alertas ou incidentes específicos, quando disparado por uma regra de análise ou uma regra de automação.

>**Importante:** os exercícios de laboratório para o Roteiro de Aprendizagem 9 estão em um ambiente *independente*. Se você sair do laboratório antes de concluí-lo, será necessário executar as configurações novamente.

### Tarefa 1: criar um guia estratégico no Microsoft Sentinel

Nesta tarefa, você criará um Aplicativo lógico que será usado como um Guia estratégico no Microsoft Sentinel.

>**Observação:** o Microsoft Sentinel foi pré-implantado em sua assinatura do Azure com o nome **defenderWorkspace** e as soluções necessárias do *hub de conteúdo* foram instaladas.

1. Entre na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o **defenderWorkspace** do Microsoft Sentinel.

1. No *Microsoft Sentinel*, vá para **Hub de conteúdo**.

1. Na barra de pesquisa, procure por **Sentinel SOAR Essentials**.

1. Selecione a solução que aparece nos resultados.

1. Nos detalhes da solução, selecione **Gerenciar**.

1. Encontre o guia estratégico **Defender_XDR_Ransomware_Playbook_for_SecOps-Tasks** e selecione o nome.

1. Selecione o modelo **Tarefas de incidente – Guia estratégico de Ransomware do Microsoft Defender XDR para SecOps**.

1. No painel detalhes, selecione **Criar guia estratégico**.

1. Para Grupo de recursos, selecione **Criar novo**, insira **RG-Playbooks** e selecione OK.

1. Remova **for** e os *sublinhados* extras do nome do guia estratégico (isso excederia o limite de 64 caracteres). Deve ser lido **Defender_XDR_Ransomware_Playbook_SecOps_Tasks**.

1. Selecione **Conexões**.

1. Escolha **Próximo: Revisar e criar**.

1. Agora selecione **Criar Guia estratégico**.

    >**Observação:** aguarde a conclusão da implantação antes de prosseguir para a próxima tarefa.

### Tarefa 2: atualizar um Guia estratégico no Microsoft Sentinel

Nesta tarefa, você atualizará o novo guia estratégico criado com as informações de conexão adequadas.

1. Quando a tarefa anterior for concluída, você estará na página *Defender_XDR_Ransomware_Playbook_SecOps-Tasks | Designer de aplicativo lógico*. Se não estiver, conclua as etapas 1 a 5 abaixo.

1. Na barra de Pesquisa do portal do Azure, digite Sentinel e selecione Microsoft Sentinel.

1. Selecione seu workspace do Microsoft Sentinel.

1. Selecione Automação na área Configuração e, em seguida, selecione a guia *Guias estratégicos ativos*.

1. Selecione Atualizar na barra de comandos, caso não veja nenhum guia estratégico. Você deve ver o guia estratégico criado a partir da etapa anterior.

1. Clique no link do nome do guia estratégico **Defender_XDR_Ransomware_Playbook_SecOps_Tasks**.

1. Na página do designer do aplicativo lógico do **Defender_XDR_Ransomware_Playbook_SecOps_Tasks**, no menu de comandos, selecione Editar.

    >**Observação:** talvez seja necessário atualizar a página.

1. Selecione o primeiro bloco, incidentes do Microsoft Sentinel.

1. Selecione o link **Alterar conexão***.

1. Selecione **Adicionar novo** e selecione **Entrar**. Na nova janela, selecione suas credenciais de administrador da assinatura do Azure quando solicitado. A última linha do bloco agora deve ser " Conectado ao nome de usuário-administrador".

<!--- 1. Below within the logic split (+ sign), select Add an action to incident.--->

1. Selecione **Salvar** na barra de comandos.

1. Selecione o **X** na janela para fechá-la. O Aplicativo lógico será usado em um laboratório futuro.

### Tarefa 3: criar uma regra de automação

1. No Microsoft Sentinel, expanda *Configuração* no menu de navegação e selecione *Automação*.

1. Selecione  **+ Criar** e escolha **Regra de automação**.

1. Dê um nome para a regra

1. Deixe o *Gatilho* como **Quando um incidente for criado**.

1. Em *Condições*, deixe o provedor de incidentes como *Todos*.

1. Deixe o *Nome da regra de análise* como *Todos*.

1. Selecione **+ Adicionar** e escolha *Condição (E)*.

1. Na lista suspensa, selecione **Táticas**.

1. Selecione o operador **Contém** no menu suspenso.

1. Selecione os seguintes *Valores* de táticas:
    - Reconhecimento
    - Execução
    - Persistência
    - Comando e controle
    - Exfiltração
    - PreAttack

1. Em Ações, selecione **Executar guia estratégico**.

1. Selecione o link para **Gerenciar permissões do guia estratégico**.

1. Na página *Gerenciar permissões*, selecione o grupo de recursos **RG-Playbooks** criado no laboratório anterior e selecione **Aplicar**.

1. Na lista suspensa, selecione o guia estratégico **Defender_XDR_Ransomware_Playbook_SecOps_Tasks**.

1. Por fim, selecione **Aplicar** na parte inferior.

1. Selecione o **X** na janela *Criar nova regra de automação* para fechá-la.

Agora você criou um guia estratégico e uma regra de automação no Microsoft Sentinel.

## Prossiga para o Exercício 3
