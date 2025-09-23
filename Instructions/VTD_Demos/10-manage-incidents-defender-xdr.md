# Módulo 10 – Gerenciar incidentes no Microsoft Defender XDR

## Gerenciar incidentes no Microsoft Defender XDR

Nesta tarefa, você explorará os recursos de gerenciamento de incidentes no Microsoft Defender XDR, incluindo a investigação de incidentes, as ações de resposta e os recursos de colaboração.

>**Importante:** este laboratório foi projetado para ser executado no ambiente de demonstração do *Zava/Alpine Ski House*. Credenciais adequadas são necessárias para o acesso.

### Principais áreas abordadas

- Painel de Incidente
- Investigação de incidentes
- Evidência e ações de resposta
- Fluxos de trabalho de gerenciamento de incidentes
- Colaboração e documentação

1. Se você ainda não está no portal do Microsoft Defender no navegador, acesse o portal do Microsoft Defender em (<https://security.microsoft.com>) e entre usando suas credenciais atribuídas.

1. No painel de navegação esquerdo, expanda a seção **Investigação e resposta** e selecione **Incidentes e alertas** > **Incidentes**. Isso exibirá a fila de incidentes, mostrando todos os incidentes ativos em seu ambiente.

1. Revise a interface da fila de incidentes:
   - Opções de filtro (Status, Atribuído a, Tags etc.)
   - Indicadores de prioridade e gravidade do incidente
   - Fontes de serviço (Defender para Ponto de Extremidade, Office 365 etc.)
   - Carimbos de data/hora da última atividade

1. Selecione um incidente na lista para abrir a página de detalhes do incidente. Observe a visão geral do incidente mostrando:
   - Linha do tempo do incidente
   - Ativos afetados (usuários, dispositivos, caixas de correio)
   - Detalhes do alerta e correlação
   - Táticas e técnicas do MITRE ATT&CK

## Processo de investigação do incidente

1. Nos detalhes do incidente, explore a guia **Alertas** para ver todos os alertas relacionados que compõem o incidente.
   - Revise a correlação e o agrupamento automático de alertas
   - Examine as evidências e os artefatos do alerta
   - Observe os níveis de confiança e as fontes de detecção

1. Selecione a guia **Dispositivos** para exibir todos os pontos de extremidade afetados:
   - Níveis de risco do dispositivo
   - Pontuações de prioridade de investigação
   - Linha do tempo de atividades do dispositivo
   - Ações de resposta disponíveis

1. Navegue até a guia **Usuários** para revisar as contas de usuário afetadas:
   - Avaliações de risco do usuário
   - Atividades e anomalias de entrada
   - Indicadores de comprometimento da conta

1. Examine a guia **Caixas de correio** (se aplicável) para incidentes relacionados a emails:
   - Detalhes de fluxo e entrega de emails
   - Análise de anexos e URLs
   - Avaliação de impacto do destinatário

## Análise de evidências e ações de resposta

1. Na guia **Evidência**, revise todas as evidências coletadas:
   - Arquivos e hashes de arquivo
   - Endereços IP e domínios
   - Chaves e processos do registro
   - Mensagens de e-mail e URLs

1. Para cada evidência, explore as ações disponíveis:
   - **Enviar para análise** – envie arquivos suspeitos para a Microsoft para análise profunda
   - **Adicionar aos indicadores** – crie indicadores de ameaça personalizados
   - **Bloquear/Permitir** – tome medidas de proteção imediatas

1. Demonstre ações de resposta selecionando um dispositivo e escolhendo entre as ações disponíveis:
   - **Isolar dispositivo** – desconecte o dispositivo da rede enquanto mantém a conectividade com o Defender
   - **Executar verificação antivírus** – inicie uma verificação completa ou rápida
   - **Coletar pacote de investigação** – colete dados forenses
   - **Restringir a execução do aplicativo** – limite a execução do aplicativo no dispositivo

## Gerenciamento e fluxo de trabalho de incidentes

1. Pratique a atribuição e o gerenciamento de incidentes:
   - **Atribuir incidente** – atribua a um analista ou equipe de segurança específico
   - **Alterar status** – atualize de Ativo para Resolvido ou outros status
   - **Adicionar tags** – aplique tags personalizadas para categorização e rastreamento
   - **Definir classificação** – marque como Verdadeiro positivo, Falso positivo ou Informativo

1. Explore o fluxo de trabalho de gerenciamento de incidentes:
   - Revise na guia **Comentários** a colaboração de analistas
   - Verifique na guia **Histórico** todas as ações realizadas
   - Usar a guia **Resumo** para relatórios executivos

1. Demonstre o processo de classificação de incidentes:
   - **Verdadeiro positivo** – atividade maliciosa confirmada que requer resposta
   - **Informativo** – atividade esperada que acionou a detecção
   - **Falso positivo** – atividade benigna sinalizada incorretamente

## Recursos avançados de incidentes

1. Explore os resultados da **Investigação automatizada** (se disponíveis):
   - Revise as descobertas da investigação orientada por IA
   - Examine as ações recomendadas
   - Aprove ou rejeite a correção automatizada

1. Navegue até a integração da **Análise de ameaças**:
   - Vincule incidentes a campanhas de ameaças conhecidas
   - Examine o contexto da inteligência contra ameaças
   - Acesse relatórios de analistas e IOCs

1. Demonstrar o impacto das **Regras de detecção personalizadas**:
   - Mostre como as regras personalizadas contribuem para a criação de incidentes
   - Examine a eficácia da regra e as oportunidades de ajuste
   - Acesse opções de modificação e teste de regras

## Relatórios e métricas de incidentes

1. Acesse recursos de relatório de incidentes:
   - Navegue até **Relatórios** > **Relatório de segurança**
   - Revise tendências e estatísticas de incidentes
   - Gere relatórios de resumo executivo

1. Explore métricas e KPIs de incidentes:
   - MTTD (tempo médio para detecção)
   - MTTR (tempo médio para resposta)
   - Tendências de volume de incidentes
   - Taxas de falsos positivos

1. Configure notificações de incidentes:
   - Configure alertas por e-mail para incidentes de alta prioridade
   - Configure a integração de equipes para resposta colaborativa
   - Crie regras de notificação personalizadas com base em critérios de incidente

## Práticas recomendadas para o gerenciamento de incidentes

1. **Estratégia de priorização**:
   - Concentre-se primeiro em incidentes de alta gravidade
   - Considere o impacto nos negócios e a criticidade dos ativos
   - Use a pontuação de risco para orientar os esforços de investigação

1. **Padrões de documentação**:
   - Mantenha notas de investigação detalhadas
   - Documente todas as ações de resposta tomadas
   - Registre as lições aprendidas e as oportunidades de melhoria

1. **Colaboração de equipe**:
   - Use esquemas consistentes de marcação e classificação
   - Estabeleça procedimentos claros de escalonamento
   - Implemente processos regulares de revisão de incidentes

1. **Melhoria contínua:**
   - Revise regularmente as taxas de falsos positivos
   - Ajuste as regras de detecção com base nos resultados do incidente
   - Atualize os manuais de resposta a incidentes com base nas descobertas

## Integração com o Microsoft Sentinel

1. Se o Microsoft Sentinel estiver conectado, demonstre o gerenciamento unificado de incidentes:
   - Correlação de incidentes entre plataformas
   - Experiência de investigação unificada
   - Indicadores e inteligência contra ameaças compartilhados

1. Mostre recursos de incidentes específicos do Sentinel:
   - Visualização do gráfico de investigação
   - Automação de manual personalizado
   - Busca avançada de ameaças entre ambientes

## Você concluiu a demonstração

---

**Recursos adicionais:**

- [Gerenciamento de incidentes do Microsoft Defender XDR](https://docs.microsoft.com/microsoft-365/security/defender/manage-incidents)
- [Guias estratégicos de resposta a incidentes](https://docs.microsoft.com/security/compass/incident-response-playbooks)
- [Estrutura MITRE ATT&CK](https://attack.mitre.org/)
