---
lab:
  title: Exercício 1 – Explorar logs de Auditoria do Microsoft Purview
  module: Learning Path 3 - Mitigate threats using Microsoft Purview
---

# Roteiro de aprendizagem 3 — Laboratório 1 — Exercício 1 — Explorar logs de Auditoria do Microsoft Purview

## Cenário do laboratório

Você é um analista de operações de segurança que trabalha em uma empresa que está implementando o Microsoft Defender XDR e o Microsoft Purview. Você está auxiliando colegas da equipe de conformidade de TI a configurar a Auditoria do Purview (Standard) e o Audit (Premium). O objetivo deles é garantir que todos os acessos e modificações aos dados dos pacientes em nossa rede de unidades de saúde sejam registrados com precisão para atender às regulamentações de proteção de dados de saúde.

>[!aviso] Se você receber uma mensagem de erro e não conseguir iniciar a gravação de auditoria neste exercício, use estas etapas como solução alternativa:
>
>1. Abra uma sessão do PowerShell com privilégios elevados digitando *PowerShell* no formulário Windows Search e selecione **Executar como Administrador**.
>1. Instale o módulo ExchangeOnlineManagement ao executar `Install-Module -Name ExchangeOnlineManagement`
>1. Conecte-se ao ExchangeOnlineManagement ao executar `Connect-ExchangeOnline`
>1. Quando solicitado, faça login inserindo o nome de usuário e a senha do administrador do seu provedor de hospedagem de laboratório.
>1. Para verificar se a auditoria está habilitada, execute `Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled`
>1. Se for falso, o log de auditoria estará desativado.
>1. Para habilitar a auditoria, execute `Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true`
>1. Se você receber um erro informando que não consegue executar o script em sua organização, execute `Enable-OrganizationCustomization`
>1. Tente executar `Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true` novamente
>1. Para confirmar se a auditoria está habilitada, execute `Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled`
>1. Depois de concluído, execute `Disconnect-ExchangeOnline` para encerrar sua sessão

### Tempo estimado para concluir este laboratório: 15 minutos

### Tarefa 1: Habilitar logs de Auditoria do Purview

Nesta tarefa, você atribuirá políticas de segurança predefinidas para a EOP (Proteção do Exchange Online) e o Microsoft Defender para Office 365 no portal de segurança do Microsoft 365.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. Inicie o navegador Microsoft Edge.

1. No navegador Microsoft Edge, acesse o portal do Microsoft Defender XDR em <https://security.microsoft.com>.

1. Na caixa de diálogo **Entrar**, copie e cole a conta de email do locatário referente ao nome de usuário do administrador fornecido pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a senha de locatário do administrador fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

1. No menu de navegação, expanda *Tecnologia operacional* e selecione **Mais recursos**.

1. No painel **Mais recursos**, selecione o botão **Abrir** no bloco *portal do Microsoft Purview*.

1. Quando o portal do Microsoft Purview abrir, uma mensagem será exibida informando que *O portal de conformidade está desativado*. Essa mensagem atingirá o tempo limite e redirecionará você para o novo *portal do Microsoft Purview*.

1. Na mensagem *Bem-vindo ao novo portal do Microsoft Purview*, escolha a opção para concordar com os termos de divulgação de fluxo de dados e a política de privacidade e clique em **Experimentar agora**.

    ![Captura de tela mostrando a tela de Boas-vindas ao novo porta do Microsoft Purview.](../Media/welcome-purview-portal.png)

1. Selecione **Soluções** na barra lateral esquerda e escolha **Auditoria**.

1. Na página **Pesquisar**, selecione a barra azul **Iniciar gravação de atividades do usuário e do administrador** para habilitar o log de auditoria.

    ![Captura de tela mostrando o botão Iniciar gravação de atividades do usuário e do administrador.](../Media/enable-audit-button.png)

1. Depois de selecionar esta opção, a barra azul desaparecerá desta página.

    >**Observação:** pode levar 60 minutos para que as atividades comecem a ser gravadas.

## Você concluiu o laboratório
