---
title: SQL Server, objeto Metadados de Catálogo | Microsoft Docs
description: Saiba mais sobre o objeto de desempenho SQLServer:Catalog Metadata, que fornece contadores para metadados de catálogo do SQL Server.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Catalog Metadata
ms.assetid: 665e63e6-4bd2-4091-92a5-327364db2f8d
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 54beed996f87ad279ed097efe8e4a8ca9558634e
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458645"
---
# <a name="sql-server-catalog-metadata-object"></a>SQL Server, objeto Metadados de Catálogo
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
O objeto de desempenho **SQL Server:Metadados de Catálogo** fornece contadores para metadados de catálogo do SQL Server.

A tabela a seguir descreve os objetos de desempenho **Metadados de Catálogo** do SQL Server.


|**Contadores Metadados de Catálogo do SQL Server**|Descrição|  
|-------------|-----------------|  
|**Contagem de Entradas do Cache**|Número de entradas no cache de metadados de catálogo.|
|**Contagem de Entradas de Cache Fixadas**|Número de entradas no cache de metadados de catálogo que estão fixadas.|
|**Taxa de Acertos do Cache**|Taxa entre pesquisas e ocorrências no cache de metadados de catálogo.|
|**Base do Índice de Ocorrência no Cache**|Apenas para uso interno.|

Há uma instância do contador para cada banco de dados.

## <a name="see-also"></a>Consulte Também  
[Monitorar o uso de recursos (Monitor do Sistema)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
