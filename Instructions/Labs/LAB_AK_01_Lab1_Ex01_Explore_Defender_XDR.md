---
lab:
  title: Exercício 1 – Explorar o Microsoft Defender XDR
  module: Learning Path 1 - Mitigate threats using Microsoft Defender XDR
---

# Roteiro de Aprendizagem 1 – Laboratório 1 – Exercício 1 – Explorar o Microsoft Defender XDR

## Cenário do laboratório

![M365 Defender](../Media/SC-200-Lab_M1_L1_Ex1.png)

Você é um analista de operações de segurança que trabalha em uma empresa que está implantando o Microsoft Defender XDR. Comece atribuindo políticas de segurança predefinidas usadas na EOP (Proteção do Exchange Online) e no Microsoft Defender para Office 365.

>**Observação:** **Locatários do WWL – Termos de uso** Se você estiver recebendo um locatário como parte de uma entrega de treinamento com instrutor, observe que o locatário é disponibilizado com a finalidade de dar suporte aos laboratórios práticos no treinamento com instrutor.
Os locatários não devem ser compartilhados ou usados para fins fora dos laboratórios práticos. O locatário usado neste curso é um locatário de avaliação e não pode ser usado ou acessado após o fim da aula e não está qualificado para extensão.
Os locatários não podem ser convertidos em uma assinatura paga. Os locatários obtidos como parte deste curso permanecem a propriedade da Microsoft Corporation e reservamos o direito de obter acesso e a qualquer momento.

### Tempo estimado para concluir este laboratório: 30 minutos

### Tarefa 1: obter suas credenciais do Microsoft 365

Depois de iniciar o laboratório, um locatário do Microsoft 365 E5 é disponibilizado para você acessar no ambiente do Microsoft Virtual Lab. Esse locatário recebe automaticamente um nome de usuário e uma senha exclusivos. Você deve recuperar esse nome de usuário e senha para poder entrar no Microsoft 365 no ambiente do de laboratório virtual da Microsoft.

Como esse curso pode ser oferecido por parceiros de aprendizagem que usam qualquer um dos vários provedores de Hospedagem de laboratório autorizado (ALH), as etapas reais envolvidas para recuperar o ID do locatário associado ao seu locatário podem variar de acordo com o provedor de hospedagem de laboratório. Portanto, seu instrutor fornecerá as instruções necessárias sobre como recuperar essas informações para o seu curso. As informações que você deve observar para uso posterior incluem:

- **ID do sufixo do locatário.** Essa ID é para as contas onmicrosoft.com que você usará para entrar no Microsoft 365 em todos os laboratórios. Isso está no formato de **{username}@ZZZZZZ.onmicrosoft.com**, em que ZZZZZZ é o ID de sufixo de locatário exclusivo fornecido pelo provedor de hospedagem do laboratório. Grave esse valor ZZZZZZ para usar mais tarde. Quando qualquer uma das etapas do laboratório direcioná-lo para entrar em portais do Microsoft 365, você deve inserir o valor ZZZZZZ que obtido aqui.
- **Senha do locatário.** Essa é a senha da conta de administrador fornecida pelo provedor de hospedagem do laboratório.

### Tarefa 2: aplicar políticas de segurança predefinidas no Microsoft Defender para Office 365

Nesta tarefa, você atribuirá políticas de segurança predefinidas para a EOP (Proteção do Exchange Online) e o Microsoft Defender para Office 365 no portal de segurança do Microsoft 365.

1. Faça logon na máquina virtual WIN1 como Administrador com a senha: **Pa55w.rd**.  

1. Inicie o navegador Microsoft Edge.

