---
description: '&#x40;&#x40;CONNECTIONS (Transact-SQL)'
title: '@@CONNECTIONS (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@CONNECTIONS'
- '@@CONNECTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@CONNECTIONS function'
- connections [SQL Server], number of
- connections [SQL Server], attempted
- number of connection attempts
- attempted connections
ms.assetid: c59836a8-443c-4b9a-8b96-8863ada97ac7
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 48279ffe9c454a32545d28c7ed74556ba3f93157
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88366922"
---
# <a name="x40x40connections-transact-sql"></a>&#x40;&#x40;CONNECTIONS (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Essa função retorna o número de tentativas de conexão, bem-sucedidas ou não, desde a última inicialização do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxe  
  
```sql
@@CONNECTIONS  
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Tipos de retorno
**inteiro**
  
## <a name="remarks"></a>Comentários  
Conexões são diferentes de usuários. Por exemplo, um aplicativo pode abrir várias conexões em [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sem que o usuário perceba.
  
Execute **sp_monitor** para exibir um relatório que contém várias estatísticas do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], incluindo tentativas de contagem de conexão.
  
@@MAX_CONNECTIONS é o número máximo permitido de conexões simultâneas com o servidor. @@CONNECTIONS é incrementado a cada tentativa de logon e, portanto, @@CONNECTIONS pode exceder @@MAX_CONNECTIONS.
  
## <a name="examples"></a>Exemplos  
Este exemplo retorna a contagem de tentativas de logon a partir de data e da hora atuais.
  
```sql
SELECT GETDATE() AS 'Today''s Date and Time',   
@@CONNECTIONS AS 'Login Attempts';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
  
Today's Date and Time  Login Attempts  
---------------------- --------------  
12/5/2006 10:32:45 AM  211023         
```  
  
## <a name="see-also"></a>Confira também
[Funções estatísticas do sistema &#40;Transact-SQL&#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
[sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)
  
  
