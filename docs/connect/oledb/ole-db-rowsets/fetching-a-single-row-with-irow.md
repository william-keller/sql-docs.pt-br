---
title: Efetuar fetch de uma linha individual com IRow (Driver do OLE DB) | Microsoft Docs
description: Buscar uma linha única usando a interface IRow do Driver do OLE DB para SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- OLE DB Driver for SQL Server, fetching
author: pmasl
ms.author: pelopes
ms.openlocfilehash: fba517134c69914914da95daacafdf634de7b15c
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244235"
---
# <a name="fetching-a-single-row-with-irow-ole-db-driver"></a>Fetch de uma linha individual com IRow (Driver do OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  A implementação da interface **IRow** no Driver do OLE DB para SQL Server é simplificada para aumentar o desempenho. **IRow** permite o acesso direto a colunas de um único objeto de linha. Se você souber com antecedência que o resultado de uma execução de comando produzirá exatamente uma linha, **IRow** recuperará as colunas da linha. Se o conjunto de resultados incluir várias linhas, **IRow** exporá apenas a primeira linha.  
  
 A implementação de **IRow** não permite nenhuma navegação da linha. Todas as colunas na linha são acessadas apenas uma vez com uma exceção: uma coluna pode ser acessada uma vez para localizar o tamanho da coluna e novamente para buscar os dados.  
  
> [!NOTE]  
>  **IRow::Open** só dá suporte à abertura do tipo de objetos DBGUID_STREAM e DBGUID_NULL.  
  
 Para obter um objeto de linha que usa o método **ICommand::Execute**, IID_IRow precisa ser passado. A interface **IMultipleResults** precisa ser usada para manipular vários conjuntos de resultados. **IMultipleResults** dá suporte a **IRow** e **IRowset**. **IRowset** é usado para operações em massa.  
  
## <a name="in-this-section"></a>Nesta seção  
  
-   [Usando IRow::GetColumns](../../oledb/ole-db-rowsets/using-irow-getcolumns.md)   
  
## <a name="see-also"></a>Consulte Também  
 [Conjuntos de linhas](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
