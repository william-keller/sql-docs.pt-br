---
description: cursor (Transact-SQL)
title: cursor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- cursor data type
ms.assetid: fbea16ef-f2cc-4734-9149-ec2598fd3cca
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cc1f3981733712758230287c770c47dd0bf43562
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422900"
---
# <a name="cursor-transact-sql"></a>cursor (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Um tipo de dados para parâmetros OUTPUT de variáveis ou procedimento armazenado que contém uma referência a um cursor.
  
## <a name="remarks"></a>Comentários  
As operações que podem fazer referência a variáveis e parâmetros que têm o tipo de dados **cursor** são:
-   As instruções DECLARE *\@variável_local* e SET *\@variável_local*.  
-   As instruções de cursor OPEN, FETCH, CLOSE e DEALLOCATE.  
-   Parâmetros de saída de procedimento armazenado.  
-   A função CURSOR_STATUS.  
-   Os procedimentos armazenados do sistema **sp_cursor_list**, **sp_describe_cursor**, **sp_describe_cursor_tables** e **sp_describe_cursor_columns**.  
  
A coluna de saída **cursor_name** de **sp_cursor_list** e de **sp_describe_cursor** retorna o nome da variável de cursor.
  
Qualquer variável criada com o tipo de dados **cursor** é anulável.
  
O tipo de dados **cursor** não pode ser usado para uma coluna em uma instrução CREATE TABLE.
  
## <a name="see-also"></a>Confira também
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CURSOR_STATUS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-status-transact-sql.md)  
[Conversão de tipo de dados &#40;Mecanismo de Banco de Dados&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Tipos de dados &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
