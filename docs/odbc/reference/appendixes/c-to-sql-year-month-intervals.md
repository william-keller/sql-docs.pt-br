---
description: 'C para SQL: intervalos de ano-mês'
title: 'C to SQL: intervalos de ano/mês | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], year-month intervals
- intervals [ODBC], converting
- year-month intervals [ODBC]
- data conversions from C to SQL types [ODBC], year-month intervals
ms.assetid: a0eb7b55-9db0-4375-9210-bddec4593880
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ffd9a3f7f14ff6af93f15521738bebdbc63a8f58
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449018"
---
# <a name="c-to-sql-year-month-intervals"></a>C para SQL: intervalos de ano-mês
Os identificadores para os tipos de dados ODBC C de intervalo de ano/mês são:  
  
 SQL_C_INTERVAL_MONTH SQL_C_INTERVAL_YEAR SQL_C_INTERVAL_YEAR_TO_MONTH  
  
 A tabela a seguir mostra os tipos de dados ODBC SQL para os quais os dados do intervalo do ano mês C podem ser convertidos. Para obter uma explicação das colunas e dos termos na tabela, consulte [convertendo dados de C para tipos de dados SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificador de tipo SQL|Teste|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR [a]<br /><br /> SQL_VARCHAR [a]<br /><br /> SQL_LONGVARCHAR [a]|Comprimento de byte de coluna >= comprimento de byte de caractere<br /><br /> Comprimento de byte de coluna < comprimento de byte de caractere [a]<br /><br /> O valor dos dados não é um literal de intervalo válido|n/d<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR [a]<br /><br /> SQL_WVARCHAR [a]<br /><br /> SQL_WLONGVARCHAR [a]|Comprimento de caractere de coluna >= comprimento de caractere de dados<br /><br /> Comprimento de caracteres de coluna < comprimento de caractere de dados [a]<br /><br /> O valor dos dados não é um literal de intervalo válido|n/d<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_DECIMAL [b]|A conversão de um intervalo de campo único não resultou no truncamento de dígitos inteiros<br /><br /> A conversão resultou em truncamento de dígitos inteiros|n/d<br /><br /> 22003|  
|SQL_INTERVAL_MONTH<br /><br /> SQL_INTERVAL_YEAR<br /><br /> SQL_INTERVAL_YEAR_TO_MONTH|O valor dos dados foi convertido sem truncamento de nenhum campo<br /><br /> Um ou mais campos de valor de dados foram truncados durante a conversão|n/d<br /><br /> 22015|  
  
 [a] todos os tipos de dados de intervalo de C podem ser convertidos em um tipo de dados de caractere.  
  
 [b] se o campo de tipo na estrutura de intervalo for de tal forma que o intervalo seja um único campo (SQL_YEAR ou SQL_MONTH), o tipo de intervalo C poderá ser convertido em qualquer numérico exato (SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_DECIMAL ou SQL_NUMERIC).  
  
 A conversão padrão de um tipo de intervalo C é para o tipo SQL de intervalo de ano/mês correspondente.  
  
 O driver ignora o valor de comprimento/indicador ao converter dados do tipo de dados do intervalo C e pressupõe que o tamanho do buffer de dados é o tamanho do tipo de dados do intervalo C. O valor de comprimento/indicador é passado no argumento *StrLen_or_Ind* em **SQLPutData** e no buffer especificado com o argumento *StrLen_or_IndPtr* em **SQLBindParameter**. O buffer de dados é especificado com o argumento *DataPtr* em **SQLPutData** e o argumento *ParameterValuePtr* em **SQLBindParameter**.
