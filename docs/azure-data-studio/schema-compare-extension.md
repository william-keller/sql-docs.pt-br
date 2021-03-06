---
title: Extensão de Comparação de Esquema
description: Saiba como instalar e usar a extensão de Comparação de Esquemas do Azure Data Studio para comparar facilmente dois bancos de dados e alterar seletivamente um para corresponder ao outro.
ms.custom: seodec18
ms.date: 11/04/2019
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 928c258dff70f861c33cc59125171a467eb12bf8
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88766215"
---
# <a name="schema-compare-extension"></a>Extensão de Comparação de Esquema
A extensão Comparação de Esquemas oferece uma experiência fácil de usar para comparar duas definições de banco de dados e aplicar as diferenças da origem no destino.


## <a name="features"></a>Recursos

* Comparar esquemas de dois arquivos ou bancos de dados DACPAC
* Exibir resultados como um conjunto de ações que devem ser executadas em relação ao destino para corresponderem à origem
* Excluir seletivamente ações listadas em resultados
* Definir opções que controlam o escopo da comparação
* Aplicar alterações no destino ou gerar um script com o mesmo efeito
* Salvar a comparação

![Comparação de Esquemas: Exemplo de comparação](media/extensions/schema-compare-extension/schema-compare.png)


## <a name="why-would-i-use-the-schema-compare-extension"></a>Por que usar a extensão Comparação de Esquemas?

Pode ser entediante gerenciar e sincronizar manualmente diferentes versões do banco de dados. A extensão Comparação de Esquemas simplifica o processo de comparar bancos de dados e oferece controle completo ao sincronizá-los &mdash; você pode filtrar seletivamente diferenças específicas e categorias de diferenças antes de aplicar as alterações. A extensão Comparação de Esquemas é uma ferramenta confiável que fará você economizar tempo e código.

![Comparação de Esquemas: Caixa de diálogo Opções](media/extensions/schema-compare-extension/schema-compare-options.png)


## <a name="install-the-extension"></a>Instalar a Extensão

1. Selecione o ícone de Extensões para exibir as extensões disponíveis.

    ![ícone do gerenciador de extensões](media/extensions/extension-manager-icon.png)

2. Pesquise a extensão **Comparação de Esquemas** e selecione-a para exibir seus detalhes. Clique em **Instalar** para adicionar a extensão.

3. Após a instalação, clique em **Recarregar** para habilitar a extensão no Azure Data Studio (necessário somente ao instalar uma extensão pela primeira vez).


## <a name="launch-a-schema-compare"></a>Iniciar uma Comparação de Esquemas

1. Para abrir a caixa de diálogo Comparação de Esquemas, **clique com o botão direito do mouse** em um banco de dados no Pesquisador de Objetos e clique em **Comparação de Esquemas**. O banco de dados selecionado será definido como o Banco de dados de origem na comparação.

    ![menu de inicialização de comparação de esquemas](media/extensions/schema-compare-extension/schema-compare-launch.png)


2. Selecione uma das reticências (...) para alterar a origem e o destino de sua Comparação de Esquemas e clique em OK.

    ![origem/destino de seleção da comparação de esquemas](media/extensions/schema-compare-extension/schema-compare-select-source-target.png)

3. Para personalizar sua comparação, clique no botão **Opções** na barra de ferramentas.

4. Clique em **Comparar** para exibir os resultados da comparação.


## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre a Comparação de Esquema, [confira nossa documentação](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md).
Informe problemas e solicite recursos [aqui](https://github.com/microsoft/azuredatastudio/issues).