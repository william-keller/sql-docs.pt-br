---
description: MSdistpublishers (Transact-SQL)
title: MSdistpublishers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistpublishers
- MSdistpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistpublishers system table
ms.assetid: 31844099-4b33-4dc9-84b4-bac70aa82598
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ccbc9a47974a0bbd5429cc8b92cd1f5bbffae792
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488779"
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  A tabela **MSdistpublishers** contém uma linha para cada Publicador remoto com suporte do distribuidor local. Essa tabela é armazenada no banco de dados **msdb** .  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|É o nome do Distribuidor do Publicador.|  
|**distribution_db**|**sysname**|O nome do banco de dados de distribuição.|  
|**working_directory**|**nvarchar(255)**|O nome do diretório de trabalho usado para armazenar dados e arquivos de esquema para a publicação.|  
|**security_mode**|**int**|O modo de segurança implementado no Distribuidor.<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticação.<br /><br /> **1** = autenticação do Windows.|  
|**entrar**|**sysname**|A ID de logon para Autenticação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar (524)**|A senha (criptografada) para a Autenticação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**active**|**bit**|Indica se o Distribuidor local está em uso pelo Publicador remoto.|  
|**trusted**|**bit**|Indica se o Publicador remoto usa mesma senha que o Distribuidor local.<br /><br /> **0** = uma senha é necessária no Publicador remoto para se conectar ao distribuidor.<br /><br /> **1** = nenhuma senha é necessária.|  
|**third_party**|**bit**|Se o Publicador é uma instalação do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instalação.** 1** = fonte de dados heterogêneas.|  
|**publisher_type**|**sysname**|Tipo de Publicador:<br /><br /> **MSSQLSERVER**  =  MSSQLSERVER [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Programa.<br /><br /> **Oracle** = Publicador Oracle padrão.<br /><br /> **Oracle Gateway** = Publicador de gateway Oracle.|  
|**storage_connection_string**|**nvarchar (779)**|Valor da cadeia de conexão de armazenamento do banco de dados SQL do Azure.|  

  
## <a name="see-also"></a>Consulte Também  
 [Tabelas de replicação &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Exibições de replicação &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
