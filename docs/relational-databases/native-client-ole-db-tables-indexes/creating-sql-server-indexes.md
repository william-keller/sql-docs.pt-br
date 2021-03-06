---
description: Criar índices de SQL Server (provedor de OLE DB de cliente nativo)
title: Criar índices de SQL Server (provedor de OLE DB de cliente nativo) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4850e0de477378b403c5443dc9dcd3ecf952321d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448250"
---
# <a name="creating-sql-server-native-client-indexes"></a>Criando índices de SQL Server Native Client
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo expõe a função **IIndexDefinition:: CreateIndex** , permitindo que os consumidores definam novos índices em [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabelas.  
  
 O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo cria índices de tabela como índices ou restrições. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] concede privilégios para criação de restrições ao proprietário da tabela, ao proprietário do banco de dados e aos membros de determinadas funções administrativas. Por padrão, apenas o proprietário da tabela pode criar um índice em uma tabela. Portanto, o êxito ou a falha de **CreateIndex** depende não apenas dos direitos de acesso do usuário do aplicativo, mas também do tipo de índice criado.  
  
 Os consumidores especificam o nome da tabela como uma cadeia de caracteres Unicode no membro *pwszName* da união *uName* no parâmetro *pTableID*. O membro *eKind* de *pTableID* precisa ser DBKIND_NAME.  
  
 O parâmetro *pIndexID* pode ser nulo e, se for, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo criará um nome exclusivo para o índice. O consumidor pode capturar o nome do índice especificando um ponteiro válido para um DBID no parâmetro *ppIndexID*.  
  
 O consumidor pode especificar o nome do índice como uma cadeia de caracteres Unicode no membro *pwszName* da união *uName* do parâmetro *pIndexID*. O membro *eKind* de *pIndexID* precisa ser DBKIND_NAME.  
  
 O consumidor especifica a coluna ou as colunas que participam do índice por nome. Para cada estrutura DBINDEXCOLUMNDESC usada em **CreateIndex**, o membro *eKind* da *pColumnID* precisa ser DBKIND_NAME. O nome da coluna é especificado como uma cadeia de caracteres Unicode no membro *pwszName* da união *uName* no *pColumnID*.  
  
 O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oferece suporte a ordem crescente em valores no índice. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo retorna E_INVALIDARG se o consumidor especifica DBINDEX_COL_ORDER_DESC em qualquer estrutura DBINDEXCOLUMNDESC.  
  
 **CreateIndex** interpreta as propriedades de índice, conforme mostrado a seguir.  
  
