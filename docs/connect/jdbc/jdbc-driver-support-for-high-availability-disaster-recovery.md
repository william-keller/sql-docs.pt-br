---
title: Suporte a JDBC Driver para alta disponibilidade e recuperação de desastre
description: Este tópico discute o suporte do Microsoft JDBC Driver for SQL Server para alta disponibilidade, recuperação de desastre (Grupos de Disponibilidade AlwaysOn).
ms.custom: ''
ms.date: 07/13/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e3a79f3f47db8bfa048ecb5b910bcb4946cf7a7c
ms.sourcegitcommit: e08d28530e0ee93c78a4eaaee8800fd687babfcc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301815"
---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>Suporte a JDBC Driver para alta disponibilidade e recuperação de desastre

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Este tópico aborda o suporte do [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] para alta disponibilidade, recuperação de desastre – [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]. Para obter mais informações sobre o [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], consulte os Manuais Online do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] .  
  
 Com a versão 4.0 do [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], é possível especificar o ouvinte do grupo de disponibilidade de um AG (grupo de disponibilidade) (alta disponibilidade, recuperação de desastre) na propriedade de conexão. Se um aplicativo [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] estiver conectado a um banco de dados Always On que efetua failover, a conexão original será interrompida, e o aplicativo deverá abrir uma nova conexão para continuar o trabalho após o failover. As seguintes [propriedades de conexão foram](setting-the-connection-properties.md) adicionadas ao [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]:  
  
- **multiSubnetFailover**  
  
- **applicationIntent**

Especifique multiSubnetFailover=true ao se conectar ao ouvinte do grupo de disponibilidade de um grupo de disponibilidade ou uma instância de cluster de failover. Observe que **multiSubnetFailover** é false por padrão. Use **applicationIntent** para declarar o tipo de carga de trabalho do aplicativo. Confira as seções abaixo para mais detalhes.

A partir da versão 6.0 do Microsoft JDBC Driver for SQL Server, uma nova propriedade de conexão TNIR (**transparentNetworkIPResolution**) foi adicionada à conexão transparente com grupos de disponibilidade Always On ou a um servidor que tem vários endereços IP associados. Quando **transparentNetworkIPResolution** for true, o driver tentará se conectar ao primeiro endereço IP disponível. Se a primeira tentativa falhar, o driver tentará se conectar a todos os endereços IP em paralelo até que o tempo limite expire, descartando todas as tentativas de conexão pendentes quando uma delas for bem-sucedida.

Observe que:

- transparentNetworkIPResolution é true por padrão
- transparentNetworkIPResolution será ignorada se multiSubnetFailover for true  
- transparentNetworkIPResolution será ignorada se o espelhamento de banco de dados for usado  
- transparentNetworkIPResolution será ignorada se houver mais de 64 endereços IP  
- Quando transparentNetworkIPResolution for true, a primeira tentativa de conexão usará 500 ms como o tempo limite. O restante das tentativas de conexão seguirá a mesma lógica do recurso multiSubnetFailover.  

> [!NOTE]
> Se você estiver usando o Microsoft JDBC Driver 4.2 (ou anterior) para SQL Server e se **multiSubnetFailover** for false, o [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] tentará se conectar ao primeiro endereço IP. Se o [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] não puder estabelecer uma conexão com o primeiro endereço IP, a conexão apresentará falha. O [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] não tentará se conectar a nenhum endereço IP subsequente associado ao servidor.

> [!NOTE]
> O aumento do tempo limite de conexão e a implementação de lógica de repetição de conexão aumentarão a probabilidade de um aplicativo se conectar a um grupo de disponibilidade. Além disso, como uma conexão pode falhar devido a um failover de grupo de disponibilidade, você deve implementar lógica de repetição de conexão, repetindo uma conexão com falha até se reconectar.  

