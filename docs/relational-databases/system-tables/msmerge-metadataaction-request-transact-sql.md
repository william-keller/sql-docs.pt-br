---
description: MSmerge_metadataaction_request (Transact-SQL)
title: MSmerge_metadataaction_request (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_metadataaction_request
- MSmerge_metadataaction_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_metadataaction_request system table
ms.assetid: cd31a114-900a-4218-ab58-d959e547c647
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1266bd0c4a8af020a3e29900c2d82d881010a4e8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423290"
---
# <a name="msmerge_metadataaction_request-transact-sql"></a>MSmerge_metadataaction_request (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  A tabela **MSmerge_metadataaction_request** armazena uma linha para cada ação de compensação necessária. Usando a sincronização da Web, se ocorrer um erro e a sincronização precisar ser repetida, uma entrada será feita em **MSmerge_metadataaction_request**. Durante a fase de carregamento da mesclagem subsequente, solicitações de todos os artigos que pertencem à publicação que está sendo sincronizada são recuperadas dessa tabela e carregadas. Quando a sincronização for concluída com êxito, a linha correspondente na tabela de **MSmerge_metadataaction_request** será excluída. Essa tabela é armazenada no Publicador, no banco de dados de publicação, e no Assinante, no banco de dados de assinatura.  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|O apelido da tabela publicada.|  
|**ROWGUID**|**uniqueidentifier**|O identificador para a linha determinada.|  
|**action**|**tinyint**|Identifica a ação compensatória requerida.|  
|**geração**|**bigint**|O valor da geração para a qual a ação compensatória é necessária.|  
|**Changed**|**int**|Interno-somente uso.|  
  
## <a name="see-also"></a>Consulte Também  
 [Tabelas de replicação &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Exibições de replicação &#40;&#41;Transact-SQL ](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Sincronização da Web para replicação de mesclagem](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
