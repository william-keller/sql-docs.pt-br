---
description: sp_addqueued_artinfo (Transact-SQL)
title: sp_addqueued_artinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addqueued_artinfo
- sp_addqueued_artinfo_TSQL
helpviewer_keywords:
- sp_addqueued_artinfo
ms.assetid: decdb6eb-3dcd-4053-a21d-fd367c3fbafb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 22c1c38828ab6f1857d64136a402752b110a214e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469789"
---
# <a name="sp_addqueued_artinfo-transact-sql"></a>sp_addqueued_artinfo (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  
  
> [!IMPORTANT]  
>  O procedimento de [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) deve ser usado em vez de **sp_addqueued_artinfo**. [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) gera um script que contém as chamadas **sp_addqueued_artinfo** e **sp_addsynctrigger** .  
  
 Cria a tabela de [MSsubscription_articles](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md) no Assinante que é usada para rastrear informações de assinatura do artigo (atualização em fila e atualização imediata com atualização em fila como failover). Esse procedimento armazenado é executado no Assinante no banco de dados de assinatura.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_addqueued_artinfo [ @artid= ] 'artid'  
        , [ @article= ] 'article'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @dest_table= ] 'dest_table'  
        , [ @owner = ] 'owner'  
        , [ @cft_table= ] 'cft_table'  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @artid = ] 'artid'` É o nome da ID do artigo. *artid* é **int**, sem padrão  
  
`[ @article = ] 'article'` É o nome do artigo a ser inserido no script. o *artigo* é **sysname**, sem padrão  
  
`[ @publisher = ] 'publisher'` É o nome do servidor do Publicador. o *Publicador* é **sysname**, sem padrão.  
  
`[ @publisher_db = ] 'publisher_db'` É o nome do banco de dados do Publicador. *publisher_db* é **sysname**, sem padrão.  
  
`[ @publication = ] 'publication'` É o nome da publicação a ser inserida no script. a *publicação* é **sysname**, sem padrão.  
  
`[ @dest_table = ] _'dest_table'` É o nome da tabela de destino. *dest_table* é **sysname**, sem padrão.  
  
 [** @owner =** ] **'**_proprietário_**'**  
 É o proprietário da assinatura. *Owner* é **sysname**, sem padrão.  
  
`[ @cft_table = ] 'cft_table'` Nome da tabela de conflitos de atualização enfileirada deste artigo. *cft_table*é **sysname**, sem padrão.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="remarks"></a>Comentários  
 **sp_addqueued_artinfo** é usado pelo agente de distribuição como parte da inicialização da assinatura. Esse procedimento armazenado não é executado com frequência pelos usuários, mas pode ser útil se o usuário precisar configurar manualmente uma assinatura.  
  
 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) em vez de **sp_addqueued_artinfo**.  
  
## <a name="permissions"></a>Permissões  
 Somente os membros da função de servidor fixa **sysadmin** ou **db_owner** função de banco de dados fixa podem ser executados **sp_addqueued_artinfo**.  
  
## <a name="see-also"></a>Consulte Também  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [&#41;&#40;Transact-SQL de sp_script_synctran_commands ](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [&#41;&#40;Transact-SQL de MSsubscription_articles ](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
