---
description: RangeMax (DMX)
title: RangeMax (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 1f7c3b58dde656e3afa07e9c53f1dca1c8116369
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487703"
---
# <a name="rangemax-dmx"></a>RangeMax (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Retorna a parte final superior da partição prevista que é descoberta para a coluna de dados discretos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
RangeMax(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Aplica-se A  
 Colunas escalares.  
  
## <a name="return-type"></a>Tipo de retorno  
 Valor escalar.  
  
## <a name="remarks"></a>Comentários  
 A função **RangeMax** pode ser usada em consultas [do modelo de &#60;&#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md) . Quando usada com esse tipo de consulta, a referência da coluna escalar poderá conter colunas contínuas ou distintas que são tanto previsíveis como de entrada.  
  
 Quando usado com [Select do modelo de &#60;&#62; junção de previsão &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md), as funções **RangeMin**, **RangeMid**e **RangeMax** retornam os valores de limite reais do Bucket especificado. Por exemplo, se uma previsão for realizada em uma coluna de dados discretos, a consulta retornará o número de partição previsto na coluna de dados discretos. As funções **RangeMin**, **RangeMid**e **RangeMax** descrevem o Bucket que a previsão especifica. Quando a função **RangeMax** é usada com uma instrução de junção de previsão, a referência de coluna escalar pode conter apenas colunas discretas e previsíveis.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna valores mínimo, máximo e médio para a coluna contínua Yearly Income no modelo de mineração Árvore de decisão.  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de função&#41; DMX &#40;extensões de mineração de dados](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funções &#40;&#41;DMX ](../dmx/functions-dmx.md)   
 [Funções de previsão gerais &#40;&#41;DMX ](../dmx/general-prediction-functions-dmx.md)   
 [&#41;&#40;DMX RangeMid ](../dmx/rangemid-dmx.md)   
 [&#41;&#40;DMX RangeMin ](../dmx/rangemin-dmx.md)  
  
  
