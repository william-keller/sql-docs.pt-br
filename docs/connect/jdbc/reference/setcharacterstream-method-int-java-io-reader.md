---
title: Método setCharacterStream (int, java.io.Reader) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8d4e1f7-14fc-4590-af98-1eda30d2ca6d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4987a452d0f4d4985dbcaacf53b265aa7d8f1c5
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80929106"
---
# <a name="setcharacterstream-method-int-javaioreader"></a>Método setCharacterStream (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define o parâmetro designado como o objeto java.io.Reader especificado.  
  
> [!NOTE]
>  Esse recurso foi introduzido no [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver versão 2.0.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public final void setCharacterStream(int parameterIndex,  
                              java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>parâmetros  
 *parameterIndex*  
  
 Um **int** que indica o número do parâmetro.  
  
 *reader*  
  
 O objeto java.io.Reader que contém os dados Unicode.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentários  
 Esse método setCharacterStream é especificado pelo método setCharacterStream na interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Consulte Também  
 [Método setCharacterStream &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverpreparedstatement.md)   
 [Membros de SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
