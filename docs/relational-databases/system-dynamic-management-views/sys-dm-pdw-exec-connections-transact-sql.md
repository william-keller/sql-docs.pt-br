---
description: sys. dm_pdw_exec_connections (Transact-SQL)
title: sys. dm_pdw_exec_connections (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 25b5edb0d1c89042b876fc0cefac278b867fb5ac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474749"
---
# <a name="sysdm_pdw_exec_connections-transact-sql"></a>sys. dm_pdw_exec_connections (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Retorna informações sobre as conexões estabelecidas com essa instância do [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e os detalhes de cada conexão.  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|session_id|**int**|Identifica a sessão associada a esta conexão. Use `SESSION_ID()` para retornar a `session_id` da conexão atual.|  
|connect_time|**datetime**|Carimbo de data/hora de quando a conexão foi estabelecida. Não permite valor nulo.|  
|encrypt_option|**nvarchar(40)**|Indica TRUE (a conexão é criptografada) ou FALSE (a conexão não é enctypred).|  
|auth_scheme|**nvarchar(40)**|Especifica o esquema do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Autenticação do Windows usado com esta conexão. Não permite valor nulo.|  
|client_id|**varchar(48)**|Endereço IP do cliente que está se conectando a este servidor. Permite valor nulo.|  
|sql_spid|**int**|A ID de processo do servidor da conexão. Use `@@SPID` para retornar a `sql_spid` da conexão atual. Para a maior finalidade, use o `session_id` em vez disso.|  
  
## <a name="permissions"></a>Permissões  
 Requer a permissão **View Server State** no servidor.  
  
## <a name="relationship-cardinalities"></a>Cardinalidades de relações  
  
| De | Para | Relação |
| ---- | -- | ------------ |
|dm_pdw_exec_sessions. session_id|dm_pdw_exec_connections. session_id|Um para um|  
|dm_pdw_exec_requests. connection_id|dm_pdw_exec_connections. connection_id|Muitos para um|  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Exemplos: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Consulta típica para reunir informações sobre a própria conexão de consultas.  
  
```  
SELECT  
    c.session_id, c.encrypt_option,  
    c.auth_scheme, s.client_id, s.login_name,   
    s.status, s.query_count  
FROM sys.dm_pdw_exec_connections AS c  
JOIN sys.dm_pdw_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = SESSION_ID();  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Exibições de gerenciamento dinâmico de SQL Data Warehouse e paralelo data warehouse &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

