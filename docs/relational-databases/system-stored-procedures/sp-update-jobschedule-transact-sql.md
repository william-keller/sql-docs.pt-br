---
description: sp_update_jobschedule (Transact-SQL)
title: sp_update_jobschedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_jobschedule_TSQL
- sp_update_jobschedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_jobschedule
ms.assetid: 4df02594-4cd1-49a9-8d97-37c44e4d5423
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 92aa7a001a365ed9d24c0e856b304b723e57c9c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473513"
---
# <a name="sp_update_jobschedule-transact-sql"></a>sp_update_jobschedule (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Altera as configurações de agenda para o trabalho especificado.  
  
 **sp_update_jobschedule** é fornecido somente para fins de compatibilidade com versões anteriores.  
  
> [!IMPORTANT]
>  Para obter mais informações sobre a sintaxe usada em versões anteriores do Microsoft SQL Server, consulte Referencefor Microsoft SQL Server 2000 do Transact-SQL *.*  
  
## <a name="remarks"></a>Comentários  
 As agendas de trabalho podem ser gerenciadas independentemente dos trabalhos. Para atualizar uma agenda, use **sp_update_schedule**.  
  
## <a name="permissions"></a>Permissões  
 Por padrão, os membros da função de servidor fixa **sysadmin** podem executar este procedimento armazenado. Deve ser concedida a outros usuários uma das seguintes funções de banco de dados fixas do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no banco de dados **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Para obter detalhes sobre as permissões dessas funções, consulte [Funções de banco de dados fixas do SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Somente os membros do **sysadmin** podem usar esse procedimento armazenado para atualizar as agendas de trabalho que pertencem a outros usuários.  
  
## <a name="see-also"></a>Consulte Também  
 [SQL Server Agent procedimentos armazenados &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [&#41;&#40;Transact-SQL de sp_update_schedule ](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)  
  
  
