---
description: UniqueName (MDX)
title: UniqueName (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3108cf8fdfbd0bc6864438be9ac95ff909308bc6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341162"
---
# <a name="uniquename-mdx"></a>UniqueName (MDX)


  Retorna o nome exclusivo de uma dimensão, hierarquia, nível ou membro especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Dimension expression syntax  
Dimension_Expression.UniqueName  
  
Hierarchy expression syntax  
Hierarchy_Expression.UniqueName  
  
Level expression syntax  
Level_Expression.UniqueName  
  
Member expression syntax  
Member_Expression.UniqueName  
```  
  
## <a name="arguments"></a>Argumentos  
 *Dimension_Expression*  
 Uma linguagem MDX válida que retorna uma expressão que será resolvida em uma dimensão.  
  
 *Hierarchy_Expression*  
 Uma linguagem MDX válida que retorna uma hierarquia.  
  
 *Level_Expression*  
 Uma linguagem MDX válida que retorna um nível.  
  
 *Member_Expression*  
 Uma linguagem MDX válida que retorna um membro.  
  
## <a name="remarks"></a>Comentários  
 A função **UniqueName** retorna o nome exclusivo do objeto, não o nome retornado pela função [Name](../mdx/name-mdx.md) . O nome retornado não inclui o nome do cubo. Os resultados retornados dependem das configurações do servidor ou da propriedade de cadeia de conexão MDX Unique Name Style.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna um valor de nome exclusivo para a dimensão Produto, a hierarquia Categorias de Produtos, nível Subcategoria e o membro Suportes para Bicicleta do cubo Adventure Works.  
  
```  
WITH MEMBER DimensionUniqueName   
   AS [Product].UniqueName  
MEMBER HierarchyUniqueName   
   AS [Product].[Product Categories].UniqueName  
MEMBER LevelUniqueName   
   AS [Product].[Product Categories].[Subcategory].UniqueName  
MEMBER MemberUniqueName   
   AS [Product].[Product Categories].[Subcategory].[Bike Racks]  
SELECT   
   {DimensionUniqueName  
   , HierarchyUniqueName  
   , LevelUniqueName  
   , MemberUniqueName }  
   ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Referência da Função MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
