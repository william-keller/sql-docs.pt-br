---
description: Opções de linha de comando no console do SSMA (DB2ToSQL)
title: Opções de linha de comando no console do SSMA (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 237354e9-25c4-4386-9d1f-ca0618d4a9a0
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 5dde1168e8107f01f06d5e60fb2b1853d47abc43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472519"
---
# <a name="command-line-options-in-ssma-console-db2tosql"></a>Opções de linha de comando no console do SSMA (DB2ToSQL)
A Microsoft fornece uma série robusta de opções de linha de comando para executar e controlar as atividades do SSMA. As seções que mais profundos detalham o mesmo.  
  
## <a name="command-line-options-in-ssma-console"></a>Opções de linha de comando no Console do SSMA  
Aqui descritos estão as opções de comando do console.  
  
Para fins desta seção, o termo ' Option ' também é conhecido como ' switch '.  
  
As opções não diferenciam maiúsculas de minúsculas e podem começar com o **-** caractere ' ' ou, ' **/** '.  
  
Se as opções forem especificadas, será obrigatório especificar os parâmetros de opção correspondentes.  
  
Os parâmetros de opção devem ser separados do caractere de opção por espaço em branco.  
  
**Exemplos de sintaxe:**  
  
`C:\> SSMAforDB2Console.EXE -s scriptfile`  
  
`C:\> SSMAforDB2Console.EXE -s "C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \AssessmentReportGenerationSample.xml" -v "C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \VariableValueFileSample.xml" -c "C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ServersConnectionFileSample.xml"`  
  
Nomes de pastas ou arquivos contendo espaços devem ser especificados entre aspas duplas.  
  
A saída de entradas de linha de comando e mensagens de erro são armazenadas em STDOUT ou em um arquivo especificado.  
  
### <a name="script-file-option--sscript"></a>Opção de arquivo de script:-s/script  
Uma opção obrigatória, o caminho/nome do arquivo de script especifica o script de sequências de comando a ser executado pelo SSMA.  
  
**Exemplos de sintaxe:**  
  
`C:\>SSMAforDB2Console.EXE -s "C Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"`  
  
### <a name="variable-value-file-option--vvariable"></a>Opção de arquivo de valor de variável:-v/Variable  
Esse arquivo consiste em variáveis usadas no arquivo de script. Esse é um comutador opcional. Se as variáveis não forem declaradas no arquivo de variável e usadas no arquivo de script, o aplicativo gerará um erro e encerrará a execução do console.  
  
**Exemplos de sintaxe:**  
  
-   Variáveis definidas em vários arquivos de valor de variável, talvez um com um valor padrão e outro com um valor específico de instância quando aplicável. O último arquivo de variável especificado nos argumentos de linha de comando assume a preferência, caso haja uma duplicação de variáveis:  
  
    `C:\>SSMAforDB2Console.EXE -s`  
  
    `"C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml" -v c:\migration`  
  
    `projects\global_variablevaluefile.xml -v "c:\migrationprojects\instance_variablevaluefile.xml"`  
  
### <a name="server-connection-file-option--cserverconnection"></a>Opção de arquivo de conexão do servidor:-c/ServerConnection  
Esse arquivo contém informações de conexão de servidor para cada servidor. Cada definição de servidor é identificada por uma ID de servidor exclusiva. As IDs de servidor são referenciadas no arquivo de script para comandos relacionados à conexão.  
  
A definição do servidor pode fazer parte do arquivo de conexão do servidor e/ou do arquivo de script. A ID do servidor no arquivo de script tem precedência sobre o arquivo de conexão do servidor, caso haja uma duplicação da ID do servidor.  
  
**Exemplos de sintaxe:**  
  
-   As IDs de servidor são usadas no arquivo de script e são definidas em um arquivo de conexão de servidor separado, o arquivo de conexão do servidor usa variáveis que são definidas no arquivo de valor da variável:  
  
    `C:\>SSMAforDB2Console.EXE -s "C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -v`  
  
    `c:\SsmaProjects\myvaluefile1.xml -c`  
  
    `c:\SsmaProjects\myserverconnectionsfile1.xml`  
  
-   A definição do servidor é inserida no arquivo de script:  
  
    `C:\>SSMAforDB2Console.EXE -s "C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"`  
  
### <a name="xml-output-option--xxmloutput-xmloutputfile"></a>Opção de saída XML:-x/xmlsaídas [xmlarquivo_de_saídafile]  
Esse comando é usado para gerar mensagens de saída de comando em um formato XML para o console do ou para um arquivo XML.  
  
Há duas opções disponíveis para xmloutput, aula sobre visualização..,:  
  
-   Se o caminho de arquivo for fornecido após a opção xmloutput, a saída será redirecionada para o File.  
  
    **Exemplo de sintaxe:**  
  
    `C:\>SSMAforDB2Console.EXE -s`  
  
    `"C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -x d:\xmloutput\project1output.xml`  
  
-   Se nenhum FilePath for fornecido após a opção xmloutput, o xmlout será exibido no próprio console.  
  
    **Exemplo de sintaxe:**  
  
    `C:\>SSMAforDB2Console.EXE -s "C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -xmloutput`  
  
### <a name="log-file-option--llog"></a>Opção de arquivo de log:-l/log  
Todas as operações do SSMA no aplicativo de console são registradas em um arquivo de log. Esse é um comutador opcional. Se um arquivo de log e seu caminho forem especificados na linha de comando, o log será gerado no local especificado. Caso contrário, ele será gerado em seu local padrão.  
  
**Exemplo de sintaxe:**  
  
`C:\>SSMAforDB2Console.EXE`  
  
`"C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -l c:\SsmaProjects\migration1.log`  
  
### <a name="project-environment-folder-option--eprojectenvironment"></a>Opção de pasta de ambiente do projeto:-e/projectenvironment  
Isso denota a pasta de configurações de ambiente do projeto para o projeto do SSMA atual. Essa opção é opcional.  
  
**Exemplo de sintaxe:**  
  
`C:\>SSMAforDB2Console.EXE -s`  
  
`"C:\ Program Files\Microsoft SQL Server Migration Assistant for DB2\Sample Console Scripts \ConversionAndDataMigrationSample.xml"  -e c:\SsmaProjects\CommonEnvironment`  
  
### <a name="secure-password-option--psecurepassword"></a>Opção de senha segura:-p/SecurePassword  
Essa opção indica a senha criptografada para conexões do servidor. Ele difere de todas as outras opções: a opção não executa nenhum script nem ajuda em nenhuma atividade relacionada à migração, mas ajuda a gerenciar a criptografia de senha para as conexões de servidor usadas no projeto de migração.  
  
Você não pode inserir nenhuma outra opção ou senha como parâmetro de linha de comando. Caso contrário, resultará em um erro. Para obter mais informações, consulte a seção [Gerenciando senhas](https://msdn.microsoft.com/56d546e3-8747-4169-aace-693302667e94) .  
  
As seguintes subopções têm suporte para `-p/securepassword` :  
  
-   Para adicionar a senha ao armazenamento protegido para uma ID de servidor especificada ou para todas as IDs de servidor definidas no arquivo de conexão do servidor. A opção-overwrite, abaixo, atualiza a senha se ela já existir:  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}` `-c|-serverconnection <server-connection-file> [-v|variable <variable-value-file>]``[-o|overwrite]`  
  
    `-p|-securepassword -a|add    {"<server_id>[, .n]"|all}``-s|-script <server-connection-file> [-v|variable <variable-value-file>] [-o|overwrite]`  
  
-   Para remover a senha criptografada do armazenamento protegido da ID de servidor especificada ou para todas as IDs de servidor:  
  
    `-p/securepassword -r/remove {<server_id> [, ...n] | all}`  
  
-   Para exibir uma lista de IDs de servidor para as quais a senha é criptografada:  
  
    `-p/securepassword -l/list`  
  
-   Para exportar as senhas armazenadas no armazenamento protegido para um arquivo criptografado. Esse arquivo é criptografado com a frase secreta especificada pelo usuário.  
  
    `-p/securepassword -e/export {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
-   O arquivo criptografado que foi exportado anteriormente é importado para o armazenamento protegido local usando a frase secreta especificada pelo usuário. Depois que o arquivo é descriptografado, ele é armazenado em um novo arquivo que, por sua vez, é criptografado no computador local.  
  
    `-p/securepassword -i/import {<server-id> [, ...n] | all} <encrypted-password -file>`  
  
    Várias IDs de servidor podem ser especificadas usando separadores de vírgulas.  
  
### <a name="help-option--help"></a>Opção de ajuda:-?/help  
Exibe o resumo da sintaxe das opções do console do SSMA:  
  
`C:\>SSMAforDB2Console.EXE -?`  
  
Para ver uma exibição tabular das opções de linha de comando do console do SSMA, consulte o [Apêndice-1 &#40;DB2ToSQL&#41;](../../ssma/db2/appendix-1-db2tosql.md).  
  
### <a name="securepassword-help-option--securepassword--help"></a>Opção de ajuda do SecurePassword:-SecurePassword-?/Help  
Exibe o resumo da sintaxe das opções do console do SSMA:  
  
`C:\>SSMAforDB2Console.EXE -securepassword -?`  
  
Para ver uma exibição tabular das opções de linha de comando do console do SSMA, consulte o [Apêndice-1 &#40;DB2ToSQL&#41;](../../ssma/db2/appendix-1-db2tosql.md)  
  
### <a name="next-step"></a>Próxima etapa  
A próxima etapa depende dos requisitos do seu projeto:  
  
1.  Para especificar uma senha ou exportar/importar senhas, consulte [Gerenciando senhas &#40;DB2ToSQL&#41;](../../ssma/db2/managing-passwords-db2tosql.md).  
  
2.  Para gerar relatórios, consulte [gerando relatórios &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md).  
  
3.  Para solucionar problemas no console do, consulte solução de problemas [&#40;DB2ToSQL&#41;](../../ssma/db2/troubleshooting-db2tosql.md).  
  
