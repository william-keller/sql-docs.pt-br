---
description: sys. security_policies (Transact-SQL)
title: sys. security_policies (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.SECURITY_POLICIES_TSQL
- SECURITY_POLICIES_TSQL
- SYS.SECURITY_POLICIES
- SECURITY_POLICIES
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_policies catalog view
- security_policies catalog view
ms.assetid: 35362f5b-e601-4049-9e1d-c5307e823831
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ae97e6f310561339c24e712dd3d0f07552232bf2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490138"
---
# <a name="syssecurity_policies-transact-sql"></a>sys. security_policies (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Retorna uma linha para cada política de segurança no banco de dados.  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Nome da política de segurança, exclusivo no banco de dados.|  
|object_id|**int**|ID da política de segurança.|  
|principal_id|**int**|ID do proprietário da política de segurança, conforme registrado no banco de dados. NULL se o proprietário for determinado por meio do esquema.|  
|schema_id|**int**|ID do esquema onde o objeto reside.|  
|parent_object_id|**int**|ID do objeto ao qual esta política pertence. Deve ser 0.|  
|type|**vachar (2)**|Deve ser **SP**.|  
|type_desc|**nvarchar(60)**|**SECURITY_POLICY**.|  
|create_date|**datetime**|A data UTC em que a política de segurança foi criada.|  
|modify_date|**datetime**|A data UTC em que a política de segurança foi modificada.|  
|is_ms_shipped|**bit**|Sempre falso.|  
|is_enabled|**bit**|Estado de especificação da política de segurança:<br /><br /> 0 = desabilitado<br /><br /> 1 = habilitado|  
|is_not_for_replication|**bit**|A política foi criada com a opção NOT FOR REPLICATION.|  
|uses_database_collation|**bit**|Usa a mesma ordenação do banco de dados.|  
|is_schemabinding_enabled|**bit**|Estado de esquema para a política de segurança:<br /><br /> 0 ou NULL = habilitado<br /><br /> 1 = desabilitada|  
  
## <a name="permissions"></a>Permissões  
 Entidades com a permissão **alterar qualquer política de segurança** têm acesso a todos os objetos nessa exibição de catálogo, bem como a qualquer pessoa com **definição de exibição** no objeto.  
  
## <a name="see-also"></a>Consulte Também  
 [Segurança em nível de linha](../../relational-databases/security/row-level-security.md)   
 [sys. security_predicates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Exibições de catálogo de segurança &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Exibições de catálogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Entidades &#40;Mecanismo de Banco de Dados&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
