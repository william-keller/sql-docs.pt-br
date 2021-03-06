---
description: sp_helpdevice (Transact-SQL)
title: sp_helpdevice (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdevice
- sp_helpdevice_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdevice
ms.assetid: 1a5eafa7-384e-4691-ba05-978eb73bbefb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0da4ef24647edd8de4bda1c412afb1410f9d3c14
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474106"
---
# <a name="sp_helpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Relata informações sobre dispositivos de backup do Microsoft® SQL Server™.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] É recomendável usar a exibição de catálogo [Sys. backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md) em vez disso  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_helpdevice [ [ @devname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumentos  
`[ @devname = ] 'name'` É o nome do dispositivo de backup para o qual as informações são relatadas. O valor de *Name* sempre é **sysname**.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou 1 (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Tipo de dados|Descrição|  
|-----------------|---------------|-----------------|  
|**device_name**|**sysname**|Nome do dispositivo lógico.|  
|**physical_name**|**nvarchar(260)**|Nome do arquivo físico.|  
|**descrição**|**nvarchar(255)**|A descrição do dispositivo.|  
|**status**|**int**|Um número que corresponde à descrição do status na coluna **Descrição** .|  
|**cntrltype**|**smallint**|Tipo de controlador do dispositivo:<br /><br /> 2 = Dispositivo de disco<br /><br /> 5 = Dispositivo de fita|  
|**size**|**int**|Tamanho do dispositivo em páginas de 2 KB.|  
  
## <a name="remarks"></a>Comentários  
 Se *nome* for especificado, **sp_helpdevice** exibirá informações sobre o dispositivo de despejo especificado. Se o *nome* não for especificado, **sp_helpdevice** exibirá informações sobre todos os dispositivos de despejo na exibição do catálogo **Sys. backup_devices** .  
  
 Os dispositivos de despejo são adicionados ao sistema usando **sp_addumpdevice**.  
  
## <a name="permissions"></a>Permissões  
 Requer associação à função **pública** .  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir relata informações sobre todos os dispositivos de despejo em uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_helpdevice;  
```  
  
## <a name="see-also"></a>Consulte Também  
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Mecanismo de Banco de Dados procedimentos armazenados &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
