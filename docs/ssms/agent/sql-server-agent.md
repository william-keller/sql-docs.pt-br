---
title: SQL Server Agent
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, about SQL Server Agent
- automatic administration steps
ms.assetid: 8d1dc600-aabb-416f-b3af-fbc9fccfd0ec
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9914ebe147344b24352b97d018166601077a8895
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755118"
---
# <a name="sql-server-agent"></a>SQL Server Agent

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> No momento, na [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), a maioria dos recursos do SQL Server Agent é compatível, mas não todos. Consulte [Azure SQL Database Managed Instance T-SQL differences from SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) (Diferenças entre o T-SQL da Instância Gerenciada do Banco de Dados SQL do Azure e o SQL Server) para obter detalhes.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent é um serviço do Microsoft Windows que executa tarefas admnoistrativas agendadas, que são chamadas de *trabalhos* no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  

## <a name="benefits-of-sql-server-agent"></a><a name="Benefits"></a>Benefícios do SQL Server Agent 

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent usa o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para armazenar informações de trabalhos. Os trabalhos contêm uma ou mais etapas de trabalho. Cada etapa contém sua própria tarefa; por exemplo, fazer o backup de um banco de dados.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pode executar um trabalho de uma agenda, em resposta a um evento específico ou sob demanda. Por exemplo, se desejar fazer o backup de todos os servidores da empresa todo dia após o expediente, você pode automatizar essa tarefa. Agende o backup para execução após as 22:00, de segunda a sexta; se o backup encontrar um problema, o SQL Server Agent poderá registrar o evento e notificá-lo.  
  
> [!NOTE]  
> Por padrão, o serviço [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent encontra-se desabilitado quando o [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] é instalado, a menos que o usuário opte explicitamente por iniciar automaticamente o serviço.  
  
## <a name="sql-server-agent-components"></a><a name="Components"></a>Componentes do SQL Server Agent  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent usa os componentes a seguir para definir as tarefas a serem executadas, quando executá-las e como relatar seus êxitos ou falhas.  
  
### <a name="jobs"></a>Trabalhos  
Um *trabalho* é uma série especificada de ações que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent executa. Use trabalhos para definir uma tarefa administrativa que pode ser executada uma ou mais vezes e monitorada quanto a êxito ou falha. Um trabalho pode ser executado em um servidor local ou em vários servidores remotos.  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent executados por ocasião de um evento de failover em uma instância de cluster de failover do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] não são retomados depois do failover em outro nó de cluster de failover. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Os trabalhos do Agent executados por ocasião de uma pausa em um nó de Hyper-V não serão retomados se a pausa causar um failover em outro nó. Os trabalhos que começam, mas não são concluídos por causa de um evento de failover, são registrados em log como iniciados, mas não mostram entradas de log adicionais referentes a conclusão ou falha. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent nesses cenários parecem nunca ter terminado.  
  
Os trabalhos podem ser executados de várias maneiras:  
  
-   De acordo com uma ou mais agendas.  
  
-   Em resposta a um ou mais alertas.  
  
-   Pela execução do procedimento armazenado sp_start_job.  
  
Cada ação em um trabalho é uma *etapa de trabalho*. Por exemplo, uma etapa de trabalho pode consistir na execução de uma instrução [!INCLUDE[tsql](../../includes/tsql-md.md)] , na execução de um pacote do [!INCLUDE[ssIS](../../includes/ssis_md.md)] ou na emissão de um comando para um servidor Analysis Services. As etapas de trabalho são gerenciadas como parte de um trabalho.  
  
Cada etapa de trabalho é executada em um contexto de segurança específico. Para etapas de trabalho que usam [!INCLUDE[tsql](../../includes/tsql-md.md)], use uma instrução EXECUTE AS para definir o contexto de segurança para essa etapa. Para outros tipos de etapas de trabalho, use uma conta proxy para definir o contexto de segurança para a etapa de trabalho.  
  
### <a name="schedules"></a>Agendas  
Uma *agenda* especifica quando executar um trabalho. Mais de um trabalho pode ser executado na mesma agenda e mais de uma agenda pode ser aplicada ao mesmo trabalho. Uma agenda pode definir as condições a seguir para a hora em que um trabalho é executado:  
  
-   Sempre que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent for iniciado.  
  
-   Sempre que a utilização de CPU do computador estiver em um nível definido como ocioso.  
  
-   Apenas uma vez, em data e horário específicos.  
  
-   Em uma agenda recorrente.  
  
Para obter mais informações, veja [Criar e anexar agendamentos a trabalhos](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
### <a name="alerts"></a>Alertas  
Um *alerta* é uma resposta automática a um evento específico. Por exemplo, um evento pode ser um trabalho que se inicia ou recursos do sistema que atingem um limite específico. É você quem define as condições sob as quais deve ocorrer um alerta.  
  
Um alerta pode responder a uma das seguintes condições:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eventos  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] condições de desempenho  
  
