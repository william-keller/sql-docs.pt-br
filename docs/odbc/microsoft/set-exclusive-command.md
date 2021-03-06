---
description: Comando SET EXCLUSIVE
title: Definir comando exclusivo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 413c9188decc9011c2816b692b1fb4b6112ec45b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466348"
---
# <a name="set-exclusive-command"></a>Comando SET EXCLUSIVE
Especifica se os arquivos de tabela são abertos para uso exclusivo ou compartilhado em uma rede.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>Argumentos  
 ATIVADO  
 Limita a acessibilidade de uma tabela aberta em uma rede para o usuário que a abriu. A tabela não está acessível a outros usuários na rede. SET EXCLUSIVE ON também impede que todos os outros usuários tenham acesso somente leitura.  
  
 OFF  
 (O padrão para o driver; os padrões para o Visual FoxPro são ON para a sessão de dados global e OFF para uma sessão de dados privada.) Permite que uma tabela aberta em uma rede seja compartilhada e modificada por qualquer usuário na rede.  
  
## <a name="remarks"></a>Comentários  
 Alterar a configuração de SET EXCLUSIVE não altera o status de tabelas abertas anteriormente. Por exemplo, se uma tabela for aberta com SET EXCLUSIVE Set como ON e SET EXCLUSIVE for alterado posteriormente para OFF, a tabela manterá seu status de uso exclusivo.  
  
## <a name="see-also"></a>Consulte Também  
 [Caixa de diálogo da instalação do Visual FoxPro do ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
