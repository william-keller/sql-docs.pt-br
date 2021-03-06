---
title: Mapeando bancos de dados MySQL para esquemas de SQL Server (MySQLToSQL) | Microsoft Docs
description: Saiba como personalizar os mapeamentos do SSMA para MySQL entre esquemas MySQL e SQL Server ou banco de dados SQL do Azure ou aceite o padrão.
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Mapping, Modifying target database and schema
- Mapping, reverting to default database and schema
ms.assetid: 5c6fb445-92ae-4933-b77d-80230931c024
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: ded91465a2a9c7b5a0e8ddcdc219b2af5a84395e
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935320"
---
# <a name="mapping-mysql-databases-to-sql-server-schemas-mysqltosql"></a>Mapear bancos de dados MySQL para esquemas SQL Server (MySQLToSQL)
Por padrão, o SSMA para MySQL migra todos os objetos em um esquema MySQL para um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] banco de dados SQL do ou do Azure chamado para o esquema. No entanto, você pode personalizar o mapeamento entre os esquemas do MySQL e o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] banco de dados SQL do Azure.  
  
## <a name="mysql-and-sql-server-or-sql-azure-schemas"></a>Esquemas MySQL e SQL Server ou SQL Azure  
O conceito de MySQL de um esquema é mapeado para o conceito de SQL Server de um banco de dados e um de seus esquemas. O SSMA se refere à combinação SQL Server de banco de dados e esquema como um esquema.  
  
O conceito de MySQL de um esquema é mapeado para o conceito de SQL Server de um banco de dados e um de seus esquemas. Por exemplo, o MySQL pode ter um esquema chamado **HR**. Uma instância do SQL Server pode ter um banco de dados chamado **HR**e, nesse banco de dados, são esquemas. Um esquema é o esquema de **dbo** (ou proprietário do banco de dados). Por padrão, a **HR** do esquema do MySQL será mapeada para o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] banco de dados e o esquema **hr. dbo**. O SSMA se refere à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] combinação de banco de dados e esquema como um esquema.  
  
Você pode modificar o mapeamento entre o MySQL e o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou os esquemas do Azure.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modificando o esquema e o banco de dados de destino  
No SSMA, você pode mapear um esquema MySQL para qualquer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esquema disponível ou SQL Azure.  
  
**Para modificar o banco de dados e o esquema**  
  
1.  No Gerenciador de metadados do MySQL, selecione **esquemas**.  
  
    A guia **mapeamento de esquema** também está disponível quando você seleciona esquemas individuais. A lista na guia **mapeamento de esquema** é personalizada para o objeto selecionado.  
  
2.  No painel direito, clique na guia **mapeamento de esquema** .  
  
    Você verá uma lista de todos os esquemas do MySQL, seguida por um valor de destino. Esse destino é indicado em uma notação de duas partes (*Database. Schema*) no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure onde seus objetos e dados serão migrados.  
  
3.  Selecione a linha que contém o mapeamento que você deseja alterar e clique em **Modificar**.  
  
    Na caixa de diálogo **escolher esquema de destino** , você pode procurar o banco de dados de destino e o esquema disponíveis ou digitar o banco de dados e o nome do esquema na caixa de texto em uma notação de duas partes (Database. Schema) e clicar em **OK**.  
  
4.  O destino é alterado na guia **mapeamento de esquema** .  
  
**Modos de mapeamento**  
  
-   Mapeando para SQL Server  
  
Você pode mapear o banco de dados de origem para qualquer banco de dados de destino. Por padrão, banco de dados de origem é mapeado para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o banco de dados de destino com o qual você se conectou usando o SSMA. Se o banco de dados de destino que está sendo mapeado não for existente no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , você será solicitado com uma mensagem **"o banco de dados e/ou esquema não existe nos metadados de destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Ele seria criado durante a sincronização. Deseja continuar? "** Clique em Sim. Da mesma forma, você pode mapear o esquema para um esquema não existente no banco de dados de destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que será criado durante a sincronização.  
  
-   Mapeando para SQL Azure  
  
Você pode mapear o banco de dados de origem para o banco de dados de destino conectado [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou para qualquer esquema no banco de dados de destino conectado [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Se você mapear o esquema de origem para qualquer esquema não existente no banco de dados de destino conectado, será exibida uma mensagem **"o esquema não existe nos metadados de destino. Ele seria criado durante a sincronização. Deseja continuar? "** Clique em Sim.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Revertendo para o banco de dados e esquema padrão  
Se você personalizar o mapeamento entre um esquema MySQL e um esquema de SQL Server, poderá reverter o mapeamento para os valores padrão.  
  
**Para reverter para o banco de dados e o esquema padrão**  
  
1.  Na guia mapeamento de esquema, selecione qualquer linha e clique em **Redefinir para padrão** para reverter para o banco de dados e o esquema padrão.  
  
## <a name="next-steps"></a>Próximas etapas  
Se desejar analisar a conversão de objetos MySQL em objetos SQL Server ou SQL Azure, você poderá [criar um relatório de conversão](assessing-mysql-databases-for-conversion-mysqltosql.md) , caso contrário, poderá [converter as definições de objeto do banco de dados mysql](converting-mysql-databases-mysqltosql.md) em esquemas SQL Server ou SQL Azure  
  
## <a name="see-also"></a>Consulte Também  
[Configurações do projeto &#40;conversão&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
[Conectando-se ao banco de dados SQL do Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
[Migrando bancos de dados MySQL para SQL Server-banco de MySQLToSql SQL do Azure &#40;&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Conectando-se ao SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
