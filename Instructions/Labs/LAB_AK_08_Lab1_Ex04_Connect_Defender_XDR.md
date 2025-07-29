---
lab:
  title: Exercício 4 – Conectar o Defender XDR ao Microsoft Sentinel usando conectores de dados
  module: Learning Path 8 - Connect logs to Microsoft Sentinel
---

# Roteiro de Aprendizagem 8 – Laboratório 1 – Exercício 4 – Conectar o Defender XDR ao Microsoft Sentinel usando conectores de dados

## Cenário do laboratório

![Visão geral do laboratório.](../Media/SC-200-Lab_Diagrams_Mod8_L1_Ex4.png)

Você é um analista de operações de segurança que trabalha em uma empresa que implantou o Microsoft Defender XDR e o Microsoft Sentinel. Você precisa se preparar para a Plataforma de Operações de Segurança Unificada conectando o Microsoft Sentinel ao Defender XDR. A próxima etapa será instalar a solução do Hub de Conteúdo do Defender XDR e implantar o conector de dados do Defender XDR no Microsoft Sentinel.

>**Observação:** o ambiente para este exercício é uma simulação gerada a partir do produto. Como uma simulação limitada, os links em uma página podem não estar habilitados e pode não haver suporte para entradas baseadas em texto que estejam fora do script especificado. Uma mensagem pop-up será exibida informando: "Este recurso não está disponível na simulação". Quando isso ocorrer, selecione OK e continue com as etapas do exercício.

![Mensagem de erro pop-up](../Media/simulation-pop-up-error.png)

### Tarefa 1: Microsoft Defender XDR

Nesta tarefa, você implantará o conector do Microsoft Defender XDR.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. No navegador Microsoft Edge, abra o ambiente simulado selecionando este link: [Portal do Azure]( https://app.highlights.guide/start/1c894b46-4b0a-40cb-b0f0-1e1c86c615f3?token=16d48b6c-eace-4a1f-8050-098d29d23a89).

1. Na página *Home* do portal do Azure, selecione o ícone do **Microsoft Sentinel**.

1. Na página do *Microsoft Sentinel*, selecione o workspace **Woodgrove-LogAnalyiticWorkspace**.

1. No menu esquerdo do Microsoft Sentinel, role para baixo até a seção **Gerenciamento de conteúdo** e selecione **Hub de conteúdos**.

1. No *Hub de Conteúdo*, pesquise a solução do **Microsoft Defender XDR** e selecione-a na lista.

1. Na página de detalhes da solução do *Microsoft Defender XDR*, selecione **Instalar**.

1. Quando a instalação for concluída, pesquise a solução do **Microsoft Defender XDR** e selecione-a.

1. Na página de detalhes da solução do *Microsoft Defender XDR*, selecione **Gerenciar**

1. Marque a caixa de seleção do Conector de dados *Microsoft Defender XDR* e selecione **Abrir página do conector**.

1. Você deve ver uma mensagem informando que a conexão foi bem-sucedida.

### Tarefa 2: Conectar o Microsoft Sentinel e o Microsoft Defender XDR

Nesta tarefa, você continuará com a simulação e conectará um workspace do Microsoft Sentinel ao Microsoft Defender XDR.

1. Volte para o *Hub de Conteúdo* do Microsoft Sentinel (usando o link do menu "breadcrumb" no topo da página) e selecione **Visão geral (versão prévia)** na seção Geral do menu de navegação.

1. Selecione o botão **Saiba mais** na mensagem *Tenha seu SIEM e XDR em um só lugar*.

1. Selecionar o botão **Saiba mais** abre uma nova guia no navegador do portal do *Microsoft Defender XDR*.

1. Na tela **Inicial** do portal do **Defender Defender**, você deverá ver um banner na parte superior com a mensagem: *Tenha seu SIEM e XDR em um só lugar*. Selecione o botão **Conectar um workspaces**.

1. Na página *Escolher um workspace*, selecione o workspace **woodgrove-loganalyiticsworkspace** do Microsoft Sentinel.

1. Selecione o botão **Avançar**.

1. Na página **Definir um workspace primário**, você verá o workspace **woodgrove-loganalyiticsworkspace** do Microsoft Sentinel no menu suspenso. Selecione o botão **Avançar**.

1. Na página *Examinar e concluir*, verifique se a seleção do *Workspace* está correta e examine os itens com marcadores na seção *O que esperar quando o workspace estiver conectado*. Selecione o botão **Conectar**.

1. Uma mensagem *Você está prestes a conectar um workspace* será exibida. Selecione o botão **Conectar**.

1. Agora, a página *Workspace conectado com sucesso* será exibida.

1. Selecione o botão **Fechar**.

1. Na tela **Inicial** do portal do **Defender XDR**, você deverá ver uma faixa na parte superior com a mensagem, *SIEM unificado e o XDR estiverem prontos*. Selecione o botão **Iniciar Busca**.

1. Na *Busca avançada*, você deverá ver uma mensagem para "Explorar seu conteúdo do Microsoft Sentinel". No menu de navegação de *Busca avançada de ameaças*, você pode encontrar as tabelas, funções e consultas do *Microsoft Sentinel* nas guias correspondentes.

1. Role a página para baixo na guia **Esquema** até o título **Microsoft Sentinel** e clique duas vezes na tabela **ThreatIntelligenceIndicator**.

1. No painel *Consulta*, você deverá ver uma consulta (KQL) que retorna indicadores de inteligência contra ameaças. Selecione o botão **Executar consulta**.

1. Você deverá ver os resultados retornados no painel *Resultados*.

1. Expanda o painel de menu principal esquerdo se recolhido e expanda os novos itens de menu do **Microsoft Sentinel**. Você deverá ver as seleções *Pesquisa*, *Gerenciamento de ameaças*, *Gerenciamento de conteúdo* e *Configuração*.

    >**Observação:** Lembre-se de que há diferenças de funcionalidade entre o portal do Microsoft Sentinel do Azure e o Sentinel no portal do Microsoft Defender XDR **[Diferenças de funcionalidade do Portal](https://learn.microsoft.com/azure/sentinel/microsoft-sentinel-defender-portal#capability-differences-between-portals)**.

1. No menu do Microsoft Defender XDR e **Microsoft Sentinel**, selecione **Configuração** e depois **Conectores de dados**.

1. Na página *Conectores de dados*, você deverá ver a **Atividade do Azure** e outros conectores de dados listados com o status **Conectado**.

>**Observação:** Sinta-se à vontade para explorar e comparar as outras funcionalidades do Microsoft Sentinel, mas como se trata de uma simulação, sua capacidade de explorar o Microsoft Sentinel no portal do Microsoft Defender é limitada. Em um ambiente real, você poderia explorar todas as funcionalidades do Microsoft Sentinel no portal do Microsoft Defender.

## Você concluiu o laboratório – prossiga para o Roteiro de Aprendizagem 9 – Laboratório 1 – Exercício 1 – Modificar uma regra de segurança da Microsoft
