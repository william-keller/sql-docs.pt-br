---
description: SQLEndTran
title: SQLEndTran | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e5ac26d47e9d75731e879d5fd05f7b72b09da047
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428268"
---
# <a name="sqlendtran"></a>SQLEndTran
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Por padrão, o driver ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fecha o cursor associado de uma instrução quando **SQLEndTran** confirma ou reverte uma operação. Os cursores de servidor são fechados, a menos que eles sejam estáticos. Quando **SQLEndTran** confirma ou reverte uma operação, o comportamento do cursor associado da instrução é determinado pelo valor do atributo SQL_COPT_SS_PRESERVE_CURSORS da conexão ODBC específica do driver, definido por [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Detalhes de implementação da API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [Função SQLEndTran](https://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
