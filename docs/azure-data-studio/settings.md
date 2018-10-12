---
title: Configurações de espaço de trabalho e usuário do Studio de dados do Azure | Microsoft Docs
description: Como modificar as configurações de espaço de trabalho e de usuário do Azure Data Studio.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: e446d117bd56cb0c3607eeaf40522800d82e8a7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2018
ms.locfileid: "48037699"
---
# <a name="user-and-workspace-settings"></a>Usuário e configurações de espaço de trabalho

É fácil configurar [!INCLUDE[name-sos](../includes/name-sos-short.md)] de sua preferência por meio das configurações. Quase todas as partes do [!INCLUDE[name-sos](../includes/name-sos-short.md)]do editor de interface do usuário e comportamento funcional tem opções você pode modificar.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] fornece dois escopos diferentes para as configurações:

* **Usuário** essas configurações se aplicam globalmente a qualquer instância do [!INCLUDE[name-sos](../includes/name-sos-short.md)] abrir.
* **Espaço de trabalho** configurações de espaço de trabalho são configurações específicas para uma pasta no seu computador e estão disponíveis somente quando a pasta é aberta na barra lateral do Explorer. As configurações definidas nesse escopo substituem o escopo do usuário.

## <a name="creating-user-and-workspace-settings"></a>Criação de usuário e configurações de espaço de trabalho

O comando de menu **arquivo** > **preferências** > **configurações** (**código**  >  **Preferências** > **configurações** em Mac) fornece o ponto de entrada para definir as configurações de usuário e o espaço de trabalho. Você receberá uma lista de configurações padrão. Copie qualquer configuração que você deseja alterar para apropriado `settings.json` arquivo. As guias à direita permitem que você alternar rapidamente entre os arquivos de configurações do usuário e o espaço de trabalho.

Você também pode abrir as configurações de usuário e o espaço de trabalho do **paleta de comandos** (**Ctrl + Shift + P**) com **preferências: abrir as configurações do usuário** e  **Preferências: Abrir configurações do espaço de trabalho** ou use o atalho de teclado (**Ctrl +,**).

O exemplo a seguir desabilita os números de linha no editor e configura as linhas de código a ser recuado automaticamente.

![Configurações de exemplo](media/settings/sample-settings.png)

As alterações nas configurações são recarregadas por [!INCLUDE[name-sos](../includes/name-sos-short.md)] após a modificação `settings.json` arquivo é salvo.

>**Observação:** configurações de espaço de trabalho são úteis para compartilhar configurações específicas do projeto em uma equipe.

## <a name="settings-file-locations"></a>Locais de arquivo de configurações

Dependendo de sua plataforma, o arquivo de configurações do usuário está localizado aqui:

* **Windows** `%APPDATA%\sqlops\User\settings.json`
* **Mac** `$HOME/Library/Application Support/sqlops/User/settings.json`
* **Linux** `$HOME/.config/sqlops/User/settings.json`

O arquivo de configuração do espaço de trabalho está localizado sob o `.[!INCLUDE[name-sos](../includes/name-sos-short.md)]` pasta em seu projeto.

## <a name="hot-exit"></a>Saída quente

O estúdio de dados do Azure lembra as alterações não salvas em arquivos quando você sai por padrão. Isso é o mesmo que o recurso hot sair no Visual Studio Code.

Por padrão, a saída hot está desativado. Habilitar saída hot editando o `files.hotExit` configuração. Para obter detalhes, consulte [Hot Exit (na documentação do Visual Studio Code)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).


## <a name="tab-color"></a>Cor da guia

Para simplificar a identificar quais conexões que você está trabalhando com guias abertas no editor podem ter suas cores definidas para corresponder a cor do grupo de servidores de conexão pertence. Por padrão, o guia de cores é desativados por padrão. Habilitar o guia de cores, editando o `sql.tabColorMode` configuração.

## <a name="additional-resources"></a>Recursos adicionais

Porque [!INCLUDE[name-sos](../includes/name-sos-short.md)] herda as configurações de usuário e o espaço de trabalho, a funcionalidade do Visual Studio Code, informações detalhadas sobre configurações está no [as configurações para o Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) artigo.