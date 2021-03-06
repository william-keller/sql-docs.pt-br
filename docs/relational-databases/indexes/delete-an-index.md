---
description: Excluir um índice
title: Excluir um índice | Microsoft Docs
ms.custom: ''
ms.date: 02/17/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- removing indexes
- deleting indexes
- dropping indexes
- indexes [SQL Server], dropping
- index deletions [SQL Server]
ms.assetid: fd38a0ed-26c4-4c76-9ef7-e0a16147329d
author: MikeRayMSFT
ms.author: mikeray
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9279f22be324858e2a71ea523cab000c8f7253cf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490947"
---
# <a name="delete-an-index"></a>Excluir um índice
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Este tópico descreve como excluir (descartar) um índice no [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Neste tópico**  
  
-   **Antes de começar:**  
  
     [Limitações e restrições](#Restrictions)  
  
     [Segurança](#Security)  
  
-   **Para excluir um índice, usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Antes de começar  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitações e restrições  
 Índices criados em decorrência de uma restrição PRIMARY KEY ou UNIQUE não podem ser excluídos com esse método. Em vez disso, a restrição deve ser excluída. Para remover a restrição e o índice correspondente, use [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) com a cláusula DROP CONSTRAINT em [!INCLUDE[tsql](../../includes/tsql-md.md)]. Para obter mais informações, consulte [Delete Primary Keys](../../relational-databases/tables/delete-primary-keys.md).  
  
###  <a name="security"></a><a name="Security"></a> Segurança  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissões  
 Requer a permissão ALTER na tabela ou exibição. Essa permissão é concedida por padrão à função de servidor fixa **sysadmin** e às funções de banco de dados fixas **db_ddladmin** e **db_owner** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Usando o SQL Server Management Studio  
  
#### <a name="to-delete-an-index-by-using-object-explorer"></a>Para excluir um índice usando o Pesquisador de Objetos  
  
1.  No Pesquisador de Objetos, expanda o banco de dados que contém a tabela da qual você deseja excluir um índice.  
  
2.  Expanda a pasta **Tabelas** .  
  
3.  Expanda a tabela que contém o índice que você deseja excluir.  
  
4.  Expanda a pasta **Índices** .  
  
5.  Clique com o botão direito do mouse no índice a ser excluído e selecione **Excluir**.  
  
6.  Na caixa de diálogo **Excluir Objeto** , verifique se o índice correto está na grade **Objeto a ser excluído** e clique em **OK**.  
  
#### <a name="to-delete-an-index-using-table-designer"></a>Para excluir um índice usando o Designer de Tabela  
  
1.  No Pesquisador de Objetos, expanda o banco de dados que contém a tabela da qual você deseja excluir um índice.  
  
2.  Expanda a pasta **Tabelas** .  
  
3.  Clique com o botão direito do mouse na tabela que contém o índice a ser excluído e clique em Design.  
  
4.  No menu **Designer de Tabela** , clique em **Índices/Chaves**.  
  
5.  Na caixa de diálogo **Índices/Chaves** , selecione o índice que você deseja excluir.  
  
6.  Clique em **Excluir**.  
  
7.  Clique em **fechar**  
  
8.  No menu **Arquivo** , selecione **Salvar**_table_name_.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Usando o Transact-SQL  
  
#### <a name="to-delete-an-index"></a>Para excluir um índice  
  
1.  No **Pesquisador de Objetos**, conecte-se a uma instância do [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- delete the IX_ProductVendor_BusinessEntityID index  
    -- from the Purchasing.ProductVendor table  
    DROP INDEX IX_ProductVendor_BusinessEntityID   
        ON Purchasing.ProductVendor;  
    GO  
    ```  
  
 Para obter mais informações, veja [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md).  
  
  
