---
description: sysarticleupdates (Transact-SQL)
title: sysarticleupdates (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticleupdates_TSQL
- sysarticleupdates
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticleupdates system table
ms.assetid: 11a53bcd-a215-4d0b-9db8-233981d3ef5d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d1aed6a7d193dfc664e9e17473c0c9aa03c282f1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463878"
---
# <a name="sysarticleupdates-transact-sql"></a>sysarticleupdates (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Contém uma linha para cada artigo com suporte para assinaturas de atualização imediata. Essa tabela é armazenada no banco de dados replicado.  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|A coluna de identidade que fornece um número de ID exclusivo para o artigo.|  
|**pubid**|**int**|A ID da publicação à qual o artigo pertence.|  
|**sync_ins_proc**|**int**|A ID do procedimento armazenado que manuseia Inserir Transações de Sincronização.|  
|**sync_upd_proc**|**int**|A ID do procedimento armazenado que manuseia Atualizar Transações de Sincronização.|  
|**sync_del_proc**|**int**|A ID do procedimento armazenado que manuseia Excluir Transações de Sincronização.|  
|**autogen**|**bit**|Indica que são gerados procedimentos armazenados automaticamente:<br /><br /> **0** = falso, não automático.<br /><br /> **1** = true, automático.|  
|**sync_upd_trig**|**int**|A ID do gatilho de versão automática na tabela de artigo.|  
|**conflict_tableid**|**int**|A ID para a tabela de conflitos.|  
|**ins_conflict_proc**|**int**|A ID do procedimento usado para gravar o conflito no **conflict_table**.|  
|**identity_support**|**bit**|Especifica se o tratamento do intervalo de identidade automático está habilitado quando a atualização na fila é usada. **0** significa que não há suporte para o intervalo de identidade.|  
  
## <a name="see-also"></a>Consulte Também  
 [Tabelas de replicação &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Exibições de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
