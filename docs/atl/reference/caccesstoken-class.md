---
title: "Třída CAccessToken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAccessToken
- ATLSECURITY/ATL::CAccessToken
- ATLSECURITY/ATL::CAccessToken::Attach
- ATLSECURITY/ATL::CAccessToken::CheckTokenMembership
- ATLSECURITY/ATL::CAccessToken::CreateImpersonationToken
- ATLSECURITY/ATL::CAccessToken::CreatePrimaryToken
- ATLSECURITY/ATL::CAccessToken::CreateProcessAsUser
- ATLSECURITY/ATL::CAccessToken::CreateRestrictedToken
- ATLSECURITY/ATL::CAccessToken::Detach
- ATLSECURITY/ATL::CAccessToken::DisablePrivilege
- ATLSECURITY/ATL::CAccessToken::DisablePrivileges
- ATLSECURITY/ATL::CAccessToken::EnablePrivilege
- ATLSECURITY/ATL::CAccessToken::EnablePrivileges
- ATLSECURITY/ATL::CAccessToken::GetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::GetEffectiveToken
- ATLSECURITY/ATL::CAccessToken::GetGroups
- ATLSECURITY/ATL::CAccessToken::GetHandle
- ATLSECURITY/ATL::CAccessToken::GetImpersonationLevel
- ATLSECURITY/ATL::CAccessToken::GetLogonSessionId
- ATLSECURITY/ATL::CAccessToken::GetLogonSid
- ATLSECURITY/ATL::CAccessToken::GetOwner
- ATLSECURITY/ATL::CAccessToken::GetPrimaryGroup
- ATLSECURITY/ATL::CAccessToken::GetPrivileges
- ATLSECURITY/ATL::CAccessToken::GetProcessToken
- ATLSECURITY/ATL::CAccessToken::GetProfile
- ATLSECURITY/ATL::CAccessToken::GetSource
- ATLSECURITY/ATL::CAccessToken::GetStatistics
- ATLSECURITY/ATL::CAccessToken::GetTerminalServicesSessionId
- ATLSECURITY/ATL::CAccessToken::GetThreadToken
- ATLSECURITY/ATL::CAccessToken::GetTokenId
- ATLSECURITY/ATL::CAccessToken::GetType
- ATLSECURITY/ATL::CAccessToken::GetUser
- ATLSECURITY/ATL::CAccessToken::HKeyCurrentUser
- ATLSECURITY/ATL::CAccessToken::Impersonate
- ATLSECURITY/ATL::CAccessToken::ImpersonateLoggedOnUser
- ATLSECURITY/ATL::CAccessToken::IsTokenRestricted
- ATLSECURITY/ATL::CAccessToken::LoadUserProfile
- ATLSECURITY/ATL::CAccessToken::LogonUser
- ATLSECURITY/ATL::CAccessToken::OpenCOMClientToken
- ATLSECURITY/ATL::CAccessToken::OpenNamedPipeClientToken
- ATLSECURITY/ATL::CAccessToken::OpenRPCClientToken
- ATLSECURITY/ATL::CAccessToken::OpenThreadToken
- ATLSECURITY/ATL::CAccessToken::PrivilegeCheck
- ATLSECURITY/ATL::CAccessToken::Revert
- ATLSECURITY/ATL::CAccessToken::SetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::SetOwner
- ATLSECURITY/ATL::CAccessToken::SetPrimaryGroup
dev_langs: C++
helpviewer_keywords: CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3df4c5ac46c159cd3ed955621af914c677182a57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="caccesstoken-class"></a>CAccessToken – třída
Tato třída je obálka pro přístupový token.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAccessToken
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAccessToken:: ~ CAccessToken](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAccessToken::Attach](#attach)|Volejte tuto metodu za účelem převzít vlastnictví tokenu popisovač přístup.|  
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Voláním této metody lze zjistit, pokud je povoleno zadané SID `CAccessToken` objektu.|  
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Voláním této metody lze vytvořit nový přístupový token zosobnění.|  
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Volejte tuto metodu za účelem vytvoření nové primární tokenu.|  
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Voláním této metody lze vytvořit nový proces, který běží v kontextu zabezpečení uživatele reprezentován `CAccessToken` objektu.|  
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Volat tuto metodu pro vytvoření nového, s omezeným přístupem `CAccessToken` objektu.|  
|[CAccessToken::Detach](#detach)|Volejte tuto metodu za účelem odvolat vlastnictví přístupový token.|  
|[CAccessToken::DisablePrivilege](#disableprivilege)|Voláním této metody lze zakázat oprávnění v `CAccessToken` objektu.|  
|[CAccessToken::DisablePrivileges](#disableprivileges)|Voláním této metody lze zakázat jeden nebo více oprávnění v `CAccessToken` objektu.|  
|[CAccessToken::EnablePrivilege](#enableprivilege)|Voláním této metody lze povolit oprávnění v `CAccessToken` objektu.|  
|[CAccessToken::EnablePrivileges](#enableprivileges)|Volat tuto metodu za účelem povolení jeden nebo více oprávnění v `CAccessToken` objektu.|  
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Volání této metody vrátit `CAccessToken` objektu výchozí DACL.|  
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Voláním této metody lze získat `CAccessToken` objekt rovná přístupový token platí pro aktuální vlákno.|  
|[CAccessToken::GetGroups](#getgroups)|Volání této metody vrátit `CAccessToken` objektu tokenu skupiny.|  
|[CAccessToken::GetHandle](#gethandle)|Volejte tuto metodu za účelem načtení popisovače do tokenu přístupu.|  
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Volejte tuto metodu za účelem získání úroveň zosobnění z tokenu přístupu.|  
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Volat tuto metodu za účelem získání ID relace přihlášení přidružené `CAccessToken` objektu.|  
|[CAccessToken::GetLogonSid](#getlogonsid)|Volat tuto metodu a získejte SID přihlášení přidružené `CAccessToken` objektu.|  
|[CAccessToken::GetOwner](#getowner)|Volat tuto metodu k získání vlastníka přidružené `CAccessToken` objektu.|  
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Volat tuto metodu za účelem získání primární skupiny přidružené `CAccessToken` objektu.|  
|[CAccessToken::GetPrivileges](#getprivileges)|Volat tuto metodu za účelem získání oprávnění přidružených k `CAccessToken` objektu.|  
|[CAccessToken::GetProcessToken](#getprocesstoken)|Voláním této metody lze inicializovat `CAccessToken` s tímto tokenem přístupu z daného procesu.|  
|[CAccessToken::GetProfile](#getprofile)|Voláním této metody lze získat popisovač odkazující na přidružený profil uživatele `CAccessToken` objektu.|  
|[CAccessToken::GetSource](#getsource)|Volat tuto metodu za účelem získání zdroj `CAccessToken` objektu.|  
|[CAccessToken::GetStatistics](#getstatistics)|Volat tuto metodu za účelem získání informací o přidružené `CAccessToken` objektu.|  
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Volat tuto metodu za účelem získání ID relace Terminálové služby přidružené k `CAccessToken` objektu.|  
|[CAccessToken::GetThreadToken](#getthreadtoken)|Voláním této metody lze inicializovat `CAccessToken` s tokenem z dané vlákno.|  
|[CAccessToken::GetTokenId](#gettokenid)|Volat tuto metodu za účelem získání tokenu ID přidružené `CAccessToken` objektu.|  
|[CAccessToken::GetType](#gettype)|Volat tuto metodu za účelem získání tokenu typ `CAccessToken` objektu.|  
|[CAccessToken::GetUser](#getuser)|Volat tuto metodu za účelem identifikace uživatele přidruženého k `CAccessToken` objektu.|  
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Voláním této metody lze získat popisovač odkazující na přidružený profil uživatele `CAccessToken` objektu.|  
|[CAccessToken::Impersonate](#impersonate)|Voláním této metody lze přiřadit zosobnění `CAccessToken` na vlákno.|  
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Voláním této metody lze povolit volající vlákno k zosobnění kontextu zabezpečení přihlášeného uživatele.|  
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Volat tuto metodu za účelem testování, pokud `CAccessToken` objekt obsahuje seznam identifikátorů SID s omezeným přístupem.|  
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Voláním této metody lze načíst profil uživatele přidružený k `CAccessToken` objektu.|  
|[CAccessToken::LogonUser](#logonuser)|Volejte tuto metodu pro vytvoření relace přihlášení pro uživatele přidruženého k dané přihlašovací údaje.|  
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Volat tuto metodu v rámci server COM, zpracování volání od klienta k chybě při inicializaci z `CAccessToken` s tímto tokenem přístupu z COM klienta.|  
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Volat tuto metodu z v rámci serveru pořízení požadavky přes pojmenovaný kanál k chybě při inicializaci `CAccessToken` s tímto tokenem přístupu z klienta.|  
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Volat tuto metodu v rámci serveru zpracování volání od klienta k chybě při inicializaci z `CAccessToken` s tímto tokenem přístupu z klienta.|  
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Voláním této metody lze nastavit úroveň zosobnění a potom inicializujte `CAccessToken` s tokenem z dané vlákno.|  
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Voláním této metody lze zjistit, zda jsou zadané sady oprávnění povoleno **CAccessToken** objektu.|  
|[CAccessToken::Revert](#revert)|Volejte tuto metodu za účelem zastavení podprocesu, který používá token zosobnění.|  
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Volat tuto metodu a nastavit výchozí seznam DACL `CAccessToken` objektu.|  
|[CAccessToken::SetOwner](#setowner)|Volat tuto metodu a nastavit vlastníka `CAccessToken` objektu.|  
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Volat tuto metodu a nastavit primární skupiny `CAccessToken` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 [Přístupový token](http://msdn.microsoft.com/library/windows/desktop/aa374909) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen všem uživatelům přihlášení systému Windows NT nebo Windows 2000.  
  
 Úvod do model řízení přístupu v systému Windows, najdete v části [řízení přístupu](http://msdn.microsoft.com/library/windows/desktop/aa374860) ve Windows SDK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h  
  
##  <a name="attach"></a>CAccessToken::Attach  
 Volejte tuto metodu za účelem převzít vlastnictví tokenu popisovač přístup.  
  
```
void Attach(HANDLE hToken) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *hToken*  
 Obslužná rutina do tokenu přístupu.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění, dojde k chybě assertion Pokud `CAccessToken` objektu již je vlastnictví přístupový token.  
  
##  <a name="dtor"></a>CAccessToken:: ~ CAccessToken  
 Destruktor.  
  
```
virtual ~CAccessToken() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership  
 Voláním této metody lze zjistit, pokud je povoleno zadané SID `CAccessToken` objektu.  
  
```
bool CheckTokenMembership(
    const CSid& rSid, 
    bool* pbIsMember) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 Odkaz na [identifikační číslo volané stanice třída](../../atl/reference/csid-class.md) objektu.  
  
 `pbIsMember`  
 Ukazatel na proměnnou, která přijímá výsledky kontroly.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 `CheckTokenMembership` Metoda zkontroluje přítomnost SID v uživatelů a skupin SID přístupového tokenu. Pokud SID je k dispozici a obsahuje atribut SE_GROUP_ENABLED, *pbIsMember* je nastaven na hodnotu true; jinak hodnota, je nastavený na hodnotu false.  
  
 V sestavení pro ladění, dojde k chybě assertion Pokud `pbIsMember` není platný.  
  
> [!NOTE]
>  `CAccessToken` Objekt musí být token zosobnění a není primární token.  
  
##  <a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken  
 Volejte tuto metodu za účelem vytváření tokenu zosobnění.  
  
```
bool CreateImpersonationToken(
    CAccessToken* pImp, 
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pImp`  
 Ukazatel na nové `CAccessToken` objektu.  
  
 `sil`  
 Určuje [SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572) výčtového typu, který poskytuje úroveň zosobnění nový token.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 `CreateImpersonationToken`volání [DuplicateToken](http://msdn.microsoft.com/library/windows/desktop/aa446616) vytvořit nový token zosobnění.  
  
##  <a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken  
 Volejte tuto metodu za účelem vytvoření nové primární tokenu.  
  
```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pPri*  
 Ukazatel na nové `CAccessToken` objektu.  
  
 `dwDesiredAccess`  
 Určuje požadovaný přístupová práva pro nový token. Výchozí, MAXIMUM_ALLOWED, vyžádá všechna přístupová práva, které jsou platné pro volajícího. V tématu [přístupová práva a masek přístup](http://msdn.microsoft.com/library/windows/desktop/aa374902) pro další na přístupová práva.  
  
 *pTokenAttributes*  
 Ukazatel na [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která určuje popisovače zabezpečení pro nový token a určuje, zda může dědit vlastnosti podřízené procesy token. Pokud *pTokenAttributes* má hodnotu NULL, je token získá výchozí popisovač zabezpečení a nelze ji zdědit popisovač.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 `CreatePrimaryToken`volání [DuplicateTokenEx](http://msdn.microsoft.com/library/windows/desktop/aa446617) k vytvoření nové primární tokenu.  
  
##  <a name="createprocessasuser"></a>CAccessToken::CreateProcessAsUser  
 Voláním této metody lze vytvořit nový proces, který běží v kontextu zabezpečení uživatele reprezentován `CAccessToken` objektu.  
  
```
bool CreateProcessAsUser(
    LPCTSTR pApplicationName,
    LPTSTR pCommandLine,
    LPPROCESS_INFORMATION pProcessInformation,
    LPSTARTUPINFO pStartupInfo,
    DWORD dwCreationFlags = NORMAL_PRIORITY_CLASS,
    bool bLoadProfile = false,
    const CSecurityAttributes* pProcessAttributes = NULL,
    const CSecurityAttributes* pThreadAttributes = NULL,
    bool bInherit = false,
    LPCTSTR pCurrentDirectory = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pApplicationName*  
 Ukazatel na řetězec ukončené hodnotou null, který určuje modul provést. Tento parametr nesmí mít hodnotu NULL.  
  
 *pCommandLine*  
 Ukazatel na řetězec ukončené hodnotou null, který určuje příkazový řádek pro spuštění.  
  
 *pProcessInformation*  
 Ukazatel na [PROCESS_INFORMATION](http://msdn.microsoft.com/library/windows/desktop/ms684873) struktura, která přijímá identifikační informace o nový proces.  
  
 *pStartupInfo*  
 Ukazatel na [OBVYKLE](http://msdn.microsoft.com/library/windows/desktop/ms686331) struktura, která určuje, jak se mají zobrazit hlavního okna pro nový proces.  
  
 `dwCreationFlags`  
 Určuje další příznaky, které řídí s prioritou a vytvoření procesu. Najdete v části funkce Win32 [CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429) seznam příznaky.  
  
 *bLoadProfile*  
 Pokud hodnotu true, profil uživatele je načtena s [LoadUserProfile](http://msdn.microsoft.com/library/windows/desktop/bb762281).  
  
 *pProcessAttributes*  
 Ukazatel na [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která určuje popisovače zabezpečení pro nový proces a určuje, zda může dědit vlastnosti podřízené procesy Vrácený popisovač. Pokud *pProcessAttributes* má hodnotu NULL, proces získá výchozí popisovač zabezpečení a nelze ji zdědit popisovač.  
  
 *pThreadAttributes*  
 Ukazatel na [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která určuje popisovače zabezpečení pro nové vlákno a určuje, zda může dědit vlastnosti podřízené procesy Vrácený popisovač. Pokud *pThreadAttributes* má hodnotu NULL, vlákno získá výchozí popisovač zabezpečení a nelze ji zdědit popisovač.  
  
 *bInherit*  
 Určuje, zda nový proces dědí z procesu volání obslužné rutiny. V případě hodnoty true každý zděditelné otevřený popisovač v procesu volání zdědí nový proces. Zděděné obslužné rutiny mají stejnou hodnotu a přístup oprávnění jako původní obslužné rutiny.  
  
 *pCurrentDirectory*  
 Ukazatel na řetězec ukončené hodnotou null, který určuje aktuální jednotku a adresář pro nový proces. Řetězec musí být úplná cesta, která obsahuje písmeno jednotky. Pokud tento parametr hodnotu NULL, nový proces bude mít stejný aktuální jednotku a adresář jako volající proces.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 **CreateProcessAsUser** používá `CreateProcessAsUser` Win32 funkci pro vytvoření nového procesu, který je spuštěn v kontextu zabezpečení uživatele reprezentován `CAccessToken` objektu. Viz popis [CreateProcessAsUser](http://msdn.microsoft.com/library/windows/desktop/ms682429) funkce úplnou diskusi o parametry vyžadované.  
  
 Pro tuto metodu za účelem úspěšné `CAccessToken` objekt musí obsahovat AssignPrimaryToken (Pokud je token s omezeným přístupem) a IncreaseQuota oprávnění.  
  
##  <a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken  
 Volat tuto metodu pro vytvoření nového, s omezeným přístupem `CAccessToken` objektu.  
  
```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pRestrictedToken*  
 Nové, omezený `CAccessToken` objektu.  
  
 `SidsToDisable`  
 A `CTokenGroups` objekt, který určuje SID jenom pro odepření.  
  
 *SidsToRestrict*  
 A `CTokenGroups` objekt, který určuje omezení identifikátory SID.  
  
 `PrivilegesToDelete`  
 A `CTokenPrivileges` objekt, který určuje oprávnění k odstranění v tokenu s omezeným přístupem. Výchozí nastavení vytvoří prázdný objekt.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 `CreateRestrictedToken`používá [CreateRestrictedToken](http://msdn.microsoft.com/library/windows/desktop/aa446583) Win32 funkci pro vytvoření nového `CAccessToken` objekt omezení.  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici v systému Windows 2000 nebo novější.  
  
> [!IMPORTANT]
>  Při použití `CreateRestrictedToken`, zkontrolujte následující: existující token je platný (a není zadané uživatelem) a `SidsToDisable` a `PrivilegesToDelete` jsou platné (i není zadaná uživatelem). Pokud metoda vrátí hodnotu false, zakázat funkce.  
  
##  <a name="detach"></a>CAccessToken::Detach  
 Volejte tuto metodu za účelem odvolat vlastnictví přístupový token.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač `CAccessToken` který odpojit.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odvolá `CAccessToken`na vlastnictví přístupový token.  
  
##  <a name="disableprivilege"></a>CAccessToken::DisablePrivilege  
 Voláním této metody lze zakázat oprávnění v `CAccessToken` objektu.  
  
```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrivilege`  
 Ukazatel na řetězec obsahující oprávnění k zakázání v `CAccessToken` objektu.  
  
 `pPreviousState`  
 Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="disableprivileges"></a>CAccessToken::DisablePrivileges  
 Voláním této metody lze zakázat jeden nebo více oprávnění v `CAccessToken` objektu.  
  
```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rPrivileges`  
 Ukazatel na pole řetězců obsahující oprávnění zakázat v `CAccessToken` objektu.  
  
 `pPreviousState`  
 Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="enableprivilege"></a>CAccessToken::EnablePrivilege  
 Voláním této metody lze povolit oprávnění v `CAccessToken` objektu.  
  
```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszPrivilege`  
 Ukazatel na řetězec obsahující oprávnění k povolení v `CAccessToken` objektu.  
  
 `pPreviousState`  
 Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="enableprivileges"></a>CAccessToken::EnablePrivileges  
 Volat tuto metodu za účelem povolení jeden nebo více oprávnění v `CAccessToken` objektu.  
  
```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rPrivileges`  
 Ukazatel na pole řetězců obsahující oprávnění pro povolení v `CAccessToken` objektu.  
  
 `pPreviousState`  
 Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl  
 Volání této metody vrátit `CAccessToken` objektu výchozí DACL.  
  
```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pDacl`  
 Ukazatel na [CDacl třída](../../atl/reference/cdacl-class.md) objekt, který se zobrazí **CAccessToken** objektu výchozí DACL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true Pokud výchozí seznam DACL ho ZAMEZUJE byl obnovené, false, jinak hodnota.  
  
##  <a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken  
 Voláním této metody lze získat `CAccessToken` objekt rovná přístupový token platí pro aktuální vlákno.  
  
```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 Určuje masky přístupu, která určuje požadovanou typy přístupu do tokenu přístupu. Tyto typy požadovaný přístup jsou porovnávány s DACL je token k určení, který přistupuje jsou povolen nebo odepřen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="getgroups"></a>CAccessToken::GetGroups  
 Volání této metody vrátit `CAccessToken` objektu tokenu skupiny.  
  
```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pGroups*  
 Ukazatel [CTokenGroups třída](../../atl/reference/ctokengroups-class.md) objekt, který se zobrazí informace o skupinách.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="gethandle"></a>CAccessToken::GetHandle  
 Volejte tuto metodu za účelem načtení popisovače do tokenu přístupu.  
  
```
HANDLE GetHandle() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač pro `CAccessToken` objektu přístupový token.  
  
##  <a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel  
 Volejte tuto metodu za účelem získání úroveň zosobnění z tokenu přístupu.  
  
```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pImpersonationLevel*  
 Ukazatel na [SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572) typ výčtu, která se zobrazí informace o úrovni zosobnění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId  
 Volat tuto metodu za účelem získání ID relace přihlášení přidružené `CAccessToken` objektu.  
  
```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pluid`  
 Ukazatel na [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261) který obdrží ID relace přihlášení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění, dojde k chybě assertion Pokud `pluid` je neplatná hodnota.  
  
##  <a name="getlogonsid"></a>CAccessToken::GetLogonSid  
 Volat tuto metodu a získejte SID přihlášení přidružené `CAccessToken` objektu.  
  
```
bool GetLogonSid(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Ukazatel na [identifikační číslo volané stanice třída](../../atl/reference/csid-class.md) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění, dojde k chybě assertion Pokud *pSid* je neplatná hodnota.  
  
##  <a name="getowner"></a>CAccessToken::GetOwner  
 Volat tuto metodu k získání vlastníka přidružené `CAccessToken` objektu.  
  
```
bool GetOwner(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Ukazatel na [identifikační číslo volané stanice třída](../../atl/reference/csid-class.md) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Vlastník nastavena na všechny objekty vytvořené během tohoto tokenu přístupu je v platnosti ve výchozím nastavení.  
  
##  <a name="getprimarygroup"></a>CAccessToken::GetPrimaryGroup  
 Volat tuto metodu za účelem získání primární skupiny přidružené `CAccessToken` objektu.  
  
```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Ukazatel na [identifikační číslo volané stanice třída](../../atl/reference/csid-class.md) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Tato skupina nastavení na všechny objekty vytvořené během tohoto tokenu přístupu je v platnosti ve výchozím nastavení.  
  
##  <a name="getprivileges"></a>CAccessToken::GetPrivileges  
 Volat tuto metodu za účelem získání oprávnění přidružených k `CAccessToken` objektu.  
  
```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pPrivileges`  
 Ukazatel na [CTokenPrivileges třída](../../atl/reference/ctokenprivileges-class.md) objekt, který obdrží oprávnění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="getprocesstoken"></a>CAccessToken::GetProcessToken  
 Voláním této metody lze inicializovat `CAccessToken` s tímto tokenem přístupu z daného procesu.  
  
```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 Určuje masky přístupu, která určuje požadovanou typy přístupu do tokenu přístupu. Tyto typy požadovaný přístup jsou porovnávány s DACL je token k určení, který přistupuje jsou povolen nebo odepřen.  
  
 *hProcess*  
 Zpracování procesu, jejichž přístupový token je otevřen. Pokud výchozí hodnotu `NULL` se používá, se používá aktuální proces.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `true` v případě úspěchu `false` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [funkce OpenProcessToken](http://msdn.microsoft.com/library/aa379295\(vs.85\).aspx) Win32 funkce.  
  
##  <a name="getprofile"></a>CAccessToken::GetProfile  
 Voláním této metody lze získat popisovač odkazující na přidružený profil uživatele `CAccessToken` objektu.  
  
```
HANDLE GetProfile() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač odkazující na profil uživatele nebo hodnotu NULL, pokud neexistuje žádný profil.  
  
##  <a name="getsource"></a>CAccessToken::GetSource  
 Volat tuto metodu za účelem získání zdroj `CAccessToken` objektu.  
  
```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pSource*  
 Ukazatel na [TOKEN_SOURCE](http://msdn.microsoft.com/library/windows/desktop/aa379631) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="getstatistics"></a>CAccessToken::GetStatistics  
 Volat tuto metodu za účelem získání informací o přidružené `CAccessToken` objektu.  
  
```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pStatistics*  
 Ukazatel na [TOKEN_STATISTICS](http://msdn.microsoft.com/library/windows/desktop/aa379632) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="getterminalservicessessionid"></a>CAccessToken::GetTerminalServicesSessionId  
 Volat tuto metodu za účelem získání ID relace Terminálové služby přidružené k `CAccessToken` objektu.  
  
```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *pdwSessionId*  
 ID relace Terminálové služby.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="getthreadtoken"></a>CAccessToken::GetThreadToken  
 Voláním této metody lze inicializovat `CAccessToken` s tokenem z dané vlákno.  
  
```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 Určuje masky přístupu, která určuje požadovanou typy přístupu do tokenu přístupu. Tyto typy požadovaný přístup jsou porovnávány s DACL je token k určení, který přistupuje jsou povolen nebo odepřen.  
  
 `hThread`  
 Zpracování vlákno, jejichž přístupový token je otevřen.  
  
 `bOpenAsSelf`  
 Určuje, zda má být provedeno před kontext zabezpečení volání vláken je kontrola přístupu `GetThreadToken` metoda nebo podle kontextu zabezpečení procesu volající vlákno.  
  
 Pokud má parametr hodnotu false, kontrola přístupu se provádí v kontextu zabezpečení pro volající vlákno. Pokud vlákno zosobňuje klienta, může být takový kontext zabezpečení, která procesu klienta. Je-li tento parametr hodnotu true, je kontrola přístupu provedené v kontextu zabezpečení procesu pro volající vlákno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="gettokenid"></a>CAccessToken::GetTokenId  
 Volat tuto metodu za účelem získání tokenu ID přidružené `CAccessToken` objektu.  
  
```
bool GetTokenId(LUID* pluid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pluid`  
 Ukazatel na [LUID](http://msdn.microsoft.com/library/windows/desktop/aa379261) který obdrží Token ID.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="gettype"></a>CAccessToken::GetType  
 Volat tuto metodu za účelem získání tokenu typ `CAccessToken` objektu.  
  
```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pType`  
 Adresa [TOKEN_TYPE](http://msdn.microsoft.com/library/windows/desktop/aa379633) proměnné, která v případě úspěchu obdrží typ tokenu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 **TOKEN_TYPE** typ výčtu obsahuje hodnoty, které rozlišit mezi primární token a token zosobnění.  
  
##  <a name="getuser"></a>CAccessToken::GetUser  
 Volat tuto metodu za účelem identifikace uživatele přidruženého k `CAccessToken` objektu.  
  
```
bool GetUser(CSid* pSid) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `pSid`  
 Ukazatel na [identifikační číslo volané stanice třída](../../atl/reference/csid-class.md) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
##  <a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser  
 Voláním této metody lze získat popisovač odkazující na přidružený profil uživatele `CAccessToken` objektu.  
  
```
HKEY HKeyCurrentUser() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač odkazující na profil uživatele nebo hodnotu NULL, pokud neexistuje žádný profil.  
  
##  <a name="impersonate"></a>CAccessToken::Impersonate  
 Voláním této metody lze přiřadit zosobnění `CAccessToken` na vlákno.  
  
```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `hThread`  
 Popisovač vlákno přiřadit token zosobnění. Tento popisovač je nutné otevřít s TOKEN_IMPERSONATE přístupová práva. Pokud `hThread` má hodnotu NULL, metoda způsobí, že podproces přestat používat token zosobnění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění, dojde k chybě assertion Pokud `CAccessToken` nemá platný ukazatel na token.  
  
 [CAutoRevertImpersonation třída](../../atl/reference/cautorevertimpersonation-class.md) umožňuje automaticky vracet zosobněnou přístupových tokenů.  
  
##  <a name="impersonateloggedonuser"></a>CAccessToken::ImpersonateLoggedOnUser  
 Voláním této metody lze povolit volající vlákno k zosobnění kontextu zabezpečení přihlášeného uživatele.  
  
```
bool ImpersonateLoggedOnUser() const throw(...);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Pokud z nějakého důvodu selže volání funkce zosobnění, není zosobnit klienta a požadavek klienta se provádí v kontextu zabezpečení procesu, ze kterého přišla. Pokud je proces spuštěný jako vysoce privilegovaný účet, nebo jako člen skupiny pro správu, uživatel může být moct provádět akce potvrdí by jinak zakázán. Proto by měl být potvrzen vždy návratovou hodnotu pro tuto funkci.  
  
##  <a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted  
 Volat tuto metodu za účelem testování, pokud `CAccessToken` objekt obsahuje seznam identifikátorů SID s omezeným přístupem.  
  
```
bool IsTokenRestricted() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud objekt obsahuje seznam omezení identifikátory SID, false, pokud nejsou žádná omezení SID nebo metodu nezdaří.  
  
##  <a name="loaduserprofile"></a>CAccessToken::LoadUserProfile  
 Voláním této metody lze načíst profil uživatele přidružený k `CAccessToken` objektu.  
  
```
bool LoadUserProfile() throw(...);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění, dojde k chybě assertion Pokud `CAccessToken` neobsahuje platný token, nebo pokud profilu uživatele již existuje.  
  
##  <a name="logonuser"></a>CAccessToken::LogonUser  
 Volejte tuto metodu pro vytvoření relace přihlášení pro uživatele přidruženého k dané přihlašovací údaje.  
  
```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszUserName`  
 Ukazatel na řetězec ukončené hodnotou null, který určuje uživatelské jméno. Toto je název uživatelského účtu se přihlásit do systému.  
  
 *pszDomain*  
 Ukazatel na řetězec ukončené hodnotou null, který určuje název domény nebo serveru, jehož účet databáze obsahuje `pszUserName` účtu.  
  
 `pszPassword`  
 Ukazatel na řetězec ukončené hodnotou null, který určuje prostého textu heslo pro uživatelský účet zadaný pomocí `pszUserName`.  
  
 *dwLogonType*  
 Určuje typ operace přihlášení k provedení. V tématu [LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184) další podrobnosti.  
  
 *dwLogonProvider*  
 Určuje zprostředkovatele přihlášení. V tématu [LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184) další podrobnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Přístup k tokenu vyplývající z přihlášení bude přidružen `CAccessToken`. Pro tuto metodu za účelem úspěšné `CAccessToken` objekt musí mít oprávnění SE_TCB_NAME, identifikace držitele jako součást základní důvěryhodné počítače. V tématu [LogonUser](http://msdn.microsoft.com/library/windows/desktop/aa378184) Další informace týkající se požadovaná oprávnění.  
  
##  <a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken  
 Volat tuto metodu v rámci server COM, zpracování volání od klienta k chybě při inicializaci z `CAccessToken` s tímto tokenem přístupu z COM klienta.  
  
```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 Určuje masky přístupu, která určuje požadovanou typy přístupu do tokenu přístupu. Tyto typy požadovaný přístup jsou porovnávány s DACL je token k určení, který přistupuje jsou povolen nebo odepřen.  
  
 `bImpersonate`  
 V případě hodnoty true bude aktuální vlákno zosobnit volající klient COM toto volání se po úspěšném dokončení. Když má hodnotu false, otevřou se přístupový token, ale vlákno nebude mít token zosobnění po dokončení toto volání.  
  
 `bOpenAsSelf`  
 Určuje, zda má být provedeno před kontext zabezpečení volání vláken je kontrola přístupu [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) metoda nebo podle kontextu zabezpečení procesu volající vlákno.  
  
 Pokud má parametr hodnotu false, kontrola přístupu se provádí v kontextu zabezpečení pro volající vlákno. Pokud vlákno zosobňuje klienta, může být takový kontext zabezpečení, která procesu klienta. Je-li tento parametr hodnotu true, je kontrola přístupu provedené v kontextu zabezpečení procesu pro volající vlákno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 [CAutoRevertImpersonation třída](../../atl/reference/cautorevertimpersonation-class.md) lze automaticky vracet zosobněnou přístupové tokeny vytvořen nastavením `bImpersonate` příznak, který *true*.  
  
##  <a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken  
 Volat tuto metodu z v rámci serveru pořízení požadavky přes pojmenovaný kanál k chybě při inicializaci `CAccessToken` s tímto tokenem přístupu z klienta.  
  
```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *hPipe*  
 Popisovač pojmenovaný kanál.  
  
 `dwDesiredAccess`  
 Určuje masky přístupu, která určuje požadovanou typy přístupu do tokenu přístupu. Tyto typy požadovaný přístup jsou porovnávány s DACL je token k určení, který přistupuje jsou povolen nebo odepřen.  
  
 `bImpersonate`  
 V případě hodnoty true bude aktuální vlákno zosobnit volající klient kanálu Toto volání se po úspěšném dokončení. Když má hodnotu false, otevřou se přístupový token, ale vlákno nebude mít token zosobnění po dokončení toto volání.  
  
 `bOpenAsSelf`  
 Určuje, zda má být provedeno před kontext zabezpečení volání vláken je kontrola přístupu [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) metoda nebo podle kontextu zabezpečení procesu volající vlákno.  
  
 Pokud má parametr hodnotu false, kontrola přístupu se provádí v kontextu zabezpečení pro volající vlákno. Pokud vlákno zosobňuje klienta, může být takový kontext zabezpečení, která procesu klienta. Je-li tento parametr hodnotu true, je kontrola přístupu provedené v kontextu zabezpečení procesu pro volající vlákno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 [CAutoRevertImpersonation třída](../../atl/reference/cautorevertimpersonation-class.md) lze automaticky vracet zosobněnou přístupové tokeny vytvořen nastavením `bImpersonate` příznak, který *true*.  
  
##  <a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken  
 Volat tuto metodu v rámci serveru zpracování volání od klienta k chybě při inicializaci z `CAccessToken` s tímto tokenem přístupu z klienta.  
  
```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *BindingHandle*  
 Popisovač vazby na serveru, který představuje vazbu ke klientovi.  
  
 `dwDesiredAccess`  
 Určuje masky přístupu, která určuje požadovanou typy přístupu do tokenu přístupu. Tyto typy požadovaný přístup jsou porovnávány s DACL je token k určení, který přistupuje jsou povolen nebo odepřen.  
  
 `bImpersonate`  
 V případě hodnoty true bude aktuální vlákno zosobnit volající klient toto volání se po úspěšném dokončení. Když má hodnotu false, otevřou se přístupový token, ale vlákno nebude mít token zosobnění po dokončení toto volání.  
  
 `bOpenAsSelf`  
 Určuje, zda má být provedeno před kontext zabezpečení volání vláken je kontrola přístupu [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) metoda nebo podle kontextu zabezpečení procesu volající vlákno.  
  
 Pokud má parametr hodnotu false, kontrola přístupu se provádí v kontextu zabezpečení pro volající vlákno. Pokud vlákno zosobňuje klienta, může být takový kontext zabezpečení, která procesu klienta. Je-li tento parametr hodnotu true, je kontrola přístupu provedené v kontextu zabezpečení procesu pro volající vlákno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 [CAutoRevertImpersonation třída](../../atl/reference/cautorevertimpersonation-class.md) lze automaticky vracet zosobněnou přístupové tokeny vytvořen nastavením `bImpersonate` příznak, který *true*.  
  
##  <a name="openthreadtoken"></a>CAccessToken::OpenThreadToken  
 Voláním této metody lze nastavit úroveň zosobnění a potom inicializujte `CAccessToken` s tokenem z dané vlákno.  
  
```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 Určuje masky přístupu, která určuje požadovanou typy přístupu do tokenu přístupu. Tyto typy požadovaný přístup jsou porovnávány s DACL je token k určení, který přistupuje jsou povolen nebo odepřen.  
  
 `bImpersonate`  
 V případě hodnoty true bude vlákno ponechány na úroveň zosobnění požadovaný po dokončení této metody. Když má hodnotu false, bude vlákno obnovit jeho původní úroveň zosobnění.  
  
 `bOpenAsSelf`  
 Určuje, zda má být provedeno před kontext zabezpečení volání vláken je kontrola přístupu [GetThreadToken](http://msdn.microsoft.com/library/windows/desktop/ms683182) metoda nebo podle kontextu zabezpečení procesu volající vlákno.  
  
 Pokud má parametr hodnotu false, kontrola přístupu se provádí v kontextu zabezpečení pro volající vlákno. Pokud vlákno zosobňuje klienta, může být takový kontext zabezpečení, která procesu klienta. Je-li tento parametr hodnotu true, je kontrola přístupu provedené v kontextu zabezpečení procesu pro volající vlákno.  
  
 `sil`  
 Určuje [SECURITY_IMPERSONATION_LEVEL](http://msdn.microsoft.com/library/windows/desktop/aa379572) výčtového typu, který poskytuje úroveň zosobnění tokenu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 `OpenThreadToken`je podobná [CAccessToken::GetThreadToken](#getthreadtoken), ale nastaví úroveň zosobnění před inicializací `CAccessToken` z vlákna přístupový token.  
  
 [CAutoRevertImpersonation třída](../../atl/reference/cautorevertimpersonation-class.md) lze automaticky vracet zosobněnou přístupové tokeny vytvořen nastavením `bImpersonate` příznak, který *true*.  
  
##  <a name="privilegecheck"></a>CAccessToken::PrivilegeCheck  
 Voláním této metody lze zjistit, zda jsou zadané sady oprávnění povoleno **CAccessToken** objektu.  
  
```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
     bool* pbResult) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *RequiredPrivileges*  
 Ukazatel na [PRIVILEGE_SET](http://msdn.microsoft.com/library/windows/desktop/aa379307) struktury.  
  
 *pbResult*  
 Nastaví metodu k ukazatel na hodnotu označující, zda je povoleno některého nebo všech oprávnění k zadané v `CAccessToken` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Když `PrivilegeCheck` návratu **atributy** členem všech [LUID_AND_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379263) struktura je nastavena na SE_PRIVILEGE_USED_FOR_ACCESS, pokud je povoleno odpovídající oprávnění. Tato metoda volá [PrivilegeCheck](http://msdn.microsoft.com/library/windows/desktop/aa379304) Win32 funkce.  
  
##  <a name="revert"></a>CAccessToken::Revert  
 Volejte tuto metodu za účelem zastavení podprocesu pomocí token zosobnění.  
  
```
bool Revert(HANDLE hThread = NULL) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hThread`  
 Zpracování na vlákno se obnovit z zosobnění. Pokud *hThread* má hodnotu NULL, se předpokládá, že aktuální vlákno.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Reverzním zosobnění tokenů lze provést automaticky [CAutoRevertImpersonation třída](../../atl/reference/cautorevertimpersonation-class.md).  
  
##  <a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl  
 Volat tuto metodu a nastavit výchozí seznam DACL `CAccessToken` objektu.  
  
```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rDacl`  
 Nový výchozí [CDacl třída](../../atl/reference/cdacl-class.md) informace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí hodnota je seznam DACL ho ZAMEZUJE DACL, který se používá ve výchozím nastavení při vytvoření nových objektů s Tento token přístupu v platnosti.  
  
##  <a name="setowner"></a>CAccessToken::SetOwner  
 Volat tuto metodu a nastavit vlastníka `CAccessToken` objektu.  
  
```
bool SetOwner(const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 [Identifikační číslo volané stanice třída](../../atl/reference/csid-class.md) objekt obsahující informace vlastníka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Vlastník je výchozí vlastníka, který se používá pro nové objekty vytvořené během tohoto tokenu přístupu je v platnosti.  
  
##  <a name="setprimarygroup"></a>CAccessToken::SetPrimaryGroup  
 Volat tuto metodu a nastavit primární skupiny `CAccessToken` objektu.  
  
```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSid`  
 [Identifikační číslo volané stanice třída](../../atl/reference/csid-class.md) objekt obsahující informace o primární skupině.  
  
### <a name="return-value"></a>Návratová hodnota  
 Při úspěchu vrátí hodnotu true, při neúspěchu hodnotu false.  
  
### <a name="remarks"></a>Poznámky  
 Primární skupiny je skupina výchozí pro nové objekty vytvořené během tohoto tokenu přístupu je v platnosti.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka ATLSecurity](../../visual-cpp-samples.md)   
 [Přístupové tokeny](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Přehled třídy](../../atl/atl-class-overview.md)