1. No navegador Microsoft Edge, acesse o portal do Microsoft Defender XDR em (<https://security.microsoft.com>).

1. Na caixa de diálogo **Entrar**, copie e cole a conta de email do locatário referente ao nome de usuário do administrador fornecido pelo provedor de hospedagem do laboratório e selecione **Avançar**.

1. Na caixa de diálogo **Inserir senha**, copie e cole a senha de locatário do administrador fornecida pelo provedor de hospedagem do laboratório e selecione **Entrar**.

    >**Observação:** se você receber uma mensagem "A operação não pôde ser concluída. Tente novamente mais tarde. Se o problema persistir, contate o Suporte da Microsoft.", clique em **OK** para continuar.  

1. Se mostrada, feche a janela pop-up do tour rápido do Microsoft Defender XDR. **Dica:** Posteriormente nesse laboratório, você precisará aguardar até que o workspace do Defender seja provisionado. Você pode aproveitar esse tempo para navegar pelos passeios guiados para saber mais sobre o Microsoft Defender XDR.

1. No menu de navegação, expanda a seção *Email e Colaboração* e selecione **Políticas e regras**.

1. No painel *Política e regras*, selecione **Políticas de ameaça**.

1. No painel *Políticas de ameaça*, selecione **Políticas de segurança predefinidas**.

    >**Observação:** se você receber a mensagem *"Erro do cliente – Erro ao obter a regra bip"*, selecione **OK** para continuar. O erro se deve ao status de hidratação de seu locatário no Office 365, que não está habilitado por padrão.

    >**Observação:** se você receber a mensagem *"Erro do cliente – Ocorreu um erro ao recuperar as políticas de segurança predefinidas. Tente novamente mais tarde."*, selecione **OK** para continuar. Atualize seu navegador usando **Ctrl+F5**.

1. Na página *pop-out* **Saiba mais sobre políticas de segurança predefinidas**, selecione **Fechar**.

1. Em *Proteção padrão*, selecione **Gerenciar configurações de proteção**. **Dica:** se você vir essa opção esmaecida, atualize seu navegador usando **Ctrl+F5**.

1. Na seção *Aplicar Proteção do Exchange Online*, selecione **Destinatários específicos** e, em **Domínios**, comece a escrever o nome de domínio do locatário, selecione-o e clique em **Avançar**.

    >**Dica:** O nome de domínio do locatário é o mesmo nome que você tem para sua conta de administrador, pode ser algo como *WWLx######.onmicrosoft.com*. Observe que essa configuração aplica políticas para antispam, filtro de spam de saída, antimalware e antiphishing.

1. Na seção *Aplicar proteção do Defender para Office 365*, aplique a mesma configuração da etapa anterior e clique em **Avançar**. Observe que essa configuração aplica políticas para antiphishing, anexos seguros e links seguros.

1. Na seção *Proteção de representação*, clique em **Avançar** quatro vezes (4x) para continuar.

1. Na seção *Modo de política*, verifique se o botão de opção **Ativar a política depois da conclusão** está selecionado e clique em **Avançar**.

1. Leia o conteúdo em *Revisar e confirmar suas alterações* e clique em **Confirmar** para aplicar as alterações. Depois, clique em **Concluído** para concluir.

    >**Observação:** se você receber a mensagem *"O URI ''<https://outlook.office365.com/psws/service.svc/AntiPhishPolicy>" não é válido para a operação PUT. O URI deve apontar para um único recurso para operações PUT."*, Selecione **OK** e, em seguida, selecione **Cancelar** para retornar à página principal. Você verá que a opção *Proteção padrão está ativada* está habilitada.

1. Em *Proteção estrita*, selecione **Gerenciar configurações de proteção**. **Dica:** a *Proteção restrita* é encontrada em "Email e colaboração – Políticas e regras – Políticas de ameaça – Políticas de segurança predefinidas".

1. Em *Aplicar Proteção do Exchange Online*, selecione **Destinatários específicos** e, em **Grupos**, comece a escrever **Liderança**, selecione o termo e clique em **Avançar**. Observe que essa configuração aplica políticas para antispam, filtro de spam de saída, antimalware e antiphishing.

1. Na seção *Aplicar proteção do Defender para Office 365*, aplique a mesma configuração da etapa anterior e clique em **Avançar**. Observe que essa configuração aplica políticas para antiphishing, anexos seguros e links seguros.

1. Na seção *Proteção de representação*, clique em **Avançar** quatro vezes (4x) para continuar.

1. Na seção *Modo de política*, verifique se o botão de opção **Ativar a política depois da conclusão** está selecionado e clique em **Avançar**.

1. Leia o conteúdo em *Revisar e confirmar suas alterações* e clique em **Confirmar** para aplicar as alterações. Depois, clique em **Concluído** para concluir.

    >**Observação:** se você receber a mensagem *"O URI ''<https://outlook.office365.com/psws/service.svc/AntiPhishPolicy>" não é válido para a operação PUT. O URI deve apontar para um único recurso para operações PUT."*, Selecione **OK** e, em seguida, selecione **Cancelar** para retornar à página principal. Você verá que a opção *Proteção estrita está ativada* está habilitada.

### Tarefa 3: Preparar o workspace do Microsoft Defender XDR

1. No portal **Microsoft Defender**, no menu de navegação, selecione **Configurações** à esquerda.

    >**Observação:** talvez seja necessário rolar até o topo do menu.

1. Role para baixo os itens de menu para **Ativos** e selecione **Dispositivos**.

1. O processo para implantar o workspace do Defender XDR deve ser iniciado e você deverá ver mensagens informando que *carregar e inicializar* será exibida brevemente na parte superior da página e, em seguida, você verá uma imagem de uma caneca de café e uma mensagem que diz: **Espere um pouco. Estamos preparando novos espaços para seus dados e conectando-os.** O laboratório leva cerca de cinco minutos para ser concluído. *Deixe a página aberta e certifique-se de que ela seja concluída, pois ela é necessária para o próximo Laboratório.*

    >**Observação:** Desconsidere as mensagens de erro pop-up informando que *Alguns de seus dados não podem ser recuperados*. Se a mensagem "Espere! Estamos preparando novos espaços para seus dados e conectando-os" não aparece ou a página "Configurações > Microsoft Defender XDR > Conta" é aberta, mas você vê a mensagem *Falha ao carregar o local de armazenamento de dados. Tente novamente mais tarde*, selecione "Configurações de serviço de alerta" no menu "Geral".

1. Quando a inicialização do novo workspace for concluída, a página do portal **Página Inicial** exibirá um banner **Tenha o SIEM e o XDR em um só lugar**. E, em **Configurações**, as configurações gerais do Microsoft Defender XDR para Conta, Notificações por email, **Recursos de visualização**, Configurações do serviço de alerta, Permissões e funções e API de streaming agora estão ativadas.

## Você concluiu o laboratório
