---
description: Editar mapeamento de tipo (DB2ToSQL)
title: Editar mapeamento de tipo (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f93c4b7d-74fc-4856-bf42-035289918e83
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 3e31f1422415a14c4e1fb497ff56806feeb9439e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463528"
---
# <a name="edit-type-mapping-db2tosql"></a>Editar mapeamento de tipo (DB2ToSQL)
A caixa de diálogo **Editar mapeamento de tipo** permite especificar como os tipos são mapeados entre os objetos de banco de dados de origem e de destino.  
  
Você pode acessar essa caixa de diálogo em vários locais:  
  
-   Quando você seleciona um banco de dados de origem ou objeto de banco de dados, a guia **mapeamento de tipo** é exibida à direita do Gerenciador de metadados. Clique em **Adicionar** para adicionar um novo mapeamento de tipo ou clique em **Editar** para alterar um mapeamento de tipo existente.  
  
-   No menu **ferramentas** , selecione **configurações do projeto** ou **configurações padrão do projeto**. Na caixa de diálogo resultante, selecione **mapeamento de tipo**. Clique em **Adicionar** para adicionar um novo mapeamento de tipo ou clique em **Editar** para alterar um mapeamento de tipo existente.  
  
Os mapeamentos de tipo específicos de tabela substituem o banco de dados e os mapeamentos de tipo de projeto. Mapeamentos específicos de banco de dados substituem mapeamentos de projeto.  
  
## <a name="options"></a>Opções  
**Tipo de fonte**  
Selecione o tipo de dados de origem para mapear para um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo de dados.  
  
Se o tipo de dados for de comprimento variável, os campos a seguir aparecerão em **tipo de origem**:  
  
**De**  
Especifique o comprimento mínimo para esse mapeamento. Por exemplo, para o tipo de dados **nchar** , você pode inserir 10 para especificar que esse mapeamento é para um intervalo que começa em **nchar (10)**.  
  
**Para**  
Especifique o comprimento máximo para esse mapeamento. Por exemplo, para o tipo de dados **nchar** , você pode inserir 20 para especificar que esse mapeamento é para um intervalo que termina em **nchar (20)**.  
  
**Tipo de destino**  
Selecione o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo de dados para o qual o tipo de dados de origem está mapeado. Quando o SSMA cria a tabela ou o procedimento armazenado no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , o tipo de dados de origem será alterado para esse tipo de dados.  
  
Se o tipo de dados for de comprimento variável, o campo a seguir aparecerá em **tipo de destino**:  
  
**Replace with**  
Especifique o comprimento de destino para esse mapeamento. Por exemplo, para o tipo de dados **nvarchar** , você pode inserir 20 para especificar que o tipo de dados de origem especificado deve ser mapeado para **nvarchar (20)**.  
  
