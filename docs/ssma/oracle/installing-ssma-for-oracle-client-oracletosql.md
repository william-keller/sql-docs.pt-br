---
title: Instalando o SSMA para Oracle Client (OracleToSQL) | Microsoft Docs
description: Saiba mais sobre os pré-requisitos de instalação para o cliente do Assistente de Migração do SQL Server (SSMA) para Oracle e como instalá-los.
ms.prod: sql
ms.custom: ''
ms.date: 07/14/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: d5d4903d-e296-4bbf-8780-63674c4d62d5
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 939504092ef7ae9dc13bdcf829f6ea5e88ce59f9
ms.sourcegitcommit: fd7b268a34562d70d46441f689543ecce7df2e4d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86411264"
---
# <a name="installing-ssma-for-oracle-client-oracletosql"></a>Instalando o cliente SSMA para Oracle (OracleToSQL)

O cliente do SSMA consiste nos arquivos de programa que executam as seguintes tarefas:  
  
- Conecte-se a um banco de dados Oracle.
- Conectar-se a uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
- Converta objetos de banco de dados Oracle em [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sintaxe.
- Carregue os objetos no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
- Migre dados para o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

Este tópico fornece os pré-requisitos de instalação e as instruções para instalar o SSMA.

## <a name="prerequisites"></a>Pré-requisitos

O SSMA foi projetado para funcionar com o Oracle 9 ou versões posteriores e todas as edições do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

Antes de instalar o SSMA, verifique se o computador atende aos seguintes requisitos:

- Windows 7 ou versões posteriores ou Windows Server 2008 ou versões posteriores.
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 ou uma versão posterior.
- A [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] versão 4.7.2 ou posterior. Você pode obtê-lo no [centro de desenvolvedores .NET Framework](https://go.microsoft.com/fwlink/?LinkId=48882).
- Conectividade com os bancos de dados Oracle que você deseja migrar.
- Acesso a e permissões suficientes no computador que hospeda a instância de destino do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] onde você migrará objetos de banco de dados e os mesmos. Para obter mais informações, consulte [conectando-se a SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md).
- 4 GB de RAM recomendado.  
  
## <a name="installing-the-ssma-for-oracle-client"></a>Instalando o cliente do SSMA para Oracle

O SSMA é um download da Web. Para baixar a versão mais recente, consulte a [página de download do assistente de migração do SQL Server](https://aka.ms/ssmafororacle).

Para instalar o cliente SSMA:

1. Clique duas vezes em **SSMAforOracle_*n*. msi**, em que *n* é o número da compilação.
2. Na página de Boas-vindas, clique em **Avançar**.

   Se você não tiver os pré-requisitos instalados, será exibida uma mensagem que indica que você deve primeiro instalar os componentes necessários. Verifique se você instalou todos os pré-requisitos e execute o programa de instalação novamente.  

3. Leia o contrato de licença de usuário final. Se você concordar, selecione **aceito o contrato**e clique em **Avançar**.
4. Na página **escolher tipo de instalação** , clique em **típico**.
5. Na página **pronto para instalar** , você pode habilitar ou desabilitar a telemetria e as verificações de atualização automática toda vez que a ferramenta for iniciada. Clique em **Instalar** para iniciar a instalação.

> [!IMPORTANT]
> Desinstale todas as versões anteriores do SSMA para Oracle antes de instalar a nova versão.

O local de instalação padrão é `C:\Program Files\Microsoft SQL Server Migration Assistant for Oracle`.

Além dos arquivos de programa do SSMA, você também deve instalar o SSMA para Oracle Extension Pack em [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Para obter mais informações, consulte [instalando componentes do SSMA no SQL Server](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md).

## <a name="see-also"></a>Confira também

- [Instalar os componentes do SSMA no SQL Server](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)
- [Migrando Bancos de Dados Oracle para o SQL Server](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)
