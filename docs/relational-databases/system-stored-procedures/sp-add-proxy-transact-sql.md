---
description: sp_add_proxy (Transact-SQL)
title: sp_add_proxy (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_proxy
- sp_add_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE PROXY statement
- sp_add_proxy
ms.assetid: cb59df37-f103-439b-bec1-2871fb669a8b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 67b7ec7a5ccb1e4a1ba022995f4912b77afc93ee
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447470"
---
# <a name="sp_add_proxy-transact-sql"></a>sp_add_proxy (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Adiciona o proxy especificado do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_add_proxy  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description' ,  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @proxy_id = ] id OUTPUT   
```  
  
## <a name="arguments"></a>Argumentos  
`[ @proxy_name = ] 'proxy_name'` O nome do proxy a ser criado. O *proxy_name* é **sysname**, com um padrão de NULL. Quando o *proxy_name* é nulo ou uma cadeia de caracteres vazia, o nome do proxy usa como padrão o *user_name* fornecido.  
  
`[ @enabled = ] is_enabled` Especifica se o proxy está habilitado. O sinalizador *is_enabled* é **tinyint**, com um padrão de 1. Quando *is_enabled* é **0**, o proxy não é habilitado e não pode ser usado por uma etapa de trabalho.  
  
`[ @description = ] 'description'` Uma descrição do proxy. A descrição é **nvarchar (512)**, com um padrão de NULL. A descrição permite documentar o proxy, mas não é usada pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agente. Portanto, este argumento é opcional.  
  
`[ @credential_name = ] 'credential_name'` O nome da credencial para o proxy. O *credential_name* é **sysname**, com um padrão de NULL. O *credential_name* ou *credential_id* deve ser especificado.  
  
`[ @credential_id = ] credential_id` O número de identificação da credencial para o proxy. O *credential_id* é **int**, com um padrão de NULL. O *credential_name* ou *credential_id* deve ser especificado.  
  
`[ @proxy_id = ] id OUTPUT` O número de identificação de proxy atribuído ao proxy se criado com êxito.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Nenhum  
  
## <a name="remarks"></a>Comentários  
 Esse procedimento armazenado deve ser executado no banco de dados **msdb** .  
  
 Um proxy do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent gerencia a segurança para etapas de trabalho que envolvem subsistemas diferentes do subsistema [!INCLUDE[tsql](../../includes/tsql-md.md)]. Cada proxy corresponde a uma credencial de segurança. Um proxy pode ter acesso a qualquer número de subsistemas.  
  
## <a name="permissions"></a>Permissões  
 Somente os membros da função de segurança fixa **sysadmin** podem executar este procedimento.  
  
 Os membros da função de segurança fixa **sysadmin** podem criar etapas de trabalho que usam qualquer proxy. Use o procedimento armazenado [sp_grant_login_to_proxy &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md) para conceder a outros logons acesso ao proxy.  
  
## <a name="examples"></a>Exemplos  
 Este exemplo cria um proxy para a credencial `CatalogApplicationCredential`. O código supõe que a credencial já exista. Para obter mais informações sobre credenciais, consulte [criar credencial &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md).  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 1,  
    @description = 'Maintenance tasks on catalog application.',  
    @credential_name = 'CatalogApplicationCredential' ;  
GO  
```  
  
## <a name="see-also"></a>Consulte Também  
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [&#41;&#40;Transact-SQL de sp_grant_login_to_proxy ](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [&#41;&#40;Transact-SQL de sp_revoke_login_from_proxy ](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
