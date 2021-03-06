---
description: Conjunto de registros, propriedades SourceRecordset (RDS)
title: Conjunto de registros, Propriedades SourceRecordset (RDS) | Microsoft Docs
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Recordset property [ADO]
ms.assetid: a29e3fb9-306d-497a-9a59-1856a914e5e9
author: rothja
ms.author: jroth
ms.openlocfilehash: 27b6cf791b3b980000662f2073280d53f24aeaa1
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88981427"
---
# <a name="recordset-sourcerecordset-properties-rds"></a>Conjunto de registros, propriedades SourceRecordset (RDS)
Indica o objeto **Recordset** retornado de um objeto comercial personalizado.  
  
 **Aplica-se a:** [objeto DataControl (RDS)](./datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  A partir do Windows 8 e do Windows Server 2012, os componentes do servidor RDS não são mais incluídos no sistema operacional Windows (consulte Windows 8 e [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) para obter mais detalhes). Os componentes do cliente RDS serão removidos em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. Os aplicativos que usam o RDS devem migrar para o [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
DataControl.SourceRecordset = Recordset  
Recordset = DataControl.Recordset   
```  
  
#### <a name="parameters"></a>Parâmetros  
 *DataControl*  
 Uma variável de objeto que representa um [RDS. Objeto DataControl](./datacontrol-object-rds.md) .  
  
 *Recordset*  
 Uma variável de objeto que representa um objeto **Recordset** .  
  
## <a name="remarks"></a>Comentários  
 Você pode definir a propriedade **SourceRecordset** para um [conjunto de registros](../ado-api/recordset-object-ado.md) retornado de um objeto comercial personalizado.  
  
 Essas propriedades permitem que um aplicativo manipule o processo de associação por meio de um processo personalizado. Eles recebem um conjunto de linhas encapsulado em um **conjunto de registros** para que você possa interagir diretamente com o **conjunto de registros**, executando ações como definir propriedades ou Iterando por meio do conjunto de **registros**.  
  
 Você pode definir a propriedade **SourceRecordset** ou ler a propriedade **Recordset** em tempo de execução no código de script.  
  
 **SourceRecordset** é uma propriedade somente gravação, em contraste com a propriedade **Recordset** , que é uma propriedade somente leitura.  
  
## <a name="applies-to"></a>Aplica-se A  
 [Objeto DataControl (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Exemplo das propriedades Recordset e SourceRecordset (VBScript)](./recordset-and-sourcerecordset-properties-example-vbscript.md)   
 [Método createrecordset (RDS)](./createrecordset-method-rds.md)   
 [Método Query (RDS)](./query-method-rds.md)