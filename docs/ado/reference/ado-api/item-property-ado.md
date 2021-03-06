---
description: Propriedade Item (ADO)
title: Propriedade Item (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameters::GetItem
- Indexes::GetItem
- Parameters::Item
- Tables::Item
- Procedures::Item
- Users::GetItem
- Tables::GetItem
- Procedures::GetItem
- Users::get_Item
- Users::Item
- Views::GetItem
- Groups::Item
- Groups::get_Item
- Columns::Item
- Indexes::Item
- Fields15::GetItem
- Columns::GetItem
- Fields::Item
- Indexes::get_Item
- Columns::get_Item
- Fields15::Item
- Views::get_Item
- Groups::GetItem
- Errors::get_Item
- Fields15::get_Item
- Tables::get_Item
- Views::Item
- Errors::GetItem
- Parameters::get_Item
- Errors::Item
- Procedures::get_Item
helpviewer_keywords:
- Item property [ADO]
ms.assetid: e11484bb-c5c7-42d8-9bb8-21572125d727
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f54ba0276affc1b098b3e499c31769f4cf9f927
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990747"
---
# <a name="item-property-ado"></a>Propriedade Item (ADO)
Indica um membro específico de uma coleção, por nome ou número ordinal.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Set object = collection.Item ( Index )  
```  
  
## <a name="return-value"></a>Valor retornado  
 Retorna uma referência de objeto.  
  
## <a name="parameters"></a>Parâmetros  
 *Index*  
 Uma expressão **Variant** que é avaliada como o nome ou o número ordinal de um objeto em uma coleção.  
  
## <a name="remarks"></a>Comentários  
 Use a propriedade **Item** para retornar um objeto específico em uma coleção. Se o **Item** não conseguir localizar um objeto na coleção correspondente ao argumento de *índice* , ocorrerá um erro. Além disso, algumas coleções não oferecem suporte a objetos nomeados; para essas coleções, você deve usar referências de número ordinal.  
  
 A propriedade **Item** é a propriedade padrão para todas as coleções; Portanto, as seguintes formas de sintaxe são intercambiáveis:  
  
```  
collection.Item (Index)  
collection (Index)  
```  
  
## <a name="applies-to"></a>Aplica-se A  

:::row:::
    :::column:::
        [Coleção Axes (ADO MD)](../ado-md-api/axes-collection-ado-md.md)  
        [Coleção Columns (ADOX)](../adox-api/columns-collection-adox.md)  
        [Coleção CubeDefs (ADO MD)](../ado-md-api/cubedefs-collection-ado-md.md)  
        [Coleção Dimensions (ADO MD)](../ado-md-api/dimensions-collection-ado-md.md)  
        [Coleção Errors (ADO)](./errors-collection-ado.md)  
        [Coleção Fields (ADO)](./fields-collection-ado.md)  
        [Coleção Groups (ADOX)](../adox-api/groups-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Coleção Hierarchies (ADO MD)](../ado-md-api/hierarchies-collection-ado-md.md)  
        [Coleção Indexes (ADOX)](../adox-api/indexes-collection-adox.md)  
        [Coleção Keys (ADOX)](../adox-api/keys-collection-adox.md)  
        [Coleção Levels (ADO MD)](../ado-md-api/levels-collection-ado-md.md)  
        [Coleção Members (ADO MD)](../ado-md-api/members-collection-ado-md.md)  
        [Coleção Parameters (ADO)](./parameters-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Coleção Positions (ADO MD)](../ado-md-api/positions-collection-ado-md.md)  
        [Coleção Procedures (ADOX)](../adox-api/procedures-collection-adox.md)  
        [Coleção Properties (ADO)](./properties-collection-ado.md)  
        [Coleção Tables (ADOX)](../adox-api/tables-collection-adox.md)  
        [Coleção Users (ADOX)](../adox-api/users-collection-adox.md)  
        [Coleção Views (ADOX)](../adox-api/views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Consulte Também  
 [Exemplo da Propriedade Item (VB)](./item-property-example-vb.md)   
 [Exemplo da propriedade Item (VC++)](./item-property-example-vc.md)