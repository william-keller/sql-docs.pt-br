---
description: 'ISSAsynchStatus:: WaitForAsynchCompletion no SQL Server Native Client (OLE DB)'
title: 'ISSAsynchStatus:: WaitForAsynchCompletion (provedor de OLE DB de cliente nativo) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
apitype: COM
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b5557c9f73effcea3064b674081bd00901ef9e0b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490799"
---
# <a name="issasynchstatuswaitforasynchcompletion-in-sql-server-native-client-ole-db"></a>ISSAsynchStatus:: WaitForAsynchCompletion no SQL Server Native Client (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Aguarda até que a operação com execução assíncrona seja concluída ou que um tempo limite seja atingido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
HRESULT WaitForAsynchCompletion(   
        DWORD dwMillisecTimeOut);  
```  
  
## <a name="arguments"></a>Argumentos  
 *dwMillisecTimeOut*[in]  
 Tempo limite em milissegundos.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 S_OK  
 O método foi bem-sucedido.  
  
 E_UNEXPECTED  
 Um conjunto de linhas está em um estado não usado porque **ITransaction::Commit** ou **ITransaction::Abort** foi chamado ou o conjunto de linhas foi cancelado durante sua fase de inicialização.  
  
 DB_E_CANCELED  
 O processamento assíncrono foi cancelado durante a população do conjunto de linhas ou a inicialização de objeto de fonte de dados.  
  
 DB_S_ASYNCHRONOUS  
 A operação ainda não foi concluída, embora o tempo limite especificado tenha sido atingido.  
  
> [!NOTE]  
>  Além dos valores de código de retorno listados anteriormente, o método **ISSAsynchStatus::WaitForAsynchCompletion** também dá suporte aos valores de código de retorno retornados pelos principais métodos **ICommand::Execute** e **IDBInitialize::Initialize** do OLE DB.  
  
## <a name="remarks"></a>Comentários  
 O método **ISSAsynchStatus::WaitForAsynchCompletion** não será retornado enquanto o valor de tempo limite (em milissegundos) não se esgotar ou a operação pendente não for concluída. O objeto **Command** tem uma propriedade **CommandTimeout** que controla o número de segundos que uma consulta será executada antes de exceder o tempo limite. A propriedade **CommandTimeout** será ignorada se for usada em conjunto com o método **ISSAsynchStatus::WaitForAsynchCompletion**.  
  
 A propriedade de tempo limite é ignorada para operações assíncronas. O parâmetro de tempo limite de **ISSAsynchStatus::WaitForAsynchCompletion** especifica o tempo máximo decorrido antes de o controle ser retornado ao chamador. Se esse tempo limite expirar, DB_S_ASYNCHRONOUS será retornado. Os tempos limite nunca cancelam operações assíncronas. Se o aplicativo precisar cancelar uma operação assíncrona que não tenha sido concluída dentro de um tempo limite, ele deverá aguardar o tempo limite e, em seguida, cancelar explicitamente a operação, caso DB_S_ASYNCHRONOUS seja retornado.  
  
> [!NOTE]  
>  Quando os Componentes de Serviço do OLE DB são usados, S_OK pode ser retornado quando DB_S_ASYNCHRONOUS é esperado; portanto, os aplicativos devem chamar [ISSAsynchStatus::GetStatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-getstatus-ole-db.md) para verificar a conclusão quando S_OK ou DB_S_ASYNCHRONOUS é retornado.  
  
 Se o valor de *dwMillisecTimeOut* for definido como INFINITE, o método **ISSAsynchStatus::WaitForAsynchCompletion** será bloqueado até a conclusão da operação. Se o valor de *dwMillisecTimeOut* for definido como 0, o método será retornado imediatamente com o status da operação pendente. Se o tempo limite expirar antes da conclusão da operação, DB_S_ASYNCHRONOUS será retornado.  
  
 Se a operação for concluída antes da expiração do tempo limite, o HRESULT retornado será o HRESULT retornado pela operação (o HRESULT retornado executou a operação de forma síncrona).  
  
 Além disso, a propriedade SSPROP_ISSAsynchStatus foi adicionada ao conjunto de propriedades DBPROPSET_SQLSERVERROWSET. Os provedores que dão suporte à interface [ISSAsynchStatus](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md) precisam implementar essa propriedade com um valor de VARIANT_TRUE.  
  
## <a name="see-also"></a>Consulte Também  
 [Executando operações assíncronas](../../relational-databases/native-client/features/performing-asynchronous-operations.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
