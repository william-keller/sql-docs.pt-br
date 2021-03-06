---
description: Executar o aplicativo do cliente do Data Quality
title: Executar o aplicativo do cliente do Data Quality
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.browseforservers.f1
- sql13.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
author: swinarko
ms.author: sawinark
ms.openlocfilehash: ed5b6449ea470a63e27a1d23a057ed6507c2ed2e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466648"
---
# <a name="run-the-data-quality-client-application"></a>Executar o aplicativo do cliente do Data Quality

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  Executar [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], e fazer logon em um [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Pré-requisitos  
 Você precisa ter concluído a instalação do [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] executando o arquivo DQSInstaller.exe. Para obter mais informações, consulte [Executar o DQSInstaller.exe para concluir a instalação do Data Quality Server](../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
###  <a name="security"></a><a name="Security"></a> Segurança  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissões  
 Você deve ter uma das três funções DQS (dqs_adminstrator, dqs_kb_editor ou dqs_kb_operator) concedidas no banco de dados DQS_MAIN para que possa fazer logon no [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
##  <a name="run-data-quality-client"></a><a name="Run"></a> Executar Data Quality Client  
 Para executar o [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] no computador em que ele foi instalado:  
  
1.  Clique em **Iniciar**, aponte para **Todos os Programas**, clique em **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, clique em **Data Quality Services**e clique em **Cliente Data Quality**.  
  
2.  Na caixa de diálogo **Conectar ao Servidor**:  
  
    1.  Especifique o servidor ao qual você deseja conectar o aplicativo [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Selecione **(LOCAL)** para conectar ao [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] no computador local. Você também pode clicar na seta para baixo e selecionar **\<Browse network for more servers>** para se conectar a um servidor diferente (ou para se conectar ao servidor local por nome). A caixa de diálogo **Procurar Servidores** será exibida. Você pode selecionar um servidor na guia **Servidores Locais** ou na guia **Servidores de Rede** .  
  
    2.  Para criptografar a transferência de dados entre o [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] e o [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], clique em **Opções**e marque a caixa de seleção **Criptografar Conexão** .  
  
3.  Clique em **Conectar**.  
  
 A tela inicial do [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] é exibida. Para obter mais informações, consulte [Data Quality Services Concepts](../data-quality-services/data-quality-client-home-screen.md).  
  
  
