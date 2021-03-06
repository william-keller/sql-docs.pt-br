---
title: 'Tutorial: desenvolver um modelo preditivo no R'
titleSuffix: SQL machine learning
description: Nesta série de tutoriais de quatro partes, você desenvolverá dados para treinar um modelo preditivo no R com o aprendizado de máquina do SQL.
ms.prod: sql
ms.technology: machine-learning
ms.topic: tutorial
author: cawrites
ms.author: chadam
ms.reviewer: garye, davidph
ms.date: 05/26/2020
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 6114ae9acf3ecdf8444dd6aec657d5c293fc4dae
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242303"
---
# <a name="tutorial-develop-a-predictive-model-in-r-with-sql-machine-learning"></a>Tutorial: Desenvolver um modelo preditivo no R com o machine learning do SQL
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Nesta séries de tutoriais de quatro partes, você usará R e um modelo de machine learning nos [Serviços de Machine Learning do SQL Server](../sql-server-machine-learning-services.md) ou nos [Clusters de Big Data](../../big-data-cluster/machine-learning-services.md) para prever o número de aluguéis de esqui.
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Nesta séries de tutoriais de quatro partes, você usará o R e um modelo de machine learning nos [Serviços de Machine Learning do SQL Server](../sql-server-machine-learning-services.md) para prever o número de aluguéis de esqui.
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Nesta séries de tutoriais de quatro partes, você usará o R e um modelo de machine learning no [SQL Server R Services](../r/sql-server-r-services.md) para prever o número de aluguéis de esqui.
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
Nesta série de tutoriais de quatro partes, você usará o R e um modelo de machine learning nos [Serviços de Machine Learning da Instância Gerenciada de SQL do Azure](/azure/azure-sql/managed-instance/machine-learning-services-overview) para prever o número de aluguéis de esqui.
::: moniker-end

Imagine que você tenha um negócio de aluguel de esqui e queira prever o número de locações que você terá em uma data futura. Essas informações ajudarão você a preparar seu estoque, sua equipe e suas instalações.

Na primeira parte desta série, você se preparará com os pré-requisitos. Nas partes dois e três, você desenvolverá alguns scripts de R em um notebook para preparar seus dados e treinar um modelo de machine learning. Em seguida, na terceira parte, você executará esses scripts R em um banco de dados usando procedimentos armazenados T-SQL.

Neste artigo, você aprenderá a:

> [!div class="checklist"]
> * Restaurar um banco de dados de exemplo 

Na [parte dois](r-predictive-model-prepare-data.md), você aprenderá a carregar os dados de um banco de dados em uma estrutura do Python e a prepará-los no R.

Na [parte três](r-predictive-model-train.md), você aprenderá a treinar um modelo de machine learning no R.

Na [parte quatro](r-predictive-model-deploy.md), você aprenderá a armazenar o modelo em um banco de dados e, em seguida, criará procedimentos armazenados com base nos scripts do R desenvolvidos nas partes dois e três. Os procedimentos armazenados serão executados no servidor para fazer previsões com base em novos dados.

## <a name="prerequisites"></a>Pré-requisitos

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
* Serviços de Machine Learning do SQL Server – para saber como instalar os Serviços de Machine Learning, confira o [Guia de instalação do Windows](../install/sql-machine-learning-services-windows-install.md) ou o [Guia de instalação do Linux](../../linux/sql-server-linux-setup-machine-learning.md?toc=%2Fsql%2Fmachine-learning%2Ftoc.json). Você também pode [habilitar Serviços de Machine Learning em Clusters de Big Data do SQL Server](../../big-data-cluster/machine-learning-services.md).
::: moniker-end
::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
* Serviços de Machine Learning do SQL Server – para saber como instalar os Serviços de Machine Learning, confira o [Guia de instalação do Windows](../install/sql-machine-learning-services-windows-install.md). 
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
* SQL Server 2016 R Services. Para saber como instalar o R Services, confira o [Guia de instalação do Windows](../install/sql-r-services-windows-install.md). 
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
* Serviços de Machine Learning da Instância Gerenciada de SQL do Azure. Para saber como se inscrever, confira a [Visão geral dos Serviços de Machine Learning da Instância Gerenciada de SQL do Azure](/azure/azure-sql/managed-instance/machine-learning-services-overview).

* [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) para restaurar o banco de dados de exemplo na Instância Gerenciada de SQL do Azure.
::: moniker-end

* IDE do R – Este tutorial usa o [RStudio Desktop](https://www.rstudio.com/products/rstudio/download/).

* RODBC – este driver é usado nos scripts do R que você desenvolverá neste tutorial. Se ele ainda não estiver instalado, instale-o usando o comando R `install.packages("RODBC")`. Para saber mais sobre o RODBC, confira [CRAN – Pacote RODBC](https://CRAN.R-project.org/package=RODBC).

* Ferramenta de consulta SQL – este tutorial pressupõe que você está usando o [Azure Data Studio](../../azure-data-studio/what-is.md). Para obter mais informações, confira [Como usar notebooks no Azure Data Studio](../../azure-data-studio/sql-notebooks.md).

## <a name="restore-the-sample-database"></a>Restaurar o banco de dados de exemplo

O banco de dados de exemplo usado neste tutorial foi salvo em um arquivo **.bak** de backup de banco de dados para você baixar e usar.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
> [!NOTE]
> Se você estiver usando Serviços de Machine Learning em Clusters de Big Data, confira como [Restaurar um banco de dados na instância mestra de cluster de Big Data do SQL Server](../../big-data-cluster/data-ingestion-restore-database.md).
::: moniker-end

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions"
1. Baixe o arquivo [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak).

1. Siga as instruções em [Restaurar um banco de dados de um arquivo de backup](../../azure-data-studio/tutorial-backup-restore-sql-server.md#restore-a-database-from-a-backup-file) no Azure Data Studio, usando estes detalhes:

   * Importe do arquivo **TutorialDB.bak** que você baixou
   * Nomeie o banco de dados de destino como "TutorialDB"

1. Para verificar se o banco de dados restaurado existe, consulte a tabela **dbo.rental_data**:

   ```sql
   USE TutorialDB;
   SELECT * FROM [dbo].[rental_data];
   ```
::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
1. Baixe o arquivo [TutorialDB.bak](https://sqlchoice.blob.core.windows.net/sqlchoice/static/TutorialDB.bak).

1. Siga as instruções descritas em [Restaurar um banco de dados em uma Instância Gerenciada](/azure/sql-database/sql-database-managed-instance-get-started-restore) no SQL Server Management Studio usando estes detalhes:

   * Importe do arquivo **TutorialDB.bak** que você baixou
   * Nomeie o banco de dados de destino como "TutorialDB"

1. Para verificar se o banco de dados restaurado existe, consulte a tabela **dbo.rental_data**:

   ```sql
   USE TutorialDB;
   SELECT * FROM [dbo].[rental_data];
   ```
::: moniker-end

## <a name="clean-up-resources"></a>Limpar os recursos

Se você não continuar com este tutorial, exclua o banco de dados TutorialDB.
## <a name="next-steps"></a>Próximas etapas

Na parte um desta série de tutoriais, você concluiu estas etapas:

* Instalar os pré-requisitos
* Restaurar um banco de dados de exemplo

Para preparar os dados para o modelo de machine learning, siga a parte dois desta série de tutoriais:

> [!div class="nextstepaction"]
> [Preparar os dados para treinar um modelo preditivo no R](r-predictive-model-prepare-data.md)
