---
description: Método WriteText
title: Método WriteText | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords:
- WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
author: rothja
ms.author: jroth
ms.openlocfilehash: d38d493fb57e8147f882056d07514ba9f405ecf9
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987717"
---
# <a name="writetext-method"></a>Método WriteText
Grava uma cadeia de caracteres de texto especificada em um objeto de [fluxo](./stream-object-ado.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *Dados*  
 Um valor de **cadeia de caracteres** que contém o texto em caracteres a ser gravado.  
  
 *Opções*  
 Opcional. Um valor [StreamWriteEnum](./streamwriteenum.md) que especifica se um caractere separador de linha deve ser gravado no final da cadeia de caracteres especificada.  
  
## <a name="remarks"></a>Comentários  
 As cadeias de caracteres especificadas são gravadas no objeto de **fluxo** sem nenhum espaço ou caractere intermediário entre cada cadeia de caracteres.  
  
 A [posição](./position-property-ado.md) atual é definida como o caractere após os dados gravados. O método **WriteText** não trunca o restante dos dados em um fluxo. Se você quiser truncar esses caracteres, chame [SetEOS](./seteos-method.md).  
  
 Se você gravar após a posição de [EOS](./eos-property.md) atual, o [tamanho](./size-property-ado-stream.md) do **fluxo** será aumentado para conter os novos caracteres e o **EOS** será movido para o novo último byte no **fluxo**.  
  
> [!NOTE]
>  O método **WriteText** é usado com fluxos de texto (o[tipo](./type-property-ado-stream.md) é **adTypeText**). Para fluxos binários (o**tipo** é **adTypeBinary**), use [Write](./write-method.md).  
  
## <a name="applies-to"></a>Aplica-se A  
 [Objeto Stream (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Método Write](./write-method.md)