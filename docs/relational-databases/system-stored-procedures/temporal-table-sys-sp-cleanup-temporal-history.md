---
description: sys. sp_cleanup_temporal_history (Transact-SQL)
title: sys. sp_cleanup_temporal_history | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 30e689666336bfc76c7ec5e5f5df363363801baf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473299"
---
# <a name="syssp_cleanup_temporal_history-transact-sql"></a>sys. sp_cleanup_temporal_history (Transact-SQL)

[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

Remove todas as linhas da tabela de histórico temporal que correspondem ao período de HISTORY_RETENTION configurado em uma única transação.

## <a name="syntax"></a>Sintaxe

```
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```

## <a name="arguments"></a>Argumentos

*\@table_name*

O nome da tabela temporal para a qual a limpeza de retenção é invocada.

*schema_name*

O nome do esquema ao qual pertence a tabela temporal atual

*row_count_var* [saída]

O parâmetro de saída que retorna o número de linhas excluídas. Se a tabela de histórico tiver um índice columnstore clusterizado, esse parâmetro retornará sempre 0.

## <a name="remarks"></a>Comentários

Esse procedimento armazenado pode ser usado somente com tabelas temporais que têm o período de retenção finito especificado.
Use esse procedimento armazenado somente se precisar limpar imediatamente todas as linhas antigas da tabela de histórico. Você deve saber que ele pode ter um impacto significativo no log de banco de dados e no subsistema de e/s, pois exclui todas as linhas qualificadas dentro da mesma transação.

Sempre é recomendável contar com uma tarefa interna em segundo plano para limpeza que remove linhas antigas com o impacto mínimo sobre as cargas de trabalho regulares e o banco de dados em geral.

## <a name="permissions"></a>Permissões

Requer db_owner permissões.

## <a name="example"></a>Exemplo

```sql
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="next-steps"></a>Próximas etapas

[Política de retenção de tabelas temporais](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
