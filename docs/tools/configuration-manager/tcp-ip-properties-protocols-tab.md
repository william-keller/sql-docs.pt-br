---
title: Propriedades do TCP/IP (guia Protocolos)
description: Use as opções na guia Protocolos da caixa de diálogo Propriedades de TCP/IP para configurar o intervalo de keep alive, o sinalizador habilitado e outras propriedades.
ms.custom: seo-lt-2019
ms.date: 08/24/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2e9bf22b501a097e59af3bef953ffcbaa26780c1
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85880292"
---
# <a name="tcpip-properties-protocols-tab"></a>Propriedades do TCP/IP (guia Protocolos)
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  Use a caixa de diálogo **Propriedades do TCP/IP** para configurar as opções do protocolo TCP/IP. Clique em **TCP/IP** no painel esquerdo, para mostrar configurações individuais de endereço IP no painel de detalhes.  
  
 O Microsoft SQL Server deve ser reiniciado para que as alterações tenham efeito.  
  
## <a name="options"></a>Opções  
 **Enabled**  
 Os valores possíveis são **Sim** e **Não**.  
  
 **Keep Alive**  
 Especifique o intervalo (em milissegundos) no qual os pacotes keep-alive são transmitidos para verificar se o computador remoto de uma conexão ainda está disponível.  
  
 **Listen All**  
 Especifique se o SQL Server escutará em todos os endereços IP associados às placas de rede no computador. Se for definido como **No**, configure cada endereço IP separadamente usando a caixa de diálogo de propriedades de cada endereço IP. Se for definido como **Yes**, as configurações da caixa de propriedades **IPAll** se aplicarão a todos os endereços IP. O valor padrão é **Yes**.  
  
 **No Delay**  
 O SQL Server não implementa alterações a esta propriedade.  
  
## <a name="see-also"></a>Consulte Também  
 [Escolhendo um protocolo de rede](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [Criando uma cadeia de conexão válida usando TCP/IP](creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
