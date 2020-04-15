---
title: Globální funkce identifikátoru zabezpečení
ms.date: 11/04/2016
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
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
ms.openlocfilehash: 83326c13de7585806ab841f728f587f1131b5e8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325997"
---
# <a name="security-identifier-global-functions"></a>Globální funkce identifikátoru zabezpečení

Tyto funkce vrátí společné známé objekty SID.

> [!IMPORTANT]
> Funkce uvedené v následující tabulce nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

|||
|-|-|
|[Sids::AccountOps](#accountops)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_ACCOUNT_OPS.|
|[Sids::Správci](#admins)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_ADMINS.|
|[Sids::Anonymní přihlášení](#anonymouslogon)|Vrátí identifikátor SID SECURITY_ANONYMOUS_LOGON_RID.|
|[Sids::Ověřený uživatel](#authenticateduser)|Vrátí identifikátor SID SECURITY_AUTHENTICATED_USER_RID.|
|[Sids::ZálohyOps](#backupops)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_BACKUP_OPS.|
|[Sids::Dávka](#batch)|Vrátí identifikátor SID SECURITY_BATCH_RID.|
|[Sids::Skupina pro autory](#creatorgroup)|Vrátí identifikátor SID SECURITY_CREATOR_GROUP_RID.|
|[Sids::CreatorGroupServer](#creatorgroupserver)|Vrátí identifikátor SID SECURITY_CREATOR_GROUP_SERVER_RID.|
|[Sids::CreatorOwner](#creatorowner)|Vrátí identifikátor SID SECURITY_CREATOR_OWNER_RID.|
|[Sids::CreatorOwnerServer](#creatorownerserver)|Vrátí identifikátor SID SECURITY_CREATOR_OWNER_SERVER_RID.|
|[Sids::Dialup](#dialup)|Vrátí identifikátor SID SECURITY_DIALUP_RID.|
|[Sids::Hosté](#guests)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_GUESTS.|
|[Sids::Interaktivní](#interactive)|Vrátí identifikátor SID SECURITY_INTERACTIVE_RID.|
|[Sids::Místní](#local)|Vrátí identifikátor SID SECURITY_LOCAL_RID.|
|[Sids::Síť](#network)|Vrátí identifikátor SID SECURITY_NETWORK_RID.|
|[Sids::NetworkService](#networkservice)|Vrátí identifikátor SID SECURITY_NETWORK_SERVICE_RID.|
|[Sids::Null](#null)|Vrátí identifikátor SID SECURITY_NULL_RID.|
|[Sids::PreW2KAccess](#prew2kaccess)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.|
|[Sids::PowerUživatelé](#powerusers)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_POWER_USERS.|
|[Sids::PrintOps](#printops)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_PRINT_OPS.|
|[Sids::Proxy](#proxy)|Vrátí identifikátor SID SECURITY_PROXY_RID.|
|[Sids::RasServers](#rasservers)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_RAS_SERVERS.|
|[Sids::Replikátor](#replicator)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_REPLICATOR.|
|[Sids::RestrictedCode](#restrictedcode)|Vrátí identifikátor SID SECURITY_RESTRICTED_CODE_RID.|
|[Sids::Vlastní](#self)|Vrátí identifikátor SID SECURITY_PRINCIPAL_SELF_RID.|
|[Sids::ServerLogon](#serverlogon)|Vrátí identifikátor SID SECURITY_SERVER_LOGON_RID.|
|[Sids::Servis](#service)|Vrátí identifikátor SID SECURITY_SERVICE_RID.|
|[Sids::Systém](#system)|Vrátí identifikátor SID SECURITY_LOCAL_SYSTEM_RID.|
|[Sids::SystemOps](#systemops)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_SYSTEM_OPS.|
|[Sids::Terminální server](#terminalserver)|Vrátí identifikátor SID SECURITY_TERMINAL_SERVER_RID.|
|[Sids::Uživatelé](#users)|Vrátí identifikátor SID DOMAIN_ALIAS_RID_USERS.|
|[Sids::Svět](#world)|Vrátí identifikátor SID SECURITY_WORLD_RID.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="sidsaccountops"></a><a name="accountops"></a>Sids::AccountOps

Vrátí identifikátor SID DOMAIN_ALIAS_RID_ACCOUNT_OPS.

```
CSid AccountOps() throw(...);
```

## <a name="sidsadmins"></a><a name="admins"></a>Sids::Správci

Vrátí identifikátor SID DOMAIN_ALIAS_RID_ADMINS.

```
CSid Admins() throw(...);
```

## <a name="sidsanonymouslogon"></a><a name="anonymouslogon"></a>Sids::Anonymní přihlášení

Vrátí identifikátor SID SECURITY_ANONYMOUS_LOGON_RID.

```
CSid AnonymousLogon() throw(...);
```

## <a name="sidsauthenticateduser"></a><a name="authenticateduser"></a>Sids::Ověřený uživatel

Vrátí identifikátor SID SECURITY_AUTHENTICATED_USER_RID.

```
CSid AuthenticatedUser() throw(...);
```

## <a name="sidsbackupops"></a><a name="backupops"></a>Sids::ZálohyOps

Vrátí identifikátor SID DOMAIN_ALIAS_RID_BACKUP_OPS.

```
CSid BackupOps() throw(...);
```

## <a name="sidsbatch"></a><a name="batch"></a>Sids::Dávka

Vrátí identifikátor SID SECURITY_BATCH_RID.

```
CSid Batch() throw(...);
```

## <a name="sidscreatorgroup"></a><a name="creatorgroup"></a>Sids::Skupina pro autory

Vrátí identifikátor SID SECURITY_CREATOR_GROUP_RID.

```
CSid CreatorGroup() throw(...);
```

## <a name="sidscreatorgroupserver"></a><a name="creatorgroupserver"></a>Sids::CreatorGroupServer

Vrátí identifikátor SID SECURITY_CREATOR_GROUP_SERVER_RID.

```
CSid CreatorGroupServer() throw(...);
```

## <a name="sidscreatorowner"></a><a name="creatorowner"></a>Sids::CreatorOwner

Vrátí identifikátor SID SECURITY_CREATOR_OWNER_RID.

```
CSid CreatorOwner() throw(...);
```

## <a name="sidscreatorownerserver"></a><a name="creatorownerserver"></a>Sids::CreatorOwnerServer

Vrátí identifikátor SID SECURITY_CREATOR_OWNER_SERVER_RID.

```
CSid CreatorOwnerServer() throw(...);
```

## <a name="sidsdialup"></a><a name="dialup"></a>Sids::Dialup

Vrátí identifikátor SID SECURITY_DIALUP_RID.

```
CSid Dialup() throw(...);
```

## <a name="sidsguests"></a><a name="guests"></a>Sids::Hosté

Vrátí identifikátor SID DOMAIN_ALIAS_RID_GUESTS.

```
CSid Guests() throw(...);
```

## <a name="sidsinteractive"></a><a name="interactive"></a>Sids::Interaktivní

Vrátí identifikátor SID SECURITY_INTERACTIVE_RID.

```
CSid Interactive() throw(...);
```

## <a name="sidslocal"></a><a name="local"></a>Sids::Místní

Vrátí identifikátor SID SECURITY_LOCAL_RID.

```
CSid Local() throw(...);
```

## <a name="sidsnetwork"></a><a name="network"></a>Sids::Síť

Vrátí identifikátor SID SECURITY_NETWORK_RID.

```
CSid Network() throw(...);
```

## <a name="sidsnetworkservice"></a><a name="networkservice"></a>Sids::NetworkService

Vrátí identifikátor SID SECURITY_NETWORK_SERVICE_RID.

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>Poznámky

Pomocí služby NetworkService můžete uživateli NT AUTHORITY\NetworkService povolit čtení objektu zabezpečení CPerfMon. NetworkService přidá do kódu atlserveru atribut SecurityAttribute, který umožní knihovně DLL přihlásit se pod účtem NetworkService v systémech Windows XP Home Edition, Windows XP Professional, Windows Server 2003 a vyšším operačním systému.

Při vlastní čítače protokolu jsou vytvořeny s ATLServer CPerfMon třídy v Perfmon MMC, čítače nemusí zobrazit při zobrazení souboru protokolu, i když se zobrazí správně v zobrazení v reálném čase. Vlastní čítače výkonu CPerfMon nemají potřebná oprávnění ke spuštění v rámci služby Protokoly a výstrahy výkonu (smlogsvc.exe) v operačních systémech Windows XP Home Edition, Windows XP Professional, Windows Server 2003 (nebo vyšší). Tato služba je spuštěna pod účtem NT AUTHORITY\NetworkService.

## <a name="sidsnull"></a><a name="null"></a>Sids::Null

Vrátí identifikátor SID SECURITY_NULL_RID.

```
CSid Null() throw(...);
```

## <a name="sidsprew2kaccess"></a><a name="prew2kaccess"></a>Sids::PreW2KAccess

Vrátí identifikátor SID DOMAIN_ALIAS_RID_PREW2KCOMPACCESS.

```
CSid PreW2KAccess() throw(...);
```

## <a name="sidspowerusers"></a><a name="powerusers"></a>Sids::PowerUživatelé

Vrátí identifikátor SID DOMAIN_ALIAS_RID_POWER_USERS.

```
CSid PowerUsers() throw(...);
```

## <a name="sidsprintops"></a><a name="printops"></a>Sids::PrintOps

Vrátí identifikátor SID DOMAIN_ALIAS_RID_PRINT_OPS.

```
CSid PrintOps() throw(...);
```

## <a name="sidsproxy"></a><a name="proxy"></a>Sids::Proxy

Vrátí identifikátor SID SECURITY_PROXY_RID.

```
CSid Proxy() throw(...);
```

## <a name="sidsrasservers"></a><a name="rasservers"></a>Sids::RasServers

Vrátí identifikátor SID DOMAIN_ALIAS_RID_RAS_SERVERS.

```
CSid RasServers() throw(...);
```

## <a name="sidsreplicator"></a><a name="replicator"></a>Sids::Replikátor

Vrátí identifikátor SID DOMAIN_ALIAS_RID_REPLICATOR.

```
CSid Replicator() throw(...);
```

## <a name="sidsrestrictedcode"></a><a name="restrictedcode"></a>Sids::RestrictedCode

Vrátí identifikátor SID SECURITY_RESTRICTED_CODE_RID.

```
CSid RestrictedCode() throw(...);
```

## <a name="sidsself"></a><a name="self"></a>Sids::Vlastní

Vrátí identifikátor SID SECURITY_PRINCIPAL_SELF_RID.

```
CSid Self() throw(...);
```

## <a name="sidsserverlogon"></a><a name="serverlogon"></a>Sids::ServerLogon

Vrátí identifikátor SID SECURITY_SERVER_LOGON_RID.

```
CSid ServerLogon() throw(...);
```

## <a name="sidsservice"></a><a name="service"></a>Sids::Servis

Vrátí identifikátor SID SECURITY_SERVICE_RID.

```
CSid Service() throw(...);
```

## <a name="sidssystem"></a><a name="system"></a>Sids::Systém

Vrátí identifikátor SID SECURITY_LOCAL_SYSTEM_RID.

```
CSid System() throw(...);
```

## <a name="sidssystemops"></a><a name="systemops"></a>Sids::SystemOps

Vrátí identifikátor SID DOMAIN_ALIAS_RID_SYSTEM_OPS.

```
CSid SystemOps() throw(...);
```

## <a name="sidsterminalserver"></a><a name="terminalserver"></a>Sids::Terminální server

Vrátí identifikátor SID SECURITY_TERMINAL_SERVER_RID.

```
CSid TerminalServer() throw(...);
```

## <a name="sidsusers"></a><a name="users"></a>Sids::Uživatelé

Vrátí identifikátor SID DOMAIN_ALIAS_RID_USERS.

```
CSid Users() throw(...);
```

## <a name="sidsworld"></a><a name="world"></a>Sids::Svět

Vrátí identifikátor SID SECURITY_WORLD_RID.

```
CSid World() throw(...);
```

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)
