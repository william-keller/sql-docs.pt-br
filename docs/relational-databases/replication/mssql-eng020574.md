---
description: MSSQL_ENG020574
title: MSSQL_ENG020574 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG02574 error
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 49a12b3b561006196118e7e9aab3d6fecf57779b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465149"
---
# <a name="mssql_eng020574"></a>MSSQL_ENG020574
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Detalhes da mensagem  
  
|Atributo|Valor|  
|-|-|  
|Nome do Produto|SQL Server|  
|ID do evento|20574|  
|Origem do Evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbólico||  
|Texto da mensagem|Falha na validação de dados na assinatura do assinante '%s' para o artigo '%s' na publicação '%s'.|  
  
## <a name="explanation"></a>Explicação  
 Os dados no Assinante foram validados de acordo com os dados no Publicador, e os dados não corresponderam, portanto, houve falha na validação. Para obter mais informações sobre validação, consulte [Validate Replicated Data](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
## <a name="user-action"></a>Ação do usuário  
 Recomendamos que você faça o seguinte:  
  
-   Determine por que a validação falhou.  
  
-   Corrija o problema que realmente causou a falha.  
  
-   Torne os dados convergentes reiniciando a assinatura ou através de qualquer outro método.  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de erros e eventos &#40;Replicação&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
