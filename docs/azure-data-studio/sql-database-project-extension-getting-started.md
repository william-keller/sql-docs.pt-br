---
title: Introdução à extensão de Projetos de Banco de Dados SQL
description: Instale e use a extensão de Projetos de Banco de Dados SQL (versão prévia) para Azure Data Studio
ms.custom: seodec18
ms.date: 07/30/2020
ms.reviewer: drskwier, maghan, sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 9f7f277d3e038b42f72a887c8fa7e08739be9192
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180690"
---
# <a name="getting-started-with-the-sql-database-projects-extension-preview"></a>Introdução à extensão de Projetos de Banco de Dados SQL (versão prévia)

Este artigo descreve três maneiras de começar a usar a extensão de Projetos do Banco de Dados SQL:
1. Crie um projeto de banco de dados acessando o viewlet de **Projetos** no Explorer ou procurando por **Novo projeto de banco de dados** na paleta de comandos.
2. Os projetos de banco de dados existentes podem ser abertos por meio da opção **Abrir Projeto de Banco de Dados** da paleta de comandos.
3. Inicie de um banco de dados existente usando **Importar Novo Projeto de Banco de Dados** da paleta de comandos.

   ![Novo viewlet](media/extensions/sql-database-projects-extension/projects-viewlet.png)


### <a name="create-an-empty-database-project"></a>Criar um projeto de banco de dados vazio

 No viewlet **Projetos**, em **Explorer**, clique no botão **Novo Projeto** e insira um nome de projeto na entrada de texto exibida.  Na caixa de diálogo "Selecionar uma pasta" exibida, selecione um diretório para armazenar a pasta do projeto, o arquivo.sqlproj e outros conteúdos.
O projeto vazio será aberto e ficará visível no viewlet **Projetos** para edição.

### <a name="open-an-existing-project"></a>Abrir um projeto existente

No viewlet **Projetos**, clique no botão **Abrir projeto** e abra um arquivo *.sqlproj* existente no seletor de arquivos exibido. Os projetos existentes podem ser originados no Azure Data Studio ou nas [SQL Server Data Tools do Visual Studio](../ssdt/sql-server-data-tools.md).

O projeto existente será aberto e o seu conteúdo fica visível no viewlet **Projetos** para edição.

### <a name="create-a-database-project-from-an-existing-database"></a>Criar um projeto de banco de dados com base em um banco de dados existente

No viewlet **Projeto**, clique no botão **Importar projeto do banco de dados** e conecte-se a um SQL Server.  Depois que a conexão for estabelecida, selecione um banco de dados na lista de bancos de dados disponíveis e defina o nome do projeto.

Por fim, selecione uma estrutura de destino para a extração.  O novo projeto será aberto e conterá scripts SQL para o conteúdo do banco de dados selecionado.

## <a name="build-and-publish"></a>Criar e publicar

A implantação do projeto de banco de dados é alcançada na extensão de Projetos de Banco de Dados SQL para Azure Data Studio por meio da compilação do projeto em um [DACPAC](../relational-databases/data-tier-applications/data-tier-applications.md) (arquivo de aplicativo da camada de dados) e da publicação em uma plataforma compatível. Para obter mais informações sobre esse processo, confira [Compilar e publicar um projeto](sql-database-project-extension-build.md).

## <a name="schema-compare"></a>Comparação de esquemas
A extensão de Projetos de Banco de Dados SQL interage com a [extensão de Comparação de Esquemas](schema-compare-extension.md), se instalada, para comparar o conteúdo de um projeto com um dacpac ou um banco de dados existente.  A comparação de esquemas resultante pode ser usada para exibir e aplicar as diferenças da origem ao destino.

## <a name="next-steps"></a>Próximas etapas

- [Compilar e publicar um projeto com a extensão de Projetos de Banco de Dados SQL para Azure Data Studio](sql-database-project-extension-build.md)