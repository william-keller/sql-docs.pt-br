---
description: Exibições de gerenciamento dinâmico relacionadas ao sistema operacional do SQL Server (Transact-SQL)
title: SQL Server exibições de gerenciamento dinâmico relacionadas ao sistema operacional (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/17/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operating systems [SQL Server], dynamic management objects
- SQL Operating System dynamic management objects [SQL Server]
- SQL OS dynamic management objects [SQL Server]
- dynamic management objects [SQL Server], SQL OS
ms.assetid: 3030c86a-0a74-4fed-ac0f-392e244cb965
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2b95dc736e02dd274723686429907fbccf4fea2a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88475039"
---
# <a name="sql-server-operating-system-related-dynamic-management-views-transact-sql"></a>Exibições de gerenciamento dinâmico relacionadas ao sistema operacional do SQL Server (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Esta seção documenta as exibições de gerenciamento dinâmico (DMV) que estão associadas ao [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sistema operacional (SQLOS). SQLOS é responsável por gerenciar recursos do sistema operacional que são específicos do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .


|  |  |
|---------|---------|
|**sys.dm_os_buffer_descriptors** | **sys.dm_os_buffer_pool_extension_configuration**|
|**sys.dm_os_child_instances** | **sys.dm_os_cluster_nodes** |
|**sys.dm_os_cluster_properties** | **sys.dm_os_dispatcher_pools** |
|**sys.dm_os_enumerate_fixed_drives** | **sys.dm_os_host_info** |
|**sys.dm_os_hosts** | **sys.dm_os_latch_stats** |
|**sys.dm_os_loaded_modules** |**sys.dm_os_memory_brokers**|
|**sys.dm_os_memory_cache_clock_hands**|**sys.dm_os_memory_cache_counters** |
|**sys.dm_os_memory_cache_entries**|**sys.dm_os_memory_cache_hash_tables**|
|**sys.dm_os_memory_clerks**|**sys.dm_os_memory_nodes**|
|**sys.dm_os_nodes**|**sys.dm_os_performance_counters**|
|**sys.dm_os_process_memory**|**sys.dm_os_schedulers**|
|**sys.dm_os_server_diagnostics_log_configurations**|**sys.dm_os_spinlock_stats** |
|**sys.dm_os_stacks**|**sys.dm_os_sys_info**|
|**sys.dm_os_sys_memory**|**sys.dm_os_tasks**|
|**sys.dm_os_threads** |**sys.dm_os_virtual_address_dump**|
|**sys.dm_os_volume_stats**|**sys.dm_os_waiting_tasks**|
|**sys.dm_os_wait_stats**|**sys.dm_os_windows_info**|
|**sys.dm_os_workers** ||








 As [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exibições de gerenciamento dinâmico relacionadas ao sistema operacional a seguir são [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] .  
  
|||  
|-|-|  
|**sys.dm_os_function_symbolic_name**|**sys.dm_os_ring_buffers**|  
|**sys.dm_os_memory_allocations**|**sys.dm_os_sublatches**|  
|**sys.dm_os_worker_local_storage**||  
  
## <a name="see-also"></a>Consulte Também  
 [Exibições e funções de gerenciamento dinâmico &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

