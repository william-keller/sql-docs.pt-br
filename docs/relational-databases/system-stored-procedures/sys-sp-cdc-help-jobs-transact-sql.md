---
description: sys.sp_cdc_help_jobs (Transact-SQL)
title: sys. sp_cdc_help_jobs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_help_jobs
- sys.sp_cdc_help_jobs_TSQL
- sp_cdc_help_jobs_TSQL
- sys.sp_cdc_help_jobs
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_help_jobs
ms.assetid: 9399b4bc-8293-408f-b3cb-f904e0657fb5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 884d9f9b6e0cf60268d0d980f1141fee627e5a19
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485519"
---
# <a name="syssp_cdc_help_jobs-transact-sql"></a>sys.sp_cdc_help_jobs (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Reporta informações sobre todos os trabalhos de captura e limpeza do Change Data Capture no banco de dados atual.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sys.sp_cdc_help_jobs  
```  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|A ID do trabalho.|  
|**job_type**|**nvarchar (20)**|O tipo de trabalho.|  
|**maxtrans**|**int**|O número máximo de transações a serem processadas em cada ciclo de verificação.<br /><br /> **maxtrans** é válido somente para trabalhos de captura.|  
|**maxscans**|**int**|O número máximo de ciclos de exame a executar para extrair todas as linhas do log.  <br /><br /> **maxscans** é válido somente para trabalhos de captura.|  
|**visa**|**bit**|Um sinalizador que indica se o trabalho de captura deve ser executado continuamente (1) ou de uma só vez (0). Para obter mais informações, consulte [Sys. sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **contínuo** é válido somente para trabalhos de captura.|  
|**pollinginterval**|**bigint**|O número de segundos entre ciclos de exame de log.<br /><br /> **PollingInterval** é válido somente para trabalhos de captura.|  
|**políticas**|**bigint**|O número de minutos que as linhas de alteração serão retidas em tabelas de alteração.<br /><br /> a **retenção** é válida somente para trabalhos de limpeza.|  
|**threshold**|**bigint**|O número máximo de entradas de exclusão que podem ser excluídas usando uma única instrução na limpeza.|  
  
## <a name="permissions"></a>Permissões  
 Requer associação na função de banco de dados fixa **db_owner** .  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna informações sobre os trabalhos de captura e de limpeza definidos para o banco de dados `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_help_jobs;  
GO  
```  
  
## <a name="see-also"></a>Consulte Também  
 [o dbo. cdc_jobs &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
