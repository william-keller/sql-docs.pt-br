---
description: 'Coleções (Visual C++ índice de sintaxe com #import)'
title: 'Coleções (Visual C++ índice de sintaxe com #import) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- 'syntax indexes [ADO], ADO for Visual C++ syntax with #import'
- 'collections [ADO], ADO for Visual C++ syntax with #import'
- 'ADO for Visual C++ syntax with #import [ADO]'
- '#import [ADO]'
ms.assetid: 36fbca8e-1884-44b5-806b-d15e30f42fe6
author: rothja
ms.author: jroth
ms.openlocfilehash: cba9fa93b2f23388b11dc764a95b78d94df4874c
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975257"
---
# <a name="collections-visual-c-syntax-index-with-import"></a>Coleções (Visual C++ índice de sintaxe com #import)
É útil saber que as coleções herdam determinados métodos e propriedades comuns.  
  
 Todas as coleções herdam a propriedade **Count** e o método **Refresh** , e todas as coleções adicionam a propriedade **Item** . A coleção de **erros** adiciona o método **Clear** . A coleção **Parameters** herda os métodos **Append** e **delete** , enquanto a coleção **Fields** adiciona os métodos **Append**, **delete**e **Update** .  
  
## <a name="properties-collection"></a>Coleção de propriedades  
  
### <a name="methods"></a>Métodos  
  
```  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Propriedades  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="errors-collection"></a>Coleção de erros  
  
### <a name="methods"></a>Métodos  
  
```  
HRESULT Clear( );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Propriedades  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="parameters-collection"></a>Coleção Parâmetros  
  
### <a name="methods"></a>Métodos  
  
```  
HRESULT Append( IDispatch * Object );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Propriedades  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="fields-collection"></a>Coleção Campos  
  
### <a name="methods"></a>Métodos  
  
```  
HRESULT Append( _bstr_t Name, enum DataTypeEnum Type, long DefinedSize, enum FieldAttributeEnum Attrib, const _variant_t & FieldValue = vtMissing );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
HRESULT Update( );  
```  
  
### <a name="properties"></a>Propriedades  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Coleta de erros (ADO)](./errors-collection-ado.md)   
 [Coleção Fields (ADO)](./fields-collection-ado.md)   
 [Coleção Parameters (ADO)](./parameters-collection-ado.md)   
 [Coleção Properties (ADO)](./properties-collection-ado.md)