---
description: sys.dm_os_memory_pools (Transact-SQL)
title: sys. dm_os_memory_pools (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_pools_TSQL
- dm_os_memory_pools
- dm_os_memory_pools_TSQL
- sys.dm_os_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_pools dynamic management view
ms.assetid: 1ef053f3-c6f3-456e-82b6-26e4bd630d46
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e5108e097ae54800a6a41c99d52af0ca4a92ce5c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493629"
---
# <a name="sysdm_os_memory_pools-transact-sql"></a>sys.dm_os_memory_pools (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Retorna uma linha para cada repositório de objeto na instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Você pode usar esta exibição para monitorar o uso de memória cache e identificar comportamento ruim de cache  
  
> [!NOTE]  
>  Para chamá-lo de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , use o nome **Sys. dm_pdw_nodes_os_memory_pools**.  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**memory_pool_address**|**varbinary (8)**|Endereço de memória da entrada que representa o pool de memória. Não permite valor nulo.|  
|**pool_id**|**int**|ID de um pool específico em um conjunto de pools. Não permite valor nulo.|  
|**tipo**|**nvarchar(60)**|Tipo de pool de memória. Não permite valor nulo. Para obter mais informações, consulte [Sys. dm_os_memory_clerks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md).|  
|**name**|**nvarchar(256)**|Nome atribuído pelo sistema deste objeto de memória. Não permite valor nulo.|  
|**max_free_entries_count**|**bigint**|Número máximo de entradas livres que um pool pode ter. Não permite valor nulo.|  
|**free_entries_count**|**bigint**|Número de entradas livres atualmente no pool. Não permite valor nulo.|  
|**removed_in_all_rounds_count**|**bigint**|Número de entradas removidas do pool desde que a instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] foi iniciada. Não permite valor nulo.|  
|**pdw_node_id**|**int**|**Aplica-se a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] , [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> O identificador do nó em que essa distribuição está.|  
  
## <a name="permissions"></a>Permissões

Ativado [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , requer `VIEW SERVER STATE` permissão.   
Nas [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Premium, o requer a `VIEW DATABASE STATE` permissão no banco de dados. Nas [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] camadas Standard e Basic, o requer o  **administrador do servidor** ou uma conta de **administrador do Azure Active Directory** .   

## <a name="remarks"></a>Comentários  
 Os componentes do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] às vezes usam uma estrutura de pool comum para armazenar em cache tipos de dados homogêneos e sem monitoração de estado. A estrutura de pool é mais simples que a estrutura de cache. Todas as entradas nos pools são consideradas iguais. Internamente, os pools são administradores de memória e podem ser usados em locais onde os administradores de memória são usados.  
  
## <a name="see-also"></a>Consulte Também  
 
  [SQL Server exibições de gerenciamento dinâmico relacionadas ao sistema operacional &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


