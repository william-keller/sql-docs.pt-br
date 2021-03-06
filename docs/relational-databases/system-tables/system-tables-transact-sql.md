---
description: Tabelas do sistema (Transact-SQL)
title: Tabelas do sistema (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server]
- tables [SQL Server], system tables
- information retrieval [SQL Server]
- status information [SQL Server], system tables
- system information [SQL Server]
- system tables [SQL Server]
- system tables [SQL Server], about system tables
- system tables [SQL Server], retrieving information from
- retrieving system table information
ms.assetid: 56b8ad51-930c-4e5c-8d99-8c939d5b70ac
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bb4aba7e3ad13edd1d71266b96d6ef956a162cba
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446556"
---
# <a name="system-tables-transact-sql"></a>Tabelas do sistema (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Os tópicos desta seção descrevem as tabelas do sistema no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 As tabelas do sistema não devem ser alteradas diretamente por nenhum usuário. Por exemplo, não tente modificar tabelas do sistema com instruções DELETE, UPDATE ou INSERT ou com disparadores definidos pelo usuário.  
  
 É permitido fazer referência a colunas documentadas nas tabelas do sistema. Entretanto, muitas das colunas nas tabelas do sistema não são documentadas. Não devem ser escritos aplicativos que consultem diretamente colunas não documentadas. Em vez disso, para recuperar informações armazenadas nas tabelas do sistema, os aplicativos devem usar qualquer um dos seguintes componentes:  
  
-   Procedimentos armazenados do sistema  
  
-   Instruções e funções [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SMO (Management Objects)  
  
-   RMO (Replication Management Objects)  
  
-   Funções de catálogo da API do banco de dados  
  
 Estes componentes compõem uma API publicada obtendo informações do sistema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. O [!INCLUDE[msCoName](../../includes/msconame-md.md)] mantém a compatibilidade desses componentes de uma versão para outra. O formato das tabelas do sistema depende da arquitetura interna do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e pode ser diferente entre versões. Portanto, os aplicativos que acessem diretamente as colunas não documentadas das tabelas do sistema podem precisar ser alterados antes de acessar uma versão mais recente do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Nesta seção  
 Os tópicos da tabela do sistema são organizados pelas seguintes áreas de recurso:  

:::row:::
    :::column:::
        [Backup e restauração de tabelas &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)

        [Tabelas da captura de dados de alterações &#40;Transact-SQL&#41;](../../relational-databases/system-tables/change-data-capture-tables-transact-sql.md)

        [Tabelas do plano de manutenção de banco de dados &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/database-maintenance-plan-tables-transact-sql.md)

        [Tabelas de Eventos Estendidos do SQL Server &#40;Transact-SQL&#41;](../../relational-databases/extended-events/xevents-references-system-objects.md#system-tables)

        [Integration Services tabelas &#40;Transact-SQL&#41;](../../relational-databases/system-tables/integration-services-tables-transact-sql.md)
    :::column-end:::
    :::column:::
        [Tabelas de envio de logs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)

        [Tabelas de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)

        [SQL Server Agent tabelas &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)

        [sys.sysoledbusers &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysoledbusers-transact-sql.md)

        [&#41;systranschemas &#40;Transact-SQL ](../../relational-databases/system-views/systranschemas-transact-sql.md)
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Consulte Também  
 [Exibições de compatibilidade &#40;&#41;Transact-SQL ](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [Exibições de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