-   Eventos da Instrumentação de Gerenciamento do Windows (WMI) no computador em que o SQL Server Agent está executando  
  
Um alerta pode executar as seguintes ações:  
  
-   Notificar um ou mais operadores  
  
-   Executar um trabalho  
  
Para obter mais informações, consulte [Alertas](../../ssms/agent/alerts.md).  
  
### <a name="operators"></a>Operadores  
Um *operador* define as informações de contato de um indivíduo responsável pela manutenção de uma ou mais instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Em algumas empresas, as responsabilidades de operador são atribuídas a um indivíduo. Em empresas com vários servidores, vários indivíduos podem dividir as responsabilidades de operador. Um operador não contém informações de segurança nem define uma entidade de segurança.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pode notificar os operadores de alertas por uma ou mais destas formas:  
  
-   Email  
  
-   Pager (via email)  
  
-   **net send**  
  
> [!NOTE]  
> Para enviar notificações usando **net send**, o serviço do Windows Messenger deve ter sido iniciado no computador em que reside o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
> [!IMPORTANT]  
> As opções Pager e **net send** serão removidas do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent em uma versão futura do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evite usar esses recursos em novo trabalho de desenvolvimento e planeje modificar os aplicativos que os usam atualmente.  
  
Para enviar notificações a operadores usando email ou pagers, configure o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent para usar o Database Mail. Para obter mais informações, consulte [Database Mail](../../relational-databases/database-mail/database-mail.md).  
  
Você pode definir um operador como o alias de um grupo de indivíduos. Desse modo, todos os membros do alias serão notificados ao mesmo tempo. Para obter mais informações, consulte [Operadores](../../ssms/agent/operators.md).  
  
## <a name="security-for-sql-server-agent-administration"></a><a name="Security"></a>Segurança de administração do SQL Server Agent  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent usa as funções de banco de dados fixas **SQLAgentUserRole**, **SQLAgentReaderRole**e **SQLAgentOperatorRole** no banco de dados **msdb** para controlar o acesso ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent por usuários que não são membros da função de servidor fixa **sysadmin** . Além dessas funções de banco de dados fixas, subsistemas e proxies ajudam os administradores de bancos de dados a garantir que cada etapa de trabalho seja executada com as permissões mínimas necessárias para realizar sua tarefa.  
  
### <a name="roles"></a>Funções  
Membros das funções de banco de dados fixas **SQLAgentUserRole**, **SQLAgentReaderRole**e **SQLAgentOperatorRole** no banco de dados **msdb**e membros da função de servidor fixa **sysadmin** têm acesso ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Um usuário que não pertença a nenhuma dessas funções não pode usar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Para obter mais informações sobre as funções usadas pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, consulte [Implementar segurança do SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
### <a name="subsystems"></a>Subsistemas  
Um subsistema é um objeto predefinido que representa a funcionalidade disponível a uma etapa de trabalho. Cada proxy tem acesso a um ou mais subsistemas. Os subsistemas propiciam segurança, porque delimitam o acesso à funcionalidade disponível a um proxy. Cada etapa de trabalho é executada no contexto de um proxy, com exceção das etapas de trabalho [!INCLUDE[tsql](../../includes/tsql-md.md)] . As etapas do trabalho [!INCLUDE[tsql](../../includes/tsql-md.md)] usam o comando EXECUTE AS para definir o contexto de segurança para o proprietário do Trabalho.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] define os subsistemas que estão listados nesta tabela:  
  
|Nome do subsistema|DESCRIÇÃO|  
|--------------|-----------|  
|Script do Microsoft ActiveX|Execução de uma etapa de trabalho de script ActiveX.<br /><br />**Aviso** O subsistema de script do ActiveX será removido do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent em uma futura versão do [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam.|  
|Sistema Operacional (**CmdExec**)|Execução de um programa executável.|  
|PowerShell|Execução de uma etapa de trabalho de script PowerShell.|  
|Distribuidor da replicação|Execução de uma etapa de trabalho que ativa o Distribution Agent da replicação.|  
|Mesclagem da replicação|Execução de uma etapa de trabalho que ativa o Merge Agent da replicação.|  
|Leitor de fila da replicação|Execução de uma etapa de trabalho que ativa o Queue Reader Agent da replicação.|  
|Instantâneo da replicação|Execução de uma etapa de trabalho que ativa o Snapshot Agent da replicação.|  
|Leitor do log de transações da replicação|Execução de uma etapa de trabalho que ativa o Log Reader Agent da replicação.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] Comando|Execução de um comando do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] .|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] Consulta|Execução de uma consulta do [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] .|  
|[!INCLUDE[ssIS](../../includes/ssis_md.md)] execução de pacotes|Execução de um pacote do [!INCLUDE[ssIS](../../includes/ssis_md.md)] .|  
  
