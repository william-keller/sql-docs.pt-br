---
title: Caixa de diálogo Colunas de Índice de Texto Completo
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextcolumn
ms.assetid: a6f41c5c-d950-4d64-9e42-d062925917b6
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 0f52e63938317eff7f47e56300decc874997272d
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012149"
---
# <a name="full-text-index-columns-dialog-box-visual-database-tools"></a>Caixa de diálogo colunas de índice de texto completo (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Esta caixa de diálogo lista as colunas que participam do índice de texto completo para a tabela aberta no Designer de Tabela. Para acessar essa caixa de diálogo, clique com o botão direito do mouse na tabela no Designer de Tabela, escolha **Índice de Texto Completo** e, na caixa de diálogo **Índice de Texto Completo**, clique no índice com as colunas que você deseja exibir ou editar, clique no campo **Colunas** na grade à direita e clique nas reticências ( **…** ).  
  
## <a name="options"></a>Opções  
**Coluna**  
Mostra os nomes das colunas que fazem parte do índice de texto completo. Para adicionar uma coluna, clique na primeira célula vazia e escolha uma coluna da lista suspensa. Só estarão acessíveis as colunas com tipos de dados baseados em texto ou em imagens.  
  
**Tipo de Dados**  
Mostra o tipo de dados para cada coluna. Trata-se de uma propriedade somente leitura. Para alterar um tipo de dados, abra a tabela no Designer de Tabela, clique na coluna e edite o tipo de dados na guia **Propriedades da Coluna** .  
  
**Digitado por Coluna**  
Aplica-se somente a colunas com o tipo de dados **image**. Fornece uma lista suspensa na qual você pode escolher quais das outras colunas representam o tipo de dados dessa coluna. Se esta coluna não for do tipo de dados **image** , o valor será Nenhum.  
  
Colunas com o tipo de dados **image** podem conter arquivos do Microsoft Office (arquivos .doc, .xls e .ppt), arquivo de texto (arquivos .txt) e arquivos HTML (arquivos .htm); definir o tipo de dados dessa coluna para imagem permite que a pesquisa de texto completo busque o conteúdo dos arquivos.  
  
**Idioma**  
Lista os idiomas disponíveis. Escolha o idioma da lista suspensa de idiomas que é apropriado para seus dados de coluna. Por exemplo, se você estiver usando um sistema operacional em inglês, mas quiser indexar uma coluna que contenha texto em alemão, escolha alemão na lista suspensa para melhorar o desempenho do índice.  
  
**Semântica Estatística**  
Especifique se habilitará a indexação semântica da coluna selecionada. Para obter mais informações, consulte [Espaço reservado Pesquisa semântica](https://msdn.microsoft.com/cd8faa9d-07db-420d-93f4-a2ea7c974b97).  
  
Se você selecionar um **Idioma** antes de selecionar **Semântica Estatística**, e o idioma selecionado não tiver um Modelo de Idioma Semântico associado, a caixa de seleção **Semântica Estatística** será desabilitada. Se você selecionar **Semântica Estatística** antes de selecionar um **Idioma**, os idiomas disponíveis na caixa de combinação suspensa serão restringidos a esses para os quais o Modelo de Idioma Semântico dá suporte.  
  
## <a name="see-also"></a>Consulte Também  
[Caixa de diálogo Índice de Texto Completo &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/full-text-index-dialog-box-visual-database-tools.md)  
  
