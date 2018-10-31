---
title: Como a consulta de HDFS em um cluster de big data do SQL Server | Microsoft Docs
description: Este tutorial demonstra como consultar dados do HDFS em um cluster de big data do SQL Server 2019 (visualização). Criar uma tabela externa nos dados no pool de armazenamento e, em seguida, executar uma consulta.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/11/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: c6f0f01936d5b6e570c2bff53d19ae7a64f151ab
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644083"
---
# <a name="tutorial-query-hdfs-in-a-sql-server-big-data-cluster"></a>Tutorial: Consultar o HDFS em um cluster de big data do SQL Server

Este tutorial demonstra como consultar dados do HDFS em um cluster de big data do SQL Server de 2019.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
> * Crie uma tabela externa que aponta para dados do HDFS em um cluster de big data.
> * Junte-se esses dados com dados de alto valor na instância do mestre.

> [!TIP]
> Se você preferir, você pode baixar e executar um script para os comandos neste tutorial. Para obter instruções, consulte a [exemplos de virtualização de dados](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization) no GitHub.

## <a name="prerequisites"></a>Prerequisites

- [Implantar um cluster de big data no Kubernetes](deployment-guidance.md).
- [Instalar o Studio de dados do Azure e a extensão do SQL Server 2019](deploy-big-data-tools.md).
- [Carregar dados de exemplo no cluster](#sampledata).

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-external-table-to-hdfs"></a>Criar uma tabela externa para o HDFS

O pool de armazenamento contém dados de sequência de cliques da web em um arquivo CSV armazenado em HDFS. Use as etapas a seguir para definir uma tabela externa que pode acessar os dados nesse arquivo.

1. No estúdio de dados do Azure, conecte-se à instância mestre do SQL Server do seu cluster de big data. Para obter mais informações, consulte [conectar-se a instância mestre do SQL Server](deploy-big-data-tools.md#master).

2. Clique duas vezes em que a conexão na **servidores** janela para mostrar o painel do servidor para a instância mestre do SQL Server. Selecione **nova consulta**.

   ![Consulta de instância mestre do SQL Server](./media/tutorial-query-hdfs-storage-pool/sql-server-master-instance-query.png)

3. Execute o seguinte comando Transact-SQL para alterar o contexto para o **vendas** banco de dados na instância do mestre.

   ```sql
   USE Sales
   GO
   ```

4. Defina o formato do arquivo CSV para ler do HDFS. Pressione F5 para executar a instrução.

   ```sql
   CREATE EXTERNAL FILE FORMAT csv_file
   WITH (
       FORMAT_TYPE = DELIMITEDTEXT,
       FORMAT_OPTIONS(
           FIELD_TERMINATOR = ',',
           STRING_DELIMITER = '"',
           FIRST_ROW = 2,
           USE_TYPE_DEFAULT = TRUE)
   );
   ```

5. Criar uma tabela externa que pode ler o `/clickstream_data` do pool de armazenamento. O **SqlStoragePool** está acessível da instância do mestre de um cluster de big data.

   ```sql
   CREATE EXTERNAL TABLE [web_clickstreams_hdfs]
   ("wcs_click_date_sk" BIGINT , "wcs_click_time_sk" BIGINT , "wcs_sales_sk" BIGINT , "wcs_item_sk" BIGINT , "wcs_web_page_sk" BIGINT , "wcs_user_sk" BIGINT)
   WITH
   (
       DATA_SOURCE = SqlStoragePool,
       LOCATION = '/clickstream_data',
       FILE_FORMAT = csv_file
   );
   GO
   ```

## <a name="query-the-data"></a>Consultar os dados

Execute a seguinte consulta para unir os dados do HDFS `web_clickstream_hdfs` tabela externa com os dados relacionais local `Sales` banco de dados.

```sql
SELECT  
    wcs_user_sk,
    SUM( CASE WHEN i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
    SUM( CASE WHEN i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
    SUM( CASE WHEN i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
    SUM( CASE WHEN i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
    SUM( CASE WHEN i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
    SUM( CASE WHEN i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
    SUM( CASE WHEN i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
    SUM( CASE WHEN i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
    SUM( CASE WHEN i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
    SUM( CASE WHEN i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
  FROM [dbo].[web_clickstreams_hdfs]
  INNER JOIN item it ON (wcs_item_sk = i_item_sk
                        AND wcs_user_sk IS NOT NULL)
GROUP BY  wcs_user_sk;
GO
```

## <a name="clean-up"></a>Limpar

Use o comando a seguir para remover a tabela externa usada neste tutorial.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_hdfs];
GO
```

## <a name="next-steps"></a>Próximas etapas

Avance para o próximo artigo para saber como consultar o Oracle de um cluster de big data.
> [!div class="nextstepaction"]
> [Consultar dados externos no Oracle](tutorial-query-oracle.md)