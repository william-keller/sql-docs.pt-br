---
description: EXPORT (DMX)
title: EXPORTAR (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 689ab632604d26a349dbb3f2a40d5f1b7cf8d702
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88353222"
---
# <a name="export-dmx"></a>EXPORT (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Extrai um modelo de mineração ou objeto de estrutura de mineração do servidor para um arquivo .abf (Analysis Services Backup).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
EXPORT <object type> <object name>[, <object name>] [<object type> <object name>[, <object name] ] TO <filename> [WITH DEPENDENCIES]  
```  
  
## <a name="arguments"></a>Argumentos  
 *tipo de objeto*  
 Opcional. o tipo do objeto a ser exportado (modelo de mineração ou estrutura de mineração).  
  
 *nome do objeto*  
 Opcional. Nome do objeto a ser exportado.  
  
 *nome do arquivo*  
 Nome e local do arquivo a ser exportado como cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Se a instrução especificar um modelo de mineração, o arquivo resultante também conterá uma estrutura de mineração associada. Se a instrução especifica **com dependências**, todos os objetos necessários para processar o objeto (por exemplo, a fonte de dados e a exibição da fonte de dados) são incluídos no arquivo. ABF.  
  
 Você deve ser um administrador de banco de dados ou servidor para exportar ou importar objetos de um [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] banco de dados.  
  
## <a name="export-mining-structure-example"></a>Exemplo de estrutura de mineração de exportação  
 O exemplo a seguir exporta as estruturas de mineração Targeted Mailing e Forecasting, e o modelo de mineração Association para um local de arquivo específico. Como o modelo Association integra a estrutura de mineração de Market Basket, o exemplo exporta igualmente a estrutura Market Basket. Qualquer outro modelo de mineração que possa existir como parte da estrutura de mineração de cesta de mercado não será exportado porque o modelo de associação foi exportado usando o **modelo de mineração**, não a **estrutura de mineração**.  
  
```  
EXPORT MINING STRUCTURE [Targeted Mailing], [Forecasting] MINING MODEL Association TO 'C:\TM_NEW.abf'  
```  
  
## <a name="export-mining-model-example"></a>Exemplo de modelo de mineração de exportação  
 O exemplo a seguir exporta o modelo de mineração de Associação para um local de arquivo especificado. Como a instrução especifica **com dependências**, os objetos fonte de dados e exibição da fonte de dados também estão incluídos no arquivo. ABF.  
  
```  
EXPORT MINING MODEL [Association] TO 'C:\Association_NEW.abf' WITH DEPENDENCIES  
```  
  
## <a name="see-also"></a>Consulte Também  
 [&#40;&#41; instruções de definição de dados DMX de extensões de mineração de dados](../dmx/dmx-statements-data-definition.md)   
 [&#40;instruções de manipulação de dados do DMX&#41; extensões do Data Mining](../dmx/dmx-statements-data-manipulation.md)   
 [Referência de instrução&#41; &#40;DMX de extensões de mineração de dados](../dmx/data-mining-extensions-dmx-statements.md)   
 [IMPORTAR &#40;&#41;DMX ](../dmx/import-dmx.md)   
 [Exportar e importar objetos de mineração de dados](https://docs.microsoft.com/analysis-services/data-mining/export-and-import-data-mining-objects)  
  
  
