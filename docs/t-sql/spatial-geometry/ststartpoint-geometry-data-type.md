---
description: STStartPoint (tipo de dados geometry)
title: STStartPoint (tipo de dados geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STStartPoint_TSQL
- STStartPoint (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STStartPoint (geometry Data Type)
ms.assetid: 049917db-3f76-4053-8cd2-bc54158e89bc
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 3fd64405d2e08038701262105675557893cdf96f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88416852"
---
# <a name="ststartpoint-geometry-data-type"></a>STStartPoint (tipo de dados geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Retorna o ponto inicial de uma instância de **geometry**.
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
.STStartPoint ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Tipos de retorno
 Tipo de retorno do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **geometry**  
  
 Tipo de retorno do CLR: **SqlGeometry**  
  
 Tipo do OGC (Open Geospatial Consortium): **Point**  
  
## <a name="remarks"></a>Comentários  
 `STStartPoint()` é o equivalente de [STPointN](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md) (1).  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir cria uma instância de `LineString` e usa `STStartPoint()` para recuperar o ponto inicial da instância.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 1 0)', 0);  
SELECT @g.STStartPoint().ToString();  
```  
  
## <a name="see-also"></a>Consulte Também  
 [STPointN &#40;tipo de dados geometry&#41;](../../t-sql/spatial-geometry/stpointn-geometry-data-type.md)   
 [Métodos OGC em instâncias geometry](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

