---
title: Método getConnection () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f520e96-5313-468f-b987-535ddaea027e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 714ba26610aa27fbc05cb27156b293c13e58130d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923327"
---
# <a name="getconnection-method-"></a>Método getConnection ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tenta estabelecer uma conexão com a fonte de dados que o objeto [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) representa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public java.sql.Connection getConnection()  
```  
  
## <a name="return-value"></a>Valor retornado  
 Um objeto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="exceptions"></a>Exceções  
 java.sql.SQLException  
  
## <a name="remarks"></a>Comentários  
 Esse método getConnection é especificado pelo método getConnection na interface javax.sql.DataSource.  
  
## <a name="see-also"></a>Consulte Também  
 [Método getConnection &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
