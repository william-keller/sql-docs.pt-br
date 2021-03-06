---
description: sp_monitor (Transact-SQL)
title: sp_monitor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_monitor_TSQL
- sp_monitor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_monitor
ms.assetid: cb628496-2f9b-40e4-b018-d0831c4cb018
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6722a59873dcf672fe2c1b953931f44da4515a8e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446957"
---
# <a name="sp_monitor-transact-sql"></a>sp_monitor (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Exibe estatísticas sobre [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_monitor  
```  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 **0** (êxito) ou **1** (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Descrição|  
|-----------------|-----------------|  
|**last_run**|A hora **sp_monitor** foi executada pela última vez.|  
|**current_run**|A hora **sp_monitor** está sendo executada.|  
|**seg**|Número de segundos decorridos desde que **sp_monitor** foi executado.|  
|**cpu_busy**|Segundos durante os quais a CPU do computador servidor está executando o trabalho do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**io_busy**|Segundos durante os quais o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executou operações de entrada e saída.|  
|**ocioso**|Segundos durante os quais o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ficou inativo.|  
|**packets_received**|Número de leituras de pacotes de entrada feitas pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**packets_sent**|Número de pacotes de saída gravados pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**packet_errors**|Número de erros encontrados pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ao ler e gravar pacotes.|  
|**total_read**|Número de leituras feias pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**total_write**|Número de gravações feias pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**total_errors**|Número de erros encontrados pelo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durante a leitura e gravação.|  
|**conexões**|Número de logons ou tentativas de logon no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="remarks"></a>Comentários  
 O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controla, através de várias funções, a quantidade de trabalho realizada. Executar **sp_monitor** exibe os valores atuais retornados por essas funções e mostra quanto eles foram alterados desde a última vez em que o procedimento foi executado.  
  
 Para cada coluna, a estatística é impressa no *número*do formulário (*número*) –*número*% ou *número*(*número*). O primeiro *número* refere-se ao número de segundos (para **CPU_BUSY**, **IO_BUSY**e **ocioso**) ou ao número total (para as outras variáveis) desde que o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] foi reiniciado. O *número* entre parênteses refere-se ao número de segundos ou ao número total desde a última vez em que **sp_monitor** foi executado. A porcentagem é a porcentagem de tempo desde que **sp_monitor** foi executada pela última vez. Por exemplo, se o relatório mostrar **CPU_BUSY** como 4250 (215)-68%, a CPU estará ocupada em 4250 segundos desde que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] foi iniciada pela última vez, 215 segundos desde que **sp_monitor** foi executada pela última vez e 68% do tempo total desde que **sp_monitor** foi executado pela última vez.  
  
## <a name="permissions"></a>Permissões  
 Exige associação à função de servidor fixa **sysadmin** .  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir relata as informações sobre o quanto o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esteve ocupado.  
  
```console
USE master  
EXEC sp_monitor  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

```console
last_run       current_run                   seconds
-----------    --------------------------    ---------
Mar 29 1998    11:55AM Apr 4 1998 2:22 PM    561

cpu_busy           io_busy     idle
---------------    ---------   --------------
190(0)-0%          187(0)-0%   148(556)-99%

packets_received       packets_sent    packet_errors
----------------       ------------    -------------
16(1)                  20(2)           0(0)

total_read     total_write   total_errors    connections
-----------    -----------   -------------   -----------
141(0)         54920(127)    0(0)            4(0)
```
  
## <a name="see-also"></a>Consulte Também  
 [&#41;&#40;Transact-SQL de sp_who ](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
