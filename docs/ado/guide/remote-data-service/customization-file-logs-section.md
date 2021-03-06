---
description: Seção Logs do arquivo de personalização
title: Seção logs de arquivo de personalização | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- logs section in RDS [ADO]
- customization file in RDS [ADO]
ms.assetid: a368e264-865c-41ee-be00-d9097255c2ea
author: rothja
ms.author: jroth
ms.openlocfilehash: 890ba32615cdd78d9b999958f3ce3cb1e0755b81
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978237"
---
# <a name="customization-file-logs-section"></a>Seção Logs do arquivo de personalização
A seção **logs** contém uma entrada de arquivo de log, que especifica o nome de um arquivo que registra erros durante a operação do **DataFactory**.  
  
> [!IMPORTANT]
>  A partir do Windows 8 e do Windows Server 2012, os componentes do servidor RDS não são mais incluídos no sistema operacional Windows (consulte Windows 8 e [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) para obter mais detalhes). Os componentes do cliente RDS serão removidos em uma versão futura do Windows. Evite usar esse recurso em desenvolvimentos novos e planeje modificar os aplicativos que atualmente o utilizam. Os aplicativos que usam o RDS devem migrar para o [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintaxe  
 Uma entrada do arquivo de log está no formato:  
  
```console
  
err=  
FileName  
  
```  
  
## <a name="remarks"></a>Comentários  
  
|Parte|Descrição|  
|----------|-----------------|  
|**erra**|Uma cadeia de caracteres literal que indica que se trata de uma entrada de arquivo de log.|  
|*FileName*|Um caminho completo e um nome de arquivo. O nome de arquivo típico é **c:\msdfmap.log**.|  
  
 O arquivo de log conterá o nome de usuário, HRESULT, data e hora de cada erro.  
  
## <a name="see-also"></a>Consulte Também  
 [Seção conexão de arquivo de personalização](./customization-file-connect-section.md)   
 [Seção SQL do arquivo de personalização](./customization-file-sql-section.md)   
 [Seção UserList do arquivo de personalização](./customization-file-userlist-section.md)   
 [Personalização de datafactory](./datafactory-customization.md)   
 [Configurações do cliente necessárias](./required-client-settings.md)   
 [Noções básicas sobre o arquivo de personalização](./understanding-the-customization-file.md)   
 [Escrever seu próprio manipulador personalizado](./writing-your-own-customized-handler.md)