|ID da propriedade|Descrição|  
|-----------------|-----------------|  
|DBPROP_INDEX_AUTOUPDATE|L/G: Leitura/gravação<br /><br /> Padrão: Nenhum<br /><br /> Descrição: o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo não oferece suporte a essa propriedade. As tentativas de definir a propriedade em **CreateIndex** geram um valor retornado DB_S_ERRORSOCCURRED. O membro *dwStatus* da estrutura de propriedade indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_CLUSTERED|L/G: Leitura/gravação<br /><br /> Padrão: VARIANT_FALSE<br /><br /> Descrição: controla o clustering de índice.<br /><br /> VARIANT_TRUE: o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo tenta criar um índice clusterizado na [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabela. O [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oferece suporte a no máximo um índice clusterizado em qualquer tabela.<br /><br /> VARIANT_FALSE: o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo tenta criar um índice não clusterizado na [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabela.|  
|DBPROP_INDEX_FILLFACTOR|L/G: Leitura/gravação<br /><br /> Padrão: 0<br /><br /> Descrição: especifica o percentual de uma página de índice usada para armazenamento. Para obter mais informações, confira [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md).<br /><br /> O tipo da variante é VT_I4. O valor deve ser maior ou igual a 1 e menor ou igual a 100.|  
|DBPROP_INDEX_INITIALIZE|L/G: Leitura/gravação<br /><br /> Padrão: Nenhum<br /><br /> Descrição: o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo não oferece suporte a essa propriedade. As tentativas de definir a propriedade em **CreateIndex** geram um valor retornado DB_S_ERRORSOCCURRED. O membro *dwStatus* da estrutura de propriedade indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLCOLLATION|L/G: Leitura/gravação<br /><br /> Padrão: Nenhum<br /><br /> Descrição: o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo não oferece suporte a essa propriedade. As tentativas de definir a propriedade em **CreateIndex** geram um valor retornado DB_S_ERRORSOCCURRED. O membro *dwStatus* da estrutura de propriedade indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_NULLS|L/G: Leitura/gravação<br /><br /> Padrão: Nenhum<br /><br /> Descrição: o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo não oferece suporte a essa propriedade. As tentativas de definir a propriedade em **CreateIndex** geram um valor retornado DB_S_ERRORSOCCURRED. O membro *dwStatus* da estrutura de propriedade indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_PRIMARYKEY|L/G: Leitura/gravação<br /><br /> Padrão: Descrição de VARIANT_FALSE: cria o índice como uma integridade referencial, restrição PRIMARY KEY.<br /><br /> VARIANT_TRUE: o índice é criado para dar suporte à restrição PRIMARY KEY da tabela. As colunas devem ser não nulas.<br /><br /> VARIANT_FALSE: o índice não é usado como uma restrição PRIMARY KEY para valores de linha na tabela.|  
|DBPROP_INDEX_SORTBOOKMARKS|L/G: Leitura/gravação<br /><br /> Padrão: Nenhum<br /><br /> Descrição: o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo não oferece suporte a essa propriedade. As tentativas de definir a propriedade em **CreateIndex** geram um valor retornado DB_S_ERRORSOCCURRED. O membro *dwStatus* da estrutura de propriedade indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TEMPINDEX|L/G: Leitura/gravação<br /><br /> Padrão: Nenhum<br /><br /> Descrição: o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo não oferece suporte a essa propriedade. As tentativas de definir a propriedade em **CreateIndex** geram um valor retornado DB_S_ERRORSOCCURRED. O membro *dwStatus* da estrutura de propriedade indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_TYPE|L/G: Leitura/gravação<br /><br /> Padrão: Nenhum<br /><br /> Descrição: o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo não oferece suporte a essa propriedade. As tentativas de definir a propriedade em **CreateIndex** geram um valor retornado DB_S_ERRORSOCCURRED. O membro *dwStatus* da estrutura de propriedade indica DBPROPSTATUS_BADVALUE.|  
|DBPROP_INDEX_UNIQUE|L/G: Leitura/gravação<br /><br /> Padrão: VARIANT_FALSE<br /><br /> Descrição: cria o índice como uma restrição UNIQUE na coluna ou nas colunas participantes.<br /><br /> VARIANT_TRUE: o índice é usado para restringir valores de linha de maneira exclusiva na tabela.<br /><br /> VARIANT_FALSE: o índice não restringe valores de linha de maneira exclusiva.|  
  
 No conjunto de propriedades específico do provedor DBPROPSET_SQLSERVERINDEX, o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provedor de OLE DB de cliente nativo define a propriedade de informações da fonte de dados a seguir.  
  
|ID da propriedade|Descrição|  
|-----------------|-----------------|  
|SSPROP_INDEX_XML|Tipo: VT_BOOL (leitura/gravação)<br /><br /> Padrão: VARIANT_FALSE<br /><br /> Descrição: quando essa propriedade é especificada com um valor VARIANT_TRUE com IIndexDefinition::CreateIndex, ela resulta na criação de um índice xml principal correspondente à coluna que está sendo indexada. Se essa propriedade for VARIANT_TRUE, cIndexColumnDescs deverá ser 1, caso contrário, será um erro.|  
  
 Este exemplo cria um índice de chave primária:  
  
```  
// This CREATE TABLE statement shows the referential integrity and   
// PRIMARY KEY constraint on the OrderDetails table that will be created   
// by the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//        CONSTRAINT PK_OrderDetails  
//        PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
HRESULT CreatePrimaryKey  
    (  
    IIndexDefinition* pIIndexDefinition  
    )  
    {  
    HRESULT             hr = S_OK;  
  
    DBID                dbidTable;  
    DBID                dbidIndex;  
    const ULONG         nCols = 2;  
    ULONG               nCol;  
    const ULONG         nProps = 2;  
    ULONG               nProp;  
  
    DBINDEXCOLUMNDESC   dbidxcoldesc[nCols];  
    DBPROP              dbpropIndex[nProps];  
    DBPROPSET           dbpropset;  
  
    DBID*               pdbidIndexOut = NULL;  
  
    // Set up identifiers for the table and index.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    dbidIndex.eKind = DBKIND_NAME;  
    dbidIndex.uName.pwszName = L"PK_OrderDetails";  
  
    // Set up column identifiers.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbidxcoldesc[nCol].pColumnID = new DBID;  
        dbidxcoldesc[nCol].pColumnID->eKind = DBKIND_NAME;  
  
        dbidxcoldesc[nCol].eIndexColOrder = DBINDEX_COL_ORDER_ASC;  
        }  
    dbidxcoldesc[0].pColumnID->uName.pwszName = L"OrderID";  
    dbidxcoldesc[1].pColumnID->uName.pwszName = L"ProductID";  
  
    // Set properties for the index. The index is clustered,  
    // PRIMARY KEY.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        dbpropIndex[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        dbpropIndex[nProp].colid = DB_NULLID;  
  
        VariantInit(&(dbpropIndex[nProp].vValue));  
  
        dbpropIndex[nProp].vValue.vt = VT_BOOL;  
        }  
    dbpropIndex[0].dwPropertyID = DBPROP_INDEX_CLUSTERED;  
    dbpropIndex[0].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropIndex[1].dwPropertyID = DBPROP_INDEX_PRIMARYKEY;  
    dbpropIndex[1].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropset.rgProperties = dbpropIndex;  
    dbpropset.cProperties = nProps;  
    dbpropset.guidPropertySet = DBPROPSET_INDEX;  
  
    hr = pIIndexDefinition->CreateIndex(&dbidTable, &dbidIndex, nCols,  
        dbidxcoldesc, 1, &dbpropset, &pdbidIndexOut);  
  
    // Clean up dynamically allocated DBIDs.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        delete dbidxcoldesc[nCol].pColumnID;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Tabelas e índices](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
