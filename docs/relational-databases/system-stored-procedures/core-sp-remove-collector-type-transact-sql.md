---
description: core.sp_remove_collector_type (Transact-SQL)
title: Core. sp_remove_collector_type (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_remove_collector_type
- sp_remove_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- core.sp_remove_collector_type stored procedure
- management data warehouse, data collector stored procedures
- sp_remove_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 88ceba25-e41a-405f-a416-bb68918a0024
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ef7ad117692b259bb9de4cb595ce7782cac7fdf8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419320"
---
# <a name="coresp_remove_collector_type-transact-sql"></a>core.sp_remove_collector_type (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Remove uma nova entrada da exibição core.supported_collector_types no banco de dados do data warehouse de gerenciamento. O procedimento deve ser executado no contexto do banco de dados do data warehouse de gerenciamento.  
  
 A exibição core.supported_collector_types mostra os tipos de coletor registrados que podem carregar dados no data warehouse de gerenciamento.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
core.sp_remove_collector_type [ @collector_type_uid = ] 'collector_type_uid'  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @collector_type_uid =] '*collector_type_uid*'  
 O GUID do tipo de coletor. *collector_type_uid* é **uniqueidentifier**, sem valor padrão.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="permissions"></a>Permissões  
 Requer associação na função de banco de dados fixa **mdw_admin** (com permissão de execução).  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir remove o tipo de coletor de Consulta T-SQL Genérico da exibição core.supported_collector_types.  
  
```  
USE <management_data_warehouse>;  
GO  
DECLARE @RC int;  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = (SELECT collector_type_uid FROM msdb.dbo.syscollector_collector_types WHERE name = N'Generic T-SQL Query Collector Type');  
EXECUTE @RC = core.sp_remove_collector_type @collector_type_uid;  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Procedimentos armazenados do sistema &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procedimentos armazenados de coletor de dados &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Data warehouse de gerenciamento](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
