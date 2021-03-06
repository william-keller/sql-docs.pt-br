---
description: DECRYPTBYPASSPHRASE (Transact-SQL)
title: DECRYPTBYPASSPHRASE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DECRYPTBYPASSPHRASE
- DECRYPTBYPASSPHRASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- decryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], DECRYPTBYPASSPHRASE function
- DECRYPTBYPASSPHRASE function
ms.assetid: ca34b5cd-07b3-4dca-b66a-ed8c6a826c95
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b183d118a9b09bd4bb35f122ae1c1986148fe9df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417392"
---
# <a name="decryptbypassphrase-transact-sql"></a>DECRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Essa função descriptografa os dados originalmente criptografados com uma frase secreta.  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Ícone de link do tópico") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```syntaxsql
  
DecryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumentos
 *passphrase*  
A frase secreta usada para gerar a chave de descriptografia.  
  
 @passphrase  
Uma variável do tipo **char**, **nchar**, **nvarchar**ou **varchar** que contém a frase secreta usada para gerar a chave de descriptografia.  
  
'*ciphertext*'  
A cadeia de caracteres de dados criptografados com a chave. *ciphertext* tem um tipo de dados **varbinary**.  
 
@ciphertext  
Uma variável do tipo **varbinary** que contém dados criptografados com a chave. A variável *\@ciphertext* tem um tamanho máximo de 8.000 bytes.  
  
*add_authenticator*  
Indica se o processo de criptografia original incluía, e criptografava, um autenticador junto com o texto não criptografado. *add_authenticator* teria um valor de 1, se o processo de criptografia usasse um autenticador. *add_authenticator* tem um tipo de dados **int**.  
  
@add_authenticator  
Uma variável que indica se o processo de criptografia original incluía, e criptografava, um autenticador junto com o texto não criptografado. *\@add_authenticator* teria um valor de 1, se o processo de criptografia usasse um autenticador. *\@add_authenticator* tem um tipo de dados **int**.  

*authenticator*  
Os dados usados como base para a geração do autenticador. *authenticator* tem um tipo de dados **sysname**.  
  
@authenticator  
Uma variável contendo dados usados como a base para a geração dos autenticadores. *\@authenticator* tem um tipo de dados **sysname**.  
  
## <a name="return-types"></a>Tipos de retorno  
**varbinary**, com um tamanho máximo de 8.000 bytes.  
  
## <a name="remarks"></a>Comentários  
`DECRYPTBYPASSPHRASE` não requer nenhuma permissão para sua execução. `DECRYPTBYPASSPHRASE` retorna NULL se recebe a frase secreta errada ou as informações do autenticador erradas.  
  
`DECRYPTBYPASSPHRASE` usa a frase secreta para gerar uma chave de descriptografia. Essa chave de descriptografia não será mantida.  
  
Se um autenticador tiver sido incluído no momento da criptografia de texto cifrado, `DECRYPTBYPASSPHRASE` precisará receber esse mesmo autenticador para o processo de descriptografia. Se o valor do autenticador fornecido para o processo de descriptografia não corresponder ao valor do autenticador originalmente usado para criptografar os dados, a operação `DECRYPTBYPASSPHRASE` falhará.  
  
## <a name="examples"></a>Exemplos  
Este exemplo descriptografa o registro atualizado em [EncryptByPassPhrase](../../t-sql/functions/encryptbypassphrase-transact-sql.md).  
  
```  
USE AdventureWorks2012;  
-- Get the passphrase from the user.  
DECLARE @PassphraseEnteredByUser nvarchar(128);  
SET @PassphraseEnteredByUser   
= 'A little learning is a dangerous thing!';  
  
-- Decrypt the encrypted record.  
SELECT CardNumber, CardNumber_EncryptedbyPassphrase   
    AS 'Encrypted card number', CONVERT(varchar,  
    DecryptByPassphrase(@PassphraseEnteredByUser, CardNumber_EncryptedbyPassphrase, 1   
    , CONVERT(varbinary, CreditCardID)))  
    AS 'Decrypted card number' FROM Sales.CreditCard   
    WHERE CreditCardID = '3681';  
GO  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Escolher um algoritmo de criptografia](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
  
  
