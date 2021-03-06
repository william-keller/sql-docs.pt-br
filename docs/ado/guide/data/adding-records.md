---
description: Adicionando registros a um conjunto de registros
title: Adicionando registros | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- editing data [ADO], AddNew method
- editing data [ADO], adding data
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
author: rothja
ms.author: jroth
ms.openlocfilehash: b833bc78a75d09c8f58ae12532f446ec94a097e0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991747"
---
# <a name="adding-records-to-a-recordset"></a>Adicionando registros a um conjunto de registros
Use o método **AddNew** para criar e inicializar um novo registro em um **conjunto de registros**existente. Você pode usar o método com **suporte** com um valor **CursorOptionEnum** de **adAddNew** para verificar se você pode adicionar registros ao objeto **Recordset** atual.

 Depois que você chamar o método **AddNew** , o novo registro se tornará o registro atual e permanecerá atualizado depois que você chamar o método **Update** . Se o objeto **Recordset** não oferecer suporte a indicadores, talvez você não consiga acessar o novo registro depois de mover para outro registro. Portanto, dependendo do tipo de cursor, talvez seja necessário chamar o método **Requery** para tornar o novo registro acessível.

 Se você chamar **AddNew** ao editar o registro atual ou ao adicionar um novo registro, o ADO chamará o método **Update** para salvar as alterações e, em seguida, criará o novo registro.

 Esta seção contém os seguintes tópicos.

-   [Adicionar registros usando AddNew](./adding-records-using-addnew.md)

-   [Adicionar vários campos](./adding-multiple-fields.md)

-   [Determinar o modo de edição](./determining-edit-mode.md)

-   [Usar AddNew em modos de lote e imediatos](./using-addnew-in-immediate-and-batch-modes.md)