## <a name="connecting-with-multisubnetfailover"></a>Conectando-se a multiSubnetFailover  

 Sempre especifique **multiSubnetFailover=True** ao se conectar ao ouvinte de um grupo de disponibilidade do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ou a uma instância de cluster de failover do [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. **multiSubnetFailover** permite o failover mais rápido para todos os Grupos de Disponibilidade e instâncias de cluster de failover no [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e reduzirá significativamente o tempo de failover para topologias AlwaysOn de uma ou várias sub-redes. Durante um failover de várias sub-redes, o cliente tentará conexões em paralelo. Durante um failover de sub-rede, o [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] repetirá agressivamente a conexão TCP.  
  
 A propriedade de conexão **multiSubnetFailover** indica que o aplicativo está sendo implantado em um grupo de disponibilidade ou instância de cluster de failover e que o [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] tentará se conectar ao banco de dados na instância primária do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tentando se conectar a todos os endereços IP do grupo de disponibilidade. Quando **MultiSubnetFailover=true** é especificado para uma conexão, o cliente repete as tentativas de conexão TCP mais rapidamente do que os intervalos de retransmissão TCP padrão do sistema operacional. Esse comportamento permite uma reconexão mais rápida depois do failover de um Grupo de Disponibilidade AlwaysOn ou uma Instância de Cluster de Failover AlwaysOn e é aplicável a Grupos de Disponibilidade e Instâncias de Cluster de Failover com uma ou várias sub-redes.  
  
 Para obter mais informações sobre palavras-chave de cadeia de conexão no [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], confira [Configuração das propriedades de conexão](setting-the-connection-properties.md).  
  
 A especificação de **multiSubnetFailover=true** durante a conexão a algo que não seja um ouvinte de grupo de disponibilidade ou uma Instância de Cluster de Failover pode resultar em um impacto de desempenho negativo e isso não é compatível.  
  
 Se o gerenciador de segurança não for instalado, a Máquina Virtual Java armazenará VIPs (endereços IP virtuais) em cache por um período determinado, por padrão, definido pela implementação JDK e as propriedades Java networkaddress.cache.ttl e networkaddress.cache.negative.ttl. Se o gerenciador de segurança JDK for instalado, a Máquina Virtual Java armazenará VIPs em cache e não atualizará o cache, por padrão. Você deve definir a "vida útil" (networkaddress.cache.ttl) para um dia no cache da Máquina Virtual Java. Se você não alterar o valor padrão para um dia (ou valor parecido), o valor antigo não será limpo no cache da Máquina Virtual Java quando um VIP for adicionado ou atualizado. Para obter mais informações sobre networkaddress.cache.ttl e networkaddress.cache.negative.ttl, confira [https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html](https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html).  
  
 Use as diretrizes a seguir para conectar-se a um servidor em um grupo de disponibilidade ou Instância de Cluster de Failover:  
  
- O driver gerará um erro se a propriedade de conexão **instanceName** for usada na mesma cadeia de conexão da propriedade de conexão **multiSubnetFailover**. Esse erro acontece porque o SQL Browser não é usado em um grupo de disponibilidade. No entanto, se a propriedade de conexão **portNumber** também for especificada, o driver ignorará **instanceName** e usará **portNumber**.  
  
- Use a propriedade de conexão **multiSubnetFailover** quando estiver se conectando a uma ou várias sub-redes, isso melhorará o desempenho em ambos os casos.  
  
- Para conectar-se a um grupo de disponibilidade, especifique o ouvinte do grupo de disponibilidade como o servidor em sua cadeia de conexão. Por exemplo, jdbc:sqlserver://VNN1.  
  
- Conectar-se a uma instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configurada com mais de 64 endereços IP causará uma falha de conexão.  
  
- O comportamento de um aplicativo que usa a propriedade de conexão do **multiSubnetFailover** não é afetado com base no tipo de autenticação: Autenticação [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Autenticação Kerberos ou Autenticação do Windows.  
  
- Aumente o valor de **loginTimeout** para acomodar o tempo de failover e reduzir as tentativas de repetição de conexão do aplicativo.  
  
- Não há suporte para transações distribuídas.  
  
Se o roteamento somente leitura não estiver em ação, conectar-se a um local de réplica secundária em um grupo de disponibilidade apresentará falha nas seguintes situações:  
  
1. Se o local de réplica secundário não for configurado para aceitar conexões.  
  
2. Se um aplicativo usar **applicationIntent=ReadWrite** (discutido abaixo) e o local de réplica secundária estiver configurado para acesso somente leitura.  
  
Uma conexão falhará se uma réplica primária for configurada para rejeitar cargas de trabalho somente leitura e a cadeia de conexão contiver **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Atualizando para usar clusters de várias sub-redes a partir do espelhamento de banco de dados  

Se você atualizar um aplicativo [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] que atualmente usa o espelhamento de banco de dados em um cenário de várias sub-redes, deverá remover a propriedade de conexão **failoverPartner** e substituí-la por **multiSubnetFailover** definido como **true** e substituir o nome do servidor da cadeia de conexão por um ouvinte de grupo de disponibilidade. Se uma cadeia de conexão usa **failoverPartner** e **multiSubnetFailover=true**, o driver gerará um erro. No entanto, se uma cadeia de conexão usar **failoverPartner** e **multiSubnetFailover=false** (ou **ApplicationIntent=ReadWrite**), o aplicativo usará o espelhamento de banco de dados.  
  
O driver retornará um erro se o espelhamento de banco de dados for usado no banco de dados primário no AG e se **multiSubnetFailover=true** for usado na cadeia de conexão que se conecta a um banco de dados primário, em vez de ao ouvinte do grupo de disponibilidade.  

[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]

## <a name="connection-pooling"></a>Pool de conexões

Ao usar o JDBC Driver da Microsoft para SQL Server em conjunto com uma biblioteca de pooling de conexão, considere os seguintes pontos:

- Se você tiver um roteamento somente leitura configurado e um pool de servidores somente leitura para o qual deseja distribuir a carga, o pooling de conexão reduzirá o número de oportunidades para que novas conexões se espalhem pelos servidores de destino.
- Para evitar uma carga maior em qualquer servidor individual em um pool, escolha opções de pool que incentivem uma distribuição uniforme das conexões por todo o pool.
- Verifique se o pool de conexões está configurado com um tempo de vida de conexão. Caso uma réplica somente leitura não esteja disponível quando uma conexão somente leitura for feita, a configuração deverá garantir que a conexão, eventualmente, seja fechada e restabelecida com uma réplica somente leitura quando uma estiver disponível novamente.

## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>Novos métodos com suporte para multiSubnetFailover e applicationIntent  

Os seguintes métodos fornecem acesso programático às palavras-chave de cadeia de conexão **multiSubnetFailover**, **applicationIntent** e **transparentNetworkIPResolution**:  
  
- [SQLServerDataSource.getApplicationIntent](reference/getapplicationintent-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.setApplicationIntent](reference/setapplicationintent-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.getMultiSubnetFailover](reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.setMultiSubnetFailover](reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
- [SQLServerDriver.getPropertyInfo](reference/getpropertyinfo-method-sqlserverdriver.md)  

- SQLServerDataSource.setTransparentNetworkIPResolution

- SQLServerDataSource.getTransparentNetworkIPResolution
  
Os métodos **getMultiSubnetFailover**, **setMultiSubnetFailover**, **getApplicationIntent**, **setApplicationIntent**, **getTransparentNetworkIPResolution** e **setTransparentNetworkIPResolution** também são adicionados às classes [SQLServerDataSource](reference/sqlserverdatasource-class.md), [SQLServerConnectionPoolDataSource](reference/sqlserverconnectionpooldatasource-class.md) e [SQLServerXADataSource](reference/sqlserverxadatasource-class.md).  
  
## <a name="tlsssl-certificate-validation"></a>Validação do certificado TLS/SSL  

Um grupo de disponibilidade consiste em vários servidores físicos. O [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] adicionou suporte ao **Nome Alternativo da Entidade** aos certificados TLS/SSL para que vários hosts possam ser associados ao mesmo certificado. Para obter mais informações sobre o TLS, confira [Noções básicas do suporte à criptografia](understanding-ssl-support.md).  
  
## <a name="see-also"></a>Confira também  

[Conectando ao SQL Server com o JDBC Driver](connecting-to-sql-server-with-the-jdbc-driver.md)  
[Configuração das propriedades de conexão](setting-the-connection-properties.md)  