> [!NOTE]  
> Como as etapas de trabalho [!INCLUDE[tsql](../../includes/tsql-md.md)] não usam proxy, não há nenhum subsistema do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent para etapas de trabalho [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent impõe restrições de subsistema até mesmo quando a entidade de segurança do proxy teria normalmente permissão para executar a tarefa na etapa de trabalho. Por exemplo, um proxy de um usuário que é membro da função de servidor fixa sysadmin não pode executar uma etapa de trabalho [!INCLUDE[ssIS](../../includes/ssis_md.md)] , a menos que tenha acesso ao subsistema [!INCLUDE[ssIS](../../includes/ssis_md.md)] , mesmo quando o usuário pode executar pacotes [!INCLUDE[ssIS](../../includes/ssis_md.md)] .  
  
### <a name="proxies"></a>Proxies  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent usa proxies para gerenciar contextos de segurança. Um proxy pode ser usado em mais de uma etapa de trabalho. Membros da função de servidor fixa **sysadmin** podem criar proxies.  
  
Cada proxy corresponde a uma credencial de segurança. Cada proxy pode ser associado a um conjunto de subsistemas e um conjunto de logons. O proxy só pode ser usado para etapas de trabalho que utilizem um subsistema associado ao proxy. Para criar uma etapa de trabalho que utilize um proxy específico, o proprietário do trabalho deve usar um logon associado a esse proxy ou ser membro de uma função com acesso irrestrito a proxies. Membros da função de servidor fixa **sysadmin** têm acesso irrestrito a proxies. Membros de **SQLAgentUserRole**, **SQLAgentReaderRole**ou **SQLAgentOperatorRole** só podem usar proxies para os quais detém concessão de acesso específica. Cada usuário membro de alguma dessas funções de banco de dados fixas do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent deve ter acesso concedido a proxies específicos para poder criar etapas de trabalho que utilizem esses proxies.  
  
## <a name="related-tasks"></a>Related Tasks  
Use as seguintes etapas para configurar o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent para automatizar a administração do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
1.  Estabeleça quais tarefas administrativas ou eventos de servidor ocorrem regularmente e se essas tarefas ou eventos podem ser administrados via programação. Uma tarefa é uma boa candidata para automação sempre que envolve uma sequência previsível de etapas e ocorre em um horário específico ou em resposta a um evento específico.  
  
2.  Defina um conjunto de trabalhos, agendas, alertas e operadores usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], o [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts ou o SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects). Para obter mais informações, consulte [Criar trabalhos](../../ssms/agent/create-jobs.md).  
  
3.  Execute os trabalhos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent que você definiu.  
  
> [!NOTE]  
> Na instância padrão do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], o serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] é denominado SQLSERVERAGENT. Nas instâncias nomeadas, o serviço do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent é denominado SQLAgent$*nome_da_instância*.  
  
Se estiver executando várias instâncias do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], você pode usar administração multisservidor para automatizar tarefas comuns em todas as instâncias. Para obter mais informações, consulte [Administração automatizada em toda a empresa](../../ssms/agent/automated-administration-across-an-enterprise.md).  
  
Use as seguintes tarefas como introdução rápida ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent:  
  
|DESCRIÇÃO|Tópico|  
|-----------|-----|  
|Descreve como configurar o SQL Server Agent.|[Configurar o SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md)|  
|Descreve como iniciar, parar e pausar o serviço do SQL Server Agent.|[Iniciar, parar ou pausar o serviço do SQL Server Agent](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)|  
|Descreve considerações para especificar uma conta para o serviço do SQL Server Agent.|[Selecionar uma conta para o Serviço do SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md)|  
|Descreve como usar o log de erros do SQL Server Agent.|[Log de erros do SQL Server Agent](../../ssms/agent/sql-server-agent-error-log.md)|  
|Descreve como usar objetos de desempenho.|[Usar objetos de desempenho](../../ssms/agent/use-performance-objects.md)|  
|Descreve o Assistente de Plano de Manutenção, que é um utilitário a ser usado para ajudá-lo a criar trabalhos, alertas e operadores para automatizar a administração de uma instância do SQL Server.|[Usar o Assistente de Plano de Manutenção](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)|  
|Descreve como automatizar tarefas administrativas usando o SQL Server Agent.|[Tarefas de administração automatizadas &#40;SQL Server Agent&#41;](../../ssms/agent/automated-administration-tasks-sql-server-agent.md)|  
  
## <a name="see-also"></a>Consulte Também  
[Configuração da Área de Superfície](../../relational-databases/security/surface-area-configuration.md)  
  
