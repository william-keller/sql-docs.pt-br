---
description: 'IBCPSession:: BCPWriteFmt (provedor de OLE DB de cliente nativo)'
title: 'IBCPSession:: BCPWriteFmt (provedor de OLE DB de cliente nativo) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- IBCPSession::BCPWriteFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPWriteFmt method
ms.assetid: add50425-2ed6-411a-a391-4ce63c364892
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eaeb5d8806b09dc9239b07008dde23053f066abe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486662"
---
# <a name="ibcpsessionbcpwritefmt-native-client-ole-db-provider"></a>IBCPSession:: BCPWriteFmt (provedor de OLE DB de cliente nativo)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Grava informações de formato relativas a cada coluna no arquivo de formato.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
HRESULT BCPWriteFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Comentários  
 O arquivo de formato especifica o formato de dados de um arquivo de dados criado por cópia em massa. As chamadas aos métodos [IBCPSession::BCPColumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) e [IBCPSession::BCPColFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) definem o formato do arquivo de dados. O método **BCPWriteFmt** salva essa definição no arquivo referenciado pelo argumento pwszFormatFile.  
  
 O método **BCPWriteFmt** pode salvar os arquivos de formato em xml ou formato de texto. Isso precisa ser indicado usando a opção de controle BCP_OPTION_XML com o método [IBCPSession::BCPControl](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md).  
  
 Para carregar um arquivo de formato salvo, use o método [IBCPSession::BCPReadFmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md).  
  
## <a name="arguments"></a>Argumentos  
 *pwszFormatFile*[in]  
 O caminho e o nome do arquivo que contém os valores de formato do arquivo de dados.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 S_OK  
 O método foi bem-sucedido.  
  
 E_FAIL  
 Um erro específico do provedor ocorreu. Para obter informações detalhadas, use a interface [ISQLServerErrorInfo](https://docs.microsoft.com/sql/connect/oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db?view=sql-server-ver15).  
  
 E_OUTOFMEMORY  
 Erro de memória insuficiente.  
  
 E_UNEXPECTED  
 A chamada para o método era inesperada. Por exemplo, o método [IBCPSession::BCPInit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) não foi chamado antes desse método.  
  
## <a name="see-also"></a>Consulte Também  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [Executando operações de cópia em massa](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
