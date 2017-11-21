---
title: "Globální funkce identifikátor zabezpečení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlsecurity/ATL::Sids::AccountOps
- atlsecurity/ATL::Sids::Admins
- atlsecurity/ATL::Sids::AnonymousLogon
- atlsecurity/ATL::Sids::AuthenticatedUser
- atlsecurity/ATL::Sids::BackupOps
- atlsecurity/ATL::Sids::Batch
- atlsecurity/ATL::Sids::CreatorGroup
- atlsecurity/ATL::Sids::CreatorGroupServer
- atlsecurity/ATL::Sids::CreatorOwner
- atlsecurity/ATL::Sids::CreatorOwnerServer
- atlsecurity/ATL::Sids::Dialup
- atlsecurity/ATL::Sids::Guests
- atlsecurity/ATL::Sids::Interactive
- atlsecurity/ATL::Sids::Local
- atlsecurity/ATL::Sids::Network
- atlsecurity/ATL::Sids::NetworkService
- atlsecurity/ATL::Sids::Null
- atlsecurity/ATL::Sids::PowerUsers
- atlsecurity/ATL::Sids::PrintOps
- atlsecurity/ATL::Sids::Proxy
- atlsecurity/ATL::Sids::RasServers
- atlsecurity/ATL::Sids::Replicator
- atlsecurity/ATL::Sids::RestrictedCode
- atlsecurity/ATL::Sids::Self
- atlsecurity/ATL::Sids::ServerLogon
- atlsecurity/ATL::Sids::Service
- atlsecurity/ATL::Sids::System
- atlsecurity/ATL::Sids::SystemOps
- atlsecurity/ATL::Sids::TerminalServer
- atlsecurity/ATL::Sids::Users
- atlsecurity/ATL::Sids::World
dev_langs: C++
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0a8c0b901bf5be8bc89e9e77a0fa65d86bb29add
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="security-identifier-global-functions"></a>Globální funkce identifikátor zabezpečení
Tyto funkce vrátí běžné známého identifikátoru SID objekty.  
  
> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze používat v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
|||  
|-|-|  
|[SIDs::AccountOps](#accountops)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_ACCOUNT_OPS.|  
|[SIDs::Admins](#admins)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_ADMINS.|  
|[SIDs::AnonymousLogon](#anonymouslogon)|Vrátí identifikátor SID SECURITY_ANONYMOUS_LOGON_RID.|  
|[SIDs::AuthenticatedUser](#authenticateduser)|Vrátí identifikátor SID SECURITY_AUTHENTICATED_USER_RID.|  
|[SIDs::BackupOps](#backupops)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_BACKUP_OPS.|  
|[SIDs::batch](#batch)|Vrátí identifikátor SID SECURITY_BATCH_RID.|  
|[SIDs::CreatorGroup](#creatorgroup)|Vrátí identifikátor SID SECURITY_CREATOR_GROUP_RID.|  
|[SIDs::CreatorGroupServer](#creatorgroupserver)|Vrátí identifikátor SID SECURITY_CREATOR_GROUP_SERVER_RID.|  
|[SIDs::CreatorOwner](#creatorowner)|Vrátí identifikátor SID SECURITY_CREATOR_OWNER_RID.|  
|[SIDs::CreatorOwnerServer](#creatorownerserver)|Vrátí identifikátor SID SECURITY_CREATOR_OWNER_SERVER_RID.|  
|[SIDs::Dialup](#dialup)|Vrátí identifikátor SID SECURITY_DIALUP_RID.|  
|[SIDs::Guests](#guests)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_GUESTS.|  
|[SIDs::Interactive](#interactive)|Vrátí identifikátor SID SECURITY_INTERACTIVE_RID.|  
|[SIDs::Local](#local)|Vrátí identifikátor SID SECURITY_LOCAL_RID.|  
|[SIDs::Network](#network)|Vrátí identifikátor SID SECURITY_NETWORK_RID.|  
|[SIDs::NetworkService](#networkservice)|Vrátí identifikátor SID SECURITY_NETWORK_SERVICE_RID.|  
|[SIDs::Null](#null)|Vrátí identifikátor SID SECURITY_NULL_RID.|  
|[SIDs::PreW2KAccess](#prew2kaccess)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.|  
|[SIDs::PowerUsers](#powerusers)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_POWER_USERS.|  
|[SIDs::PrintOps](#printops)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_PRINT_OPS.|  
|[SIDs::proxy](#proxy)|Vrátí identifikátor SID SECURITY_PROXY_RID.|  
|[SIDs::RasServers](#rasservers)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_RAS_SERVERS.|  
|[SIDs::Replicator](#replicator)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_REPLICATOR.|  
|[SIDs::RestrictedCode](#restrictedcode)|Vrátí identifikátor SID SECURITY_RESTRICTED_CODE_RID.|  
|[SIDs::Self](#self)|Vrátí identifikátor SID SECURITY_PRINCIPAL_SELF_RID.|  
|[SIDs::ServerLogon](#serverlogon)|Vrátí identifikátor SID SECURITY_SERVER_LOGON_RID.|  
|[SIDs::Service](#service)|Vrátí identifikátor SID SECURITY_SERVICE_RID.|  
|[SIDs::System](#system)|Vrátí identifikátor SID SECURITY_LOCAL_SYSTEM_RID.|  
|[SIDs::SystemOps](#systemops)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_SYSTEM_OPS.|  
|[SIDs::TerminalServer](#terminalserver)|Vrátí identifikátor SID SECURITY_TERMINAL_SERVER_RID.|  
|[SIDs::Users](#users)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_USERS.|  
|[SIDs::World](#world)|Vrátí identifikátor SID SECURITY_WORLD_RID.|  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h 

##  <a name="accountops"></a>SIDs::AccountOps  
 Vrátí identifikátor SID DOMAIN_ALIAS_RID_ACCOUNT_OPS.    
  
```
CSid AccountOps() throw(...);
```  
  
##  <a name="admins"></a>SIDs::Admins  
 Vrátí identifikátor SID DOMAIN_ALIAS_RID_ADMINS.  
```
CSid Admins() throw(...);
```  
  
##  <a name="anonymouslogon"></a>SIDs::AnonymousLogon  
 Vrátí identifikátor SID SECURITY_ANONYMOUS_LOGON_RID.  
```
CSid AnonymousLogon() throw(...);
```  
  
##  <a name="authenticateduser"></a>SIDs::AuthenticatedUser  
 Vrátí identifikátor SID SECURITY_AUTHENTICATED_USER_RID.  
```
CSid AuthenticatedUser() throw(...);
```  
  
##  <a name="backupops"></a>SIDs::BackupOps  
 Vrátí identifikátor SID DOMAIN_ALIAS_RID_BACKUP_OPS.  
```
CSid BackupOps() throw(...);
```  
  
##  <a name="batch"></a>SIDs::batch  
 Vrátí identifikátor SID SECURITY_BATCH_RID.  
```
CSid Batch() throw(...);
```  
  
##  <a name="creatorgroup"></a>SIDs::CreatorGroup  
 Vrátí identifikátor SID SECURITY_CREATOR_GROUP_RID.  
```
CSid CreatorGroup() throw(...);
```  
  
##  <a name="creatorgroupserver"></a>SIDs::CreatorGroupServer  
 Vrátí identifikátor SID SECURITY_CREATOR_GROUP_SERVER_RID.  
```
CSid CreatorGroupServer() throw(...);
```  
  
##  <a name="creatorowner"></a>SIDs::CreatorOwner  
 Vrátí identifikátor SID SECURITY_CREATOR_OWNER_RID.  
```
CSid CreatorOwner() throw(...);
```  
  
##  <a name="creatorownerserver"></a>SIDs::CreatorOwnerServer  
 Vrátí identifikátor SID SECURITY_CREATOR_OWNER_SERVER_RID.  
```
CSid CreatorOwnerServer() throw(...);
```  
  
##  <a name="dialup"></a>SIDs::Dialup  
 Vrátí identifikátor SID SECURITY_DIALUP_RID.  
```
CSid Dialup() throw(...);
```  
  
##  <a name="guests"></a>SIDs::Guests  
 Vrátí identifikátor SID DOMAIN_ALIAS_RID_GUESTS.  
```
CSid Guests() throw(...);
```  
  
##  <a name="interactive"></a>SIDs::Interactive  
 Vrátí identifikátor SID SECURITY_INTERACTIVE_RID.  
```
CSid Interactive() throw(...);
```  
  
##  <a name="local"></a>SIDs::Local  
 Vrátí identifikátor SID SECURITY_LOCAL_RID.  
```
CSid Local() throw(...);
```  
  
##  <a name="network"></a>SIDs::Network  
 Vrátí identifikátor SID SECURITY_NETWORK_RID.  
```
CSid Network() throw(...);
```  
  
##  <a name="networkservice"></a>SIDs::NetworkService  
 Vrátí identifikátor SID SECURITY_NETWORK_SERVICE_RID.  
```
CSid NetworkService() throw(...);
```  
  
### <a name="remarks"></a>Poznámky  
 Povolit uživateli NT AUTHORITY\NetworkService čtení CPerfMon objektu zabezpečení pomocí NetworkService. NetworkService přidá třídy SecurityAttribute ATLServer kód, který povolí knihovnu DLL, přihlaste se pod účtem NetworkService na [!INCLUDE[WinXpFamily](../../atl/reference/includes/winxpfamily_md.md)] a větší operačního systému.  
  
 Při vytvoření vlastního protokolu čítače s třídou ATLServer CPerfMon v konzole MMC Perfmon, čítače se při prohlížení souboru protokolu, i když se zobrazí správně v zobrazení v reálném čase. Čítače výkonu vlastní CPerfMon nemáte potřebná oprávnění ke spuštění v rámci služby "A výstrahy a protokolování výkonu" (smlogsvc.exe) [!INCLUDE[WinXpFamily](../../atl/reference/includes/winxpfamily_md.md)] (nebo vyšší) operační systémy. Tato služba je spuštěna pod účtem "NT AUTHORITY\NetworkService".  
  
##  <a name="null"></a>SIDs::Null  
 Vrátí identifikátor SID SECURITY_NULL_RID.  
```
CSid Null() throw(...);
```  
  
##  <a name="prew2kaccess"></a>SIDs::PreW2KAccess  
 Vrátí identifikátor SID DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.  
```
CSid PreW2KAccess() throw(...);
```  
  
##  <a name="powerusers"></a>SIDs::PowerUsers  
 Vrátí identifikátor SID DOMAIN_ALIAS_RID_POWER_USERS.  
```
CSid PowerUsers() throw(...);
```  
  
##  <a name="printops"></a>SIDs::PrintOps  
 Vrátí identifikátor SID DOMAIN_ALIAS_RID_PRINT_OPS.  
```
CSid PrintOps() throw(...);
```  
  
##  <a name="proxy"></a>SIDs::proxy  
 Vrátí identifikátor SID SECURITY_PROXY_RID.  
```
CSid Proxy() throw(...);
```  
  
##  <a name="rasservers"></a>SIDs::RasServers  
 Vrátí identifikátor SID DOMAIN_ALIAS_RID_RAS_SERVERS.  
```
CSid RasServers() throw(...);
```  
  
##  <a name="replicator"></a>SIDs::Replicator  
 Vrátí identifikátor SID DOMAIN_ALIAS_RID_REPLICATOR.  
```
CSid Replicator() throw(...);
```  
  
##  <a name="restrictedcode"></a>SIDs::RestrictedCode  
 Vrátí identifikátor SID SECURITY_RESTRICTED_CODE_RID.  
```
CSid RestrictedCode() throw(...);
```  
  
##  <a name="self"></a>SIDs::Self  
 Vrátí identifikátor SID SECURITY_PRINCIPAL_SELF_RID.  
```
CSid Self() throw(...);
```  
  
##  <a name="serverlogon"></a>SIDs::ServerLogon  
 Vrátí identifikátor SID SECURITY_SERVER_LOGON_RID.  
```
CSid ServerLogon() throw(...);
```  
  
##  <a name="service"></a>SIDs::Service  
 Vrátí identifikátor SID SECURITY_SERVICE_RID.  
```
CSid Service() throw(...);
```  
  
##  <a name="system"></a>SIDs::System  
 Vrátí identifikátor SID SECURITY_LOCAL_SYSTEM_RID.  
```
CSid System() throw(...);
```  
  
##  <a name="systemops"></a>SIDs::SystemOps  
 Vrátí identifikátor SID DOMAIN_ALIAS_RID_SYSTEM_OPS.  
```
CSid SystemOps() throw(...);
```  
  
##  <a name="terminalserver"></a>SIDs::TerminalServer  
 Vrátí identifikátor SID SECURITY_TERMINAL_SERVER_RID.  
```
CSid TerminalServer() throw(...);
```  
  
##  <a name="users"></a>SIDs::Users  
 Vrátí identifikátor SID DOMAIN_ALIAS_RID_USERS.  
```
CSid Users() throw(...);
```  
  
##  <a name="world"></a>SIDs::World  
 Vrátí identifikátor SID SECURITY_WORLD_RID.  
```
CSid World() throw(...);
```  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../../atl/reference/atl-functions.md)
