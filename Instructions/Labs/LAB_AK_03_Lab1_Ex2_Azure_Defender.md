---
lab:
  title: 'Exercício 2: mitigar as ameaças usando o Microsoft Defender para Nuvem'
  module: Learning Path 3 - Mitigate threats using Microsoft Defender for Cloud
---

# Roteiro de aprendizagem 3, Laboratório 1, Exercício 2: mitigar as ameaças usando o Microsoft Defender para Nuvem

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod3_L1_Ex2.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implementou o Microsoft Defender para Nuvem. Você precisa responder às recomendações e aos alertas de segurança gerados pelo Microsoft Defender para Nuvem.

>**Observação:** uma **[simulação de laboratório interativa](https://mslabs.cloudguides.com/guides/SC-200%20Lab%20Simulation%20-%20Mitigate%20threats%20using%20Microsoft%20Defender%20for%20Cloud)** está disponível e permite que você clique neste laboratório no seu próprio ritmo. Você pode encontrar pequenas diferenças entre a simulação interativa e o laboratório hospedado, mas os principais conceitos e ideias que estão sendo demonstrados são os mesmos. 


### Tarefa 1: explorar a conformidade regulatória

Nesta tarefa, você analisará a configuração de conformidade regulatória no Microsoft Defender para Nuvem. 

>**Importante:** As próximas etapas são feitas em uma máquina diferente daquela que você estava trabalhando anteriormente. Procure as referências de nome da máquina virtual.

1. Faça logon na máquina virtual **WIN1** como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Edge, abra o portal do Azure em (https://portal.azure.com).

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de pesquisa do portal do Azure, digite *Defender* e selecione **Microsoft Defender para Nuvem**.

1. Em *Segurança da nuvem*, selecione **Conformidade regulatória** no menu do portal.

1. Selecione **Gerenciar políticas de conformidade** na barra de ferramentas.

1. Selecione sua assinatura.

1. Em *Configurações de política*, selecione **Política de segurança** no menu do portal.

1. Role para baixo e revise os "Padrões regulatórios do setor" disponíveis para você por padrão. Observe que *a ISO 27001* agora foi preterida.

1. Selecione **Adicionar mais padrões** para adicionar o padrão regulatório ISO 27001:2013 atualizado.

1. Selecione o botão **Adicionar** à direita da *ISO 27001:2013*.

1. Uma nova página para atribuir a iniciativa Azure Policy é aberta. Confirme se sua assinatura está selecionada em *Escopo* e clique em **Examinar e criar**.

1. Selecione **Criar** para atribuir a iniciativa Azure Policy à sua assinatura.

1. Selecione Microsoft Defender para Nuvem abaixo da caixa de pesquisa para retornar à tela principal.

    >**Observação:** talvez você queira voltar mais tarde à *Conformidade regulatória* para analisar os novos controles e recomendações padrão.


### Tarefa 2: explorar a postura e as recomendações de segurança

Nesta tarefa, você revisará o gerenciamento da postura de segurança da nuvem.  As informações do Secure Score podem levar 24 horas para serem recalculadas. Recomenda-se fazer esta tarefa novamente em 24 horas.

1. Em *Segurança da nuvem*, selecione **Postura de segurança** no menu do portal.

1. A classificação de segurança provavelmente mostrará *N/D* até que a classificação seja calculada.

1. Em *Geral*, selecione **Recomendações** no menu do portal.

1. Explore as recomendações fornecidas para sua assinatura e WINServer (Servidor Arc).

1. Selecione qualquer recomendação em que o status não seja *"Concluído"* para WINServer.

1. Leia a recomendação e role para baixo até **selecionar** a caixa de seleção WINServer. **Dica:** talvez seja necessário selecionar **Recursos afetados** para exibi-lo.

1. Selecione **Atribuir proprietário** e, em seguida, clique em **Selecionar proprietário**.

1. Na caixa *Endereço de email*, anote seu email de administrador. **Dica:** você pode copiá-lo nas instruções na guia *Recursos*.

1. Selecione **Voltar**, altere a *Data de conclusão* de acordo com sua preferência e clique em **Salvar**.

    >**Observação:** se você vir o erro *Falha ao criar atribuições solicitadas*, tente novamente mais tarde.

1. Feche a página de recomendação selecionando o "X" no canto superior direito da janela.


### Tarefa 3: mitigar alertas de segurança

Nesta tarefa, você carregará alertas de segurança de exemplo e revisará os detalhes do alerta.


1. Em *Geral*, selecione **Alertas de segurança** no menu do portal.

1. Selecione **Alertas de amostra** na barra de comandos. **Dica:** talvez seja necessário selecionar o botão de reticências (...) na barra de comandos.

1. No painel Criar alertas de amostra (Visualização), certifique-se de que sua assinatura esteja selecionada e que todos os alertas de amostra estejam selecionados na área de *Planos do Defender para Nuvem*.

1. Selecione **Criar alertas de exemplo**.  

    >**Observação:** este processo de criação de alertas de exemplo pode levar alguns minutos para ser concluído, aguarde até a notificação *"Alertas de exemplo criados com êxito"* aparecer. 

1. Depois de concluído, selecione **Atualizar** para ver os alertas aparecerem na área *Alertas de segurança*.

1. Para os alertas que chamaram sua atenção, execute as seguintes ações:

    - Selecione o alerta, assim as informações sobre ele deverão aparecer. Selecione **Exibir detalhes completos**.

    - Revise e leia a guia *Detalhes do alerta*.

    - Selecione a guia **Executar ação** ou selecione o botão **Avançar: Executar ação** no final da página.

    - Revise as informações de *Executar ação*. Observe as seções disponíveis para tomar medidas, dependendo do tipo de alerta: Inspecionar o contexto do recurso, Mitigar a ameaça, Prevenir ataques futuros, Disparar resposta automatizada e Suprimir alertas semelhantes.

## Você concluiu o laboratório.
