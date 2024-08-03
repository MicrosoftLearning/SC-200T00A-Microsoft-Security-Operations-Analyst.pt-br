---
lab:
  title: Exercício 4 – Conectar o Defender XDR ao Microsoft Sentinel usando conectores de dados
  module: Learning Path 6 - Connect logs to Microsoft Sentinel
---

# Roteiro de Aprendizagem 6 – Laboratório 1 – Exercício 4 – Conectar o Defender XDR ao Microsoft Sentinel usando conectores de dados

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod6_L1_Ex4.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implantou o Microsoft Defender XDR e o Microsoft Sentinel. Você precisa se preparar para a Plataforma de Operações de Segurança Unificada conectando o Microsoft Sentinel ao Defender XDR. A próxima etapa será instalar a solução do Hub de Conteúdo do Defender XDR e implantar o conector de dados do Defender XDR no Microsoft Sentinel.

>**Importante:** Lembre-se de que há diferenças de funcionalidade entre o portal do Microsoft Sentinel do Azure e o Sentinel no portal do Microsoft Defender XDR **[Diferenças de funcionalidade do Portal](https://learn.microsoft.com/azure/sentinel/microsoft-sentinel-defender-portal#capability-differences-between-portals)**.

### Tarefa 1: Microsoft Defender XDR

Nesta tarefa, você implantará o conector do Microsoft Defender XDR.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Microsoft Edge, navegue até o portal do Azure em (<https://portal.azure.com>).

1. Na caixa de diálogo **Entrar**, copie e cole na conta **Email do locatário** fornecida pelo provedor de hospedagem de laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a **Senha de locatário** fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. Na barra de Pesquisa do portal do Azure, digite *Sentinel* e selecione **Microsoft Sentinel**.

1. Selecione o workspace do Microsoft Sentinel que você criou anteriormente.

1. No menu esquerdo do Microsoft Sentinel, role para baixo até a seção **Gerenciamento de conteúdo** e selecione **Hub de conteúdos**.

1. No *Hub de Conteúdo*, pesquise a solução do **Microsoft Defender XDR** e selecione-a na lista.

1. Na página de detalhes da solução do *Microsoft Defender XDR*, selecione **Instalar**.

1. Quando a instalação for concluída, pesquise a solução do **Microsoft Defender XDR** e selecione-a.

1. Na página de detalhes da solução do *Microsoft Defender XDR*, selecione **Gerenciar**

1. Marque a caixa de seleção do Conector de dados *Microsoft Defender XDR* e selecione **Abrir página do conector**.

1. Na seção de *Configuração*, na guia *Instruções*, **desmarque** a caixa de seleção *Desativar todas as regras de criação de incidentes da Microsoft para esses produtos. Recomendado* e selecione o botão **Conectar incidentes e alertas**.

1. Você deve ver uma mensagem informando que a conexão foi bem-sucedida.

### Tarefa 2: Conectar o Microsoft Sentinel e o Microsoft Defender XDR

Nesta tarefa, você conectará um workspace do Microsoft Sentinel ao Microsoft Defender XDR.

>**Observação:** O Microsoft Sentinel no portal do Microsoft Defender XDR está em versão prévia pública e a experiência e as etapas da interface do usuário podem ser diferentes das instruções do laboratório.

1. Faça logon na máquina virtual **WIN1** como *Administrador* com a senha: **Pa55w.rd**.  

1. Inicie o navegador Microsoft Edge.

1. No navegador Edge, acesse o portal do Microsoft Defender XDR em <https://security.microsoft.com>.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de email do locatário referente ao nome de usuário do administrador fornecido pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a senha de locatário do administrador fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

    >**Dica:** a conta de email e a senha de locatário do administrador podem ser encontradas na guia Recursos.

1. Na tela **Inicial** do portal do **Defender XDR**, você deverá ver um banner na parte superior com a mensagem: *Tenha seu SIEM e XDR em um só lugar*. Selecione o botão **Conectar um workspaces**.

1. Na página *Escolher um workspace*, selecione o workspace **Microsoft Sentinel** criado anteriormente.

    >**Dica:** Ele deve ter um nome como *uniquenameDefender*.

1. Selecione o botão **Avançar**.

    >**Observação:** se o botão *Próximo* estiver desabilitado ou esmaeçado e você vir uma mensagem de erro informando que o workspace do Microsoft Sentinel *não está integrado* ao Defender XDR, tente atualizar a página do portal do Defender XDR, pois pode levar de 5 a 10 minutos para ser sincronizado.

1. Na página *Examinar alterações*, verifique se a seleção do *Workspace* está correta e examine os itens com marcadores na seção *O que esperar quando o workspace estiver conectado*. Selecione o botão **Conectar**.

1. Você deverá ver uma mensagem *Conectar o workspace* seguida por um workspace *conectado com êxito* mensagem.

1. Selecione o botão **Fechar**.

1. Na tela **Inicial** do portal do **Defender XDR**, você deverá ver uma faixa na parte superior com a mensagem, *SIEM unificado e o XDR estiverem prontos*. Selecione o botão **Iniciar Busca**.

1. Na *Busca avançada*, você deverá ver uma mensagem para "Explorar seu conteúdo do Sentinel". No painel de menu à esquerda, observe as tabelas, funções e consultas do *Microsoft Sentinel* nas guias correspondentes.

1. Expanda o painel de menu principal esquerdo se recolhido e expanda os novos itens de menu do **Microsoft Sentinel**. Você deverá ver *Gerenciamento de ameaças*, *Gerenciamento de conteúdo* e seleções de *Configuração*.

 >**Observação:** a sincronização entre o Microsoft Sentinel e o Microsoft Defender XDR pode levar alguns minutos para ser concluída, portanto, talvez você não veja todos os *conectores de dados* instalados, por exemplo.

## Você concluiu o laboratório
