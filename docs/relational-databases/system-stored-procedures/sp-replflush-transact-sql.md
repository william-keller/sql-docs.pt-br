---
description: sp_replflush (Transact-SQL)
title: sp_replflush (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replflush
- sp_replflush_TSQL
helpviewer_keywords:
- sp_replflush
ms.assetid: 20809f5f-941d-427f-8f0c-de7a6c487584
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 144bffdd6076b73c8b10fca3c7d9f878d77091d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485725"
---
# <a name="sp_replflush-transact-sql"></a>sp_replflush (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Libera o cache de artigo. Esse procedimento armazenado é executado no Publicador, no banco de dados publicador.  
  
> [!IMPORTANT]  
>  Você não deve precisar executar esse procedimento manualmente. **sp_replflush** só deve ser usado para solucionar problemas de replicação, conforme indicado por um profissional de suporte de replicação experiente.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_replflush  
```  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Comentários  
 **sp_replflush** é usado na replicação transacional.  
  
 As definições de artigo são armazenadas no cache para maior eficiência. **sp_replflush** é usado por outros procedimentos armazenados de replicação sempre que uma definição de artigo é modificada ou removida.  
  
 Somente uma conexão de cliente pode ter acesso de Log Reader a um determinado banco de dados. Se um cliente tiver acesso ao leitor de log a um banco de dados, a execução de **sp_replflush** fará com que o cliente libere seu acesso. Outros clientes podem, então, verificar o log de transações usando **sp_replcmds** ou **sp_replshowcmds**.  
  
## <a name="permissions"></a>Permissões  
 Somente os membros da função de servidor fixa **sysadmin** ou a função de banco de dados fixa **db_owner** podem ser executados **sp_replflush**.  
  
## <a name="see-also"></a>Consulte Também  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [&#41;&#40;Transact-SQL de sp_repldone ](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [&#41;&#40;Transact-SQL de sp_repltrans ](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
