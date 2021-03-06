---
description: Procedimentos armazenados de automação OLE (Transact-SQL)
title: Procedimentos armazenados de automação OLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system stored procedures [SQL Server], OLE Automation
- OLE Automation [SQL Server], stored procedures
ms.assetid: ff16a833-01fe-4877-8aa6-55b72603ec2e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 820a100a4da0ed62fd22bb64b22bf83daacee490
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454736"
---
# <a name="ole-automation-stored-procedures-transact-sql"></a>Procedimentos armazenados de automação OLE (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aceita os seguintes procedimentos armazenados de sistema que permitem o uso de objetos de automação OLE em um lote do [!INCLUDE[tsql](../../includes/tsql-md.md)]. Por padrão, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impede o acesso a procedimentos armazenados de automação OLE, pois este componente está desligado como parte da configuração de segurança do servidor. Um administrador de sistema pode ativar o acesso a procedimentos de automação OLE usando sp_configure. Para obter mais informações, consulte [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  

:::row:::
    :::column:::
        [sp_OACreate](../../relational-databases/system-stored-procedures/sp-oacreate-transact-sql.md)

        [sp_OADestroy](../../relational-databases/system-stored-procedures/sp-oadestroy-transact-sql.md)

        [sp_OAGetErrorInfo](../../relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql.md)

        [sp_OAGetProperty](../../relational-databases/system-stored-procedures/sp-oagetproperty-transact-sql.md)
    :::column-end:::
    :::column:::
        [sp_OAMethod](../../relational-databases/system-stored-procedures/sp-oamethod-transact-sql.md)

        [sp_OASetProperty](../../relational-databases/system-stored-procedures/sp-oasetproperty-transact-sql.md)

        [sp_OAStop](../../relational-databases/system-stored-procedures/sp-oastop-transact-sql.md)

        [Sintaxe da hierarquia de objetos &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/object-hierarchy-syntax-transact-sql.md)
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Consulte Também  
 [Procedimentos armazenados do sistema &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Opção de configuração de servidor Ole Automation Procedures](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
  
