# Módulo 1: mitigar as ameaças usando o Microsoft 365 Defender

**Observação** A conclusão bem-sucedida desta demonstração depende da conclusão de todas as etapas no [Documento de pré-requisitos](00-prerequisites.md).

## Use o portal do Microsoft Defender

Nesta tarefa, você se familiarizará com os recursos do portal Microsoft 365 Defender.

- Página inicial (Painel)
- Incidentes e alertas
- Busca
- Centro de ações
- Análise de ameaças
- Pontuação segura
- Pontos de extremidade
- Gerenciamento de vulnerabilidades
- Email e colaboração
- Aplicativos na nuvem
- Relatórios
- Configurações
- Permissões

1. Se você ainda não estiver na Central de segurança do Microsoft Defender em seu navegador, acesse a Central de segurança do Microsoft Defender em (https://security.microsoft.com) conectado como Administrador de seu locatário.

1. No painel **Página inicial**, você pode visualizar seu status seguro. Você pode personalizar a exibição em **Adicionar cartões** ou removendo cartões. Para remover um cartão, selecione as reticências (...) em um cartão.
1. Em seguida, selecione **Incidentes e alertas**. Isso expandirá as opções de menu abaixo. É aqui que as investigações são realizadas.
1. Faça o mesmo em **Busca** para expor a página Consulta de **Busca avançada de ameaças**. 
    1. Você pode executar consultas KQL aqui.
1. A seleção de **Ações e envios** exporá o **Centro de ações** e os **Envios**
1. Selecione **Inteligência contra ameaças** e, em seguida, **Análise de ameaças**. Essa página fornece insights sobre as Vulnerabilidades e exposições comuns (CVE) que você precisa rastrear. Selecione a **Classificação de segurança** e explore as guias. Dê uma olhada em **Ações recomendadas** aqui.
1. Selecione **Ativos** e **Dispositivos** para `Device Inventory`. Você pode integrar dispositivos aqui ou trabalhar com um inventário existente.
1. Além disso, em `Assets`, há **Identidades**
1. Na seção **Pontos de extremidade** está **Gerenciamento de vulnerabilidades**. `Vulnerability management` tem `Dashboard`, você pode analisar sua Pontuação de exposição.
1. Outro recurso em **Pontos de extremidade** são as **Avaliações e simulações**. O **Laboratório de avaliação** permite configurar dispositivos isolados para explorar malware.
1. Na seção **Email e colaboração** estão os recursos `Defender for Office 365`. **Investigações** é onde você vê os resultados das investigações de ameaças de Investigação e resposta automatizadas (AIR).
1. Também em **Email e colaboração** estão as **Políticas e regras**. Você configurará as políticas de **Ameaça e alerta** aqui.
1. Role para baixo até **Aplicativos na nuvem**. Esta é a seção do serviço **Microsoft Defender para Aplicativos de Nuvem**. Em **Governança de aplicativo**, é onde você define as políticas do aplicativo.
1. Na próxima seção, você verá **Relatórios** para os serviços do Microsoft 365 Defender, **AUdit**, onde habilitará a gravação da atividade de administrador do usuário e **Permissões** e **Configurações**.
1. Em **Permissões**, você pode configurar as funções do **Azure AD** e do **Ponto de extremidade**.
1. Em **Configurações**, são inseridas as configurações gerais, como fuso horário e notificações por email, além de configurações granulares para Pontos de extremidade, Identidades e Detecção de dispositivo.
1. Selecione **Configurações** e, em seguida, **Pontos de extremidade**. Você pode visualizar e adicionar as **licenças** aqui. Em seguida, selecione **Recursos avançados**. Role a lista de recursos, mas não faça alterações agora.
1. Por fim, saia do recurso **Configurações** e, na lista do menu à esquerda, selecione **Mais recursos**. Você deverá ver cartões ou blocos com links para **Conformidade do Microsoft Purview**, **Azure Active Directory** e outros recursos que não fazem parte diretamente do **Microsoft 365 Defender**. Clique no botão **Abrir** para **Conformidade do Microsoft Purview**. Isso abrirá o portal de conformidade.

## Conectar o Microsoft Sentinel ao Microsoft Defender XDR

Nesta tarefa, você conectará um workspace do Microsoft Sentinel ao Microsoft Defender XDR.

**Observação:** há diferenças de funcionalidade entre o portal do Microsoft Defender XDR e o portal do Microsoft Sentinel. A experiência e as etapas da interface do usuário podem ser diferentes das instruções do laboratório.

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

## Você concluiu o laboratório.