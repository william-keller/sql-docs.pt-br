---
description: Validar Assinaturas
title: Validar Assinaturas | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.subscriptions.f1
helpviewer_keywords:
- Validate Subscriptions dialog box
ms.assetid: 0ca39a35-f22c-46c5-82a4-342e34bf5d1b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: cf4b901c4d830bf333e3078b836eb775ceac6d3a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470104"
---
# <a name="validate-subscriptions"></a>Validar Assinaturas
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
   Use a caixa de diálogo **Validar Assinaturas** para especificar que as assinaturas em uma publicação transacional devem ser validadas na próxima execução, para cada assinatura, do Agente de Distribuição. Os resultados de validação são exibidos no Replication Monitor. Para obter mais informações, consulte [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Opções  
 **Validar todas as assinaturas SQL Server**  
 Selecione para validar dados para todas as assinaturas SQL Server nesta publicação.  
  
 **Validar estas assinaturas**  
 Selecione se você não quiser validar todas as assinaturas. Selecione na lista as assinaturas que você quer validar.  
  
 **Opções de Validação**  
 Clique para acessar a caixa de diálogo **Opções de Validação de Assinatura** , que permite especificar se deve ser usada a validação de contagem de linhas ou validação de soma de verificação binária.  
  
## <a name="see-also"></a>Consulte Também  
 [Validar os dados replicados](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
