---
description: sys. dm_pdw_dms_cores (Transact-SQL)
title: sys. dm_pdw_dms_cores (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b3f09b15-0863-4418-9347-a4f5fd2ab7c7
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: e6d785fae400ae3544b803e284d8362434899f04
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474759"
---
# <a name="sysdm_pdw_dms_cores-transact-sql"></a>sys. dm_pdw_dms_cores (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Contém informações sobre todos os serviços DMS em execução nos nós de computação do dispositivo. Ele lista uma linha por instância de serviço, que atualmente é uma linha por nó.  
  
|Nome da coluna|Tipo de Dados|DESCRIÇÃO|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|ID numérica exclusiva associada a este núcleo DMS.<br /><br /> Chave para esta exibição.|Defina como o pdw_node_id do nó em que esse núcleo do DMS está sendo executado.|  
|pdw_node_id|**int**|ID do nó no qual esse serviço DMS está em execução.|Consulte node_id em [Sys. dm_pdw_nodes &#40;&#41;do Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).|  
|status|**nvarchar(32)**|Status atual do serviço DMS.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
 Para obter informações sobre o máximo de linhas retidas por essa exibição, consulte a seção de metadados no tópico [limites de capacidade](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata) .  
  
## <a name="see-also"></a>Consulte Também  
 [Exibições de gerenciamento dinâmico de SQL Data Warehouse e paralelo data warehouse &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
