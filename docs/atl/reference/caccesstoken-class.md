---
title: CAccessToken – třída
ms.date: 07/02/2019
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
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
ms.openlocfilehash: fa50282f3aa1f4db3ebf6306fa9dc3dab1311d1b
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915903"
---
# <a name="caccesstoken-class"></a>CAccessToken – třída

Tato třída je obálkou pro přístupový token.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAccessToken
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAccessToken::~CAccessToken](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAccessToken:: Attach](#attach)|Voláním této metody převezmete vlastnictví daného popisovače přístupového tokenu.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Voláním této metody určíte, zda je v `CAccessToken` objektu povolen zadaný identifikátor SID.|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Voláním této metody vytvoříte nový přístupový token zosobnění.|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Voláním této metody vytvoříte nový primární token.|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Zavolejte tuto metodu pro vytvoření nového procesu spuštěného v kontextu zabezpečení uživatele reprezentovaného `CAccessToken` objektem.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Zavolejte tuto metodu pro vytvoření nového, omezeného `CAccessToken` objektu.|
|[CAccessToken::D etach](#detach)|Voláním této metody odvoláte vlastnictví přístupového tokenu.|
|[CAccessToken::DisablePrivilege](#disableprivilege)|Voláním této metody zakážete oprávnění v `CAccessToken` objektu.|
|[CAccessToken::DisablePrivileges](#disableprivileges)|Voláním této metody zakážete jedno nebo více oprávnění v `CAccessToken` objektu.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Voláním této metody povolíte oprávnění v `CAccessToken` objektu.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Voláním této metody povolíte v `CAccessToken` objektu jedno nebo více oprávnění.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Voláním této metody vrátíte `CAccessToken` výchozí seznam DACL objektu.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Zavolejte tuto metodu pro získání `CAccessToken` objektu, který se rovná přístupovému tokenu v platném pro aktuální vlákno.|
|[CAccessToken:: GetGroups](#getgroups)|Voláním této metody vrátíte `CAccessToken` skupiny tokenů objektu.|
|[CAccessToken:: GetHandle](#gethandle)|Voláním této metody Načtěte popisovač přístupového tokenu.|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Voláním této metody získáme úroveň zosobnění z přístupového tokenu.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Voláním této metody získáte ID přihlašovací relace přidružené `CAccessToken` k objektu.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Voláním této metody získáme přihlašovací identifikátor SID přidružený `CAccessToken` k objektu.|
|[CAccessToken::GetOwner](#getowner)|Voláním této metody získáte vlastníka přidruženého `CAccessToken` k objektu.|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Voláním této metody získáte primární skupinu přidruženou `CAccessToken` k objektu.|
|[CAccessToken:: getprivileges](#getprivileges)|Voláním této metody získáte oprávnění přidružená `CAccessToken` k objektu.|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Voláním této metody inicializujete `CAccessToken` pomocí přístupového tokenu z daného procesu.|
|[CAccessToken:: GetProfile](#getprofile)|Voláním této metody získáte popisovač odkazující na profil uživatele přidružený `CAccessToken` k objektu.|
|[CAccessToken:: GetSource](#getsource)|Voláním této metody načtete zdroj `CAccessToken` objektu.|
|[CAccessToken:: getstatistics](#getstatistics)|Voláním této metody získáte informace spojené s `CAccessToken` objektem.|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Voláním této metody získáte ID relace Terminálové služby přidružené k danému `CAccessToken` objektu.|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Zavolejte tuto metodu pro inicializaci `CAccessToken` s tokenem z daného vlákna.|
|[CAccessToken::GetTokenId](#gettokenid)|Voláním této metody získáte ID tokenu přidruženého `CAccessToken` k objektu.|
|[CAccessToken:: GetType](#gettype)|Voláním této metody získáte typ `CAccessToken` tokenu objektu.|
|[CAccessToken::GetUser](#getuser)|Zavolejte tuto metodu k identifikaci uživatele přidruženého `CAccessToken` k objektu.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Voláním této metody získáte popisovač odkazující na profil uživatele přidružený `CAccessToken` k objektu.|
|[CAccessToken:: Impersonate](#impersonate)|Voláním této metody přiřadíte zosobnění `CAccessToken` k vláknu.|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Zavolejte tuto metodu, pokud chcete volajícímu vláknu dovolit zosobnit kontext zabezpečení přihlášeného uživatele.|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Voláním této metody otestujete, `CAccessToken` zda objekt obsahuje seznam omezených identifikátorů SID.|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Voláním této metody načtete profil uživatele přidružený `CAccessToken` k objektu.|
|[CAccessToken::LogonUser](#logonuser)|Voláním této metody vytvoříte přihlašovací relaci pro uživatele přidruženého k zadaným přihlašovacím údajům.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Volání této metody ze serveru com, který zpracovává volání od klienta za účelem inicializace `CAccessToken` přístupového tokenu z klienta modelu COM.|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Volání této metody ze serveru, který přijímá požadavky přes pojmenovaný kanál k inicializaci `CAccessToken` s přístupovým tokenem z klienta.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Voláním této metody ze serveru, který zpracovává volání z klienta RPC pro inicializaci `CAccessToken` s přístupovým tokenem z klienta.|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Voláním této metody nastavíte úroveň zosobnění a potom inicializujete `CAccessToken` token z daného vlákna.|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Voláním této metody určíte, zda je v `CAccessToken` objektu povolena zadaná sada oprávnění.|
|[CAccessToken:: Revert](#revert)|Voláním této metody zastavíte vlákno, které používá token zosobnění.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Voláním této metody nastavíte výchozí seznam DACL `CAccessToken` objektu.|
|[CAccessToken::SetOwner](#setowner)|Voláním této metody nastavíte vlastníka `CAccessToken` objektu.|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Voláním této metody nastavte primární skupinu `CAccessToken` objektu.|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/desktop/SecAuthZ/access-tokens) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen každému uživateli přihlášenému do systému Windows.

Úvod do modelu řízení přístupu v systému Windows naleznete v tématu [Access Control](/windows/desktop/SecAuthZ/access-control) v Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="attach"></a>CAccessToken:: Attach

Voláním této metody převezmete vlastnictví daného popisovače přístupového tokenu.

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Parametry

*hToken*<br/>
Popisovač přístupového tokenu.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, pokud `CAccessToken` objekt již obsahuje vlastnictví přístupového tokenu.

##  <a name="dtor"></a>CAccessToken:: ~ CAccessToken

Destruktor.

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership

Voláním této metody určíte, zda je v `CAccessToken` objektu povolen zadaný identifikátor SID.

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Odkaz na objekt [třídy CSID](../../atl/reference/csid-class.md)

*pbIsMember*<br/>
Ukazatel na proměnnou, která přijímá výsledky kontroly.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

`CheckTokenMembership` Metoda zkontroluje přítomnost identifikátoru SID v identifikátorech SID uživatelů a skupin přístupového tokenu. Pokud je k dispozici identifikátor SID a má atribut SE_GROUP_ENABLED, je *pbIsMember* nastaven na hodnotu true. v opačném případě je nastaveno na FALSE.

V sestavení ladění dojde k chybě kontrolního výrazu, pokud *pbIsMember* není platný ukazatel.

> [!NOTE]
>  `CAccessToken` Objekt musí být token pro zosobnění, nikoli primární token.

##  <a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken

Voláním této metody vytvoříte přístupový token zosobnění.

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Parametry

*pImp*<br/>
Ukazatel na nový `CAccessToken` objekt.

*sil*<br/>
Určuje [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-security_impersonation_level) Výčtový typ, který poskytuje úroveň zosobnění nového tokenu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

`CreateImpersonationToken`volá [volání metody duplicatetoken](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) k vytvoření nového tokenu zosobnění.

##  <a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken

Voláním této metody vytvoříte nový primární token.

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPri*<br/>
Ukazatel na nový `CAccessToken` objekt.

*dwDesiredAccess*<br/>
Určuje požadovaná přístupová práva k novému tokenu. Výchozí MAXIMUM_ALLOWED vyžaduje všechna přístupová práva platná pro daného volajícího. Další informace o přístupových právech najdete v tématu [přístupová práva a masky přístupu](/windows/desktop/SecAuthZ/access-rights-and-access-masks) .

*pTokenAttributes*<br/>
Ukazatel na strukturu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , která určuje popisovač zabezpečení pro nový token a určuje, zda mohou podřízené procesy zdědit token. Pokud má *pTokenAttributes* hodnotu null, token Získá výchozí popisovač zabezpečení a popisovač nelze dědit.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

`CreatePrimaryToken`volá [DuplicateTokenEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) k vytvoření nového primárního tokenu.

##  <a name="createprocessasuser"></a>CAccessToken:: CreateProcessAsUser

Zavolejte tuto metodu pro vytvoření nového procesu spuštěného v kontextu zabezpečení uživatele reprezentovaného `CAccessToken` objektem.

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

*pApplicationName*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje modul, který má být spuštěn. Tento parametr nemůže mít hodnotu NULL.

*pCommandLine*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje příkazový řádek, který má být spuštěn.

*pProcessInformation*<br/>
Ukazatel na [strukturu PROCESS_INFORMATION](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information) , která přijímá identifikační informace o novém procesu.

*pStartupInfo*<br/>
Ukazatel na strukturu [startupinfo](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-startupinfoa) , která určuje, jak se má hlavní okno pro nový proces zobrazit.

*dwCreationFlags*<br/>
Určuje další příznaky, které řídí třídu priorit a vytváření procesu. Seznam příznaků najdete v [CreateProcessAsUser](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessasusera) funkce Win32.

*bLoadProfile*<br/>
Při hodnotě TRUE se profil uživatele načte pomocí [LoadUserProfile nastavenými](/windows/desktop/api/userenv/nf-userenv-loaduserprofilea).

*pProcessAttributes*<br/>
Ukazatel na strukturu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , která určuje popisovač zabezpečení pro nový proces a určuje, zda podřízené procesy mohou zdědit vrácený popisovač. Pokud má *pProcessAttributes* hodnotu null, proces Získá výchozí popisovač zabezpečení a popisovač nelze dědit.

*pThreadAttributes*<br/>
Ukazatel na strukturu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) , která určuje popisovač zabezpečení pro nové vlákno a určuje, zda podřízené procesy mohou zdědit vrácený popisovač. Pokud má *pThreadAttributes* hodnotu null, vlákno získá výchozí popisovač zabezpečení a popisovač nelze dědit.

*bInherit*<br/>
Určuje, zda nový proces dědí popisovače z volajícího procesu. Je-li nastavena hodnota TRUE, je každý dědičný otevřený popisovač v volajícím procesu děděn novým procesem. Zděděné popisovače mají stejnou hodnotu a přístupová oprávnění jako původní popisovače.

*pCurrentDirectory*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje aktuální jednotku a adresář pro nový proces. Řetězec musí být úplná cesta, která obsahuje písmeno jednotky. Pokud má tento parametr hodnotu NULL, nový proces bude mít stejnou aktuální jednotku a adresář jako volající proces.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

`CreateProcessAsUser`pomocí funkce `CAccessToken` Win32 vytvoří nový proces, který běží v kontextu zabezpečení uživatele reprezentovaného objektem. `CreateProcessAsUser` Úplnou diskuzi o požadovaných parametrech najdete v popisu funkce [CreateProcessAsUser](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessasusera) .

Aby tato metoda byla úspěšná, `CAccessToken` objekt musí obsahovat AssignPrimaryToken (Pokud se nejedná o omezený token) a oprávnění IncreaseQuota.

##  <a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken

Zavolejte tuto metodu pro vytvoření nového, omezeného `CAccessToken` objektu.

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Parametry

*pRestrictedToken*<br/>
Nový objekt s omezením `CAccessToken` .

*SidsToDisable*<br/>
`CTokenGroups` Objekt, který určuje identifikátory SID jen pro zamítnutí.

*SidsToRestrict*<br/>
`CTokenGroups` Objekt, který určuje omezení počtu identifikátorů SID.

*PrivilegesToDelete*<br/>
`CTokenPrivileges` Objekt, který určuje oprávnění, která se mají odstranit v omezeném tokenu. Výchozí hodnota vytvoří prázdný objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

`CreateRestrictedToken`pomocí funkce [CreateRestrictedToken](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) Win32 vytvoří nový `CAccessToken` objekt s omezeními.

> [!IMPORTANT]
>  Při použití `CreateRestrictedToken`nástroje zajistěte následující: existující token je platný (a nezadáte ho uživatelem) a *SidsToDisable* a *PrivilegesToDelete* jsou platné (a nezadal uživatel). Pokud metoda vrátí hodnotu FALSE, funkce odepřít.

##  <a name="detach"></a>CAccessToken::D etach

Voláním této metody odvoláte vlastnictví přístupového tokenu.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač `CAccessToken` , který byl odpojen.

### <a name="remarks"></a>Poznámky

Tato metoda odvolá `CAccessToken`vlastnictví přístupového tokenu.

##  <a name="disableprivilege"></a>CAccessToken::D isablePrivilege

Voláním této metody zakážete oprávnění v `CAccessToken` objektu.

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec obsahující oprávnění, které má být zakázáno v `CAccessToken` objektu.

*pPreviousState*<br/>
Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="disableprivileges"></a>CAccessToken::D isablePrivileges

Voláním této metody zakážete jedno nebo více oprávnění v `CAccessToken` objektu.

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Ukazatel na pole řetězců obsahující oprávnění, která mají být v `CAccessToken` objektu zakázána.

*pPreviousState*<br/>
Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="enableprivilege"></a>CAccessToken::EnablePrivilege

Voláním této metody povolíte oprávnění v `CAccessToken` objektu.

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec obsahující oprávnění pro povolení v `CAccessToken` objektu.

*pPreviousState*<br/>
Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="enableprivileges"></a>CAccessToken::EnablePrivileges

Voláním této metody povolíte v `CAccessToken` objektu jedno nebo více oprávnění.

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Ukazatel na pole řetězců obsahující oprávnění, která mají být v `CAccessToken` objektu povolena.

*pPreviousState*<br/>
Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl

Voláním této metody vrátíte `CAccessToken` výchozí seznam DACL objektu.

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl*<br/>
Ukazatel na objekt [třídy CDacl](../../atl/reference/cdacl-class.md) , který `CAccessToken` Získá výchozí seznam DACL objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu pravda, pokud byl výchozí seznam DACL obnoven, jinak FALSE.

##  <a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken

Zavolejte tuto metodu pro získání `CAccessToken` objektu, který se rovná přístupovému tokenu v platném pro aktuální vlákno.

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu se porovnají se seznamem DACL tokenu, aby bylo možné zjistit, které přístupy jsou uděleny nebo odepřeny.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="getgroups"></a>CAccessToken:: GetGroups

Voláním této metody vrátíte `CAccessToken` skupiny tokenů objektu.

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Parametry

*pGroups*<br/>
Ukazatel na objekt [třídy CTokenGroups](../../atl/reference/ctokengroups-class.md) , který obdrží informace o skupině.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="gethandle"></a>CAccessToken:: GetHandle

Voláním této metody Načtěte popisovač přístupového tokenu.

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač `CAccessToken` přístupového tokenu objektu.

##  <a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel

Voláním této metody získáme úroveň zosobnění z přístupového tokenu.

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Parametry

*pImpersonationLevel*<br/>
Ukazatel na typ výčtu [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-security_impersonation_level) , který získá informace o úrovni zosobnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId

Voláním této metody získáte ID přihlašovací relace přidružené `CAccessToken` k objektu.

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid*<br/>
Ukazatel na identifikátor [LUID](/windows/desktop/api/winnt/ns-winnt-luid) , který získá ID přihlašovací relace.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, pokud *pluid* je neplatná hodnota.

##  <a name="getlogonsid"></a>CAccessToken::GetLogonSid

Voláním této metody získáme přihlašovací identifikátor SID přidružený `CAccessToken` k objektu.

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na objekt [třídy CSID](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, pokud *PSID má* je neplatná hodnota.

##  <a name="getowner"></a>CAccessToken:: GetOwner

Voláním této metody získáte vlastníka přidruženého `CAccessToken` k objektu.

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na objekt [třídy CSID](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení se vlastník nastavuje u všech objektů vytvořených v době, kdy je tento přístupový token platný.

##  <a name="getprimarygroup"></a>CAccessToken:: getprimary

Voláním této metody získáte primární skupinu přidruženou `CAccessToken` k objektu.

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na objekt [třídy CSID](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Skupina je standardně nastavená na všech objektech vytvořených v době, kdy je tento přístupový token platný.

##  <a name="getprivileges"></a>CAccessToken:: getprivileges

Voláním této metody získáte oprávnění přidružená `CAccessToken` k objektu.

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPrivileges*<br/>
Ukazatel na objekt [třídy CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md) , který získá oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="getprocesstoken"></a>CAccessToken::GetProcessToken

Voláním této metody inicializujete `CAccessToken` pomocí přístupového tokenu z daného procesu.

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu se porovnají se seznamem DACL tokenu, aby bylo možné zjistit, které přístupy jsou uděleny nebo odepřeny.

*hProcess*<br/>
Zpracujte proces, jehož přístupový token je otevřený. Pokud je použita výchozí hodnota NULL, je použit aktuální proces.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Zavolá funkci [OpenProcessToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32.

##  <a name="getprofile"></a>CAccessToken:: GetProfile

Voláním této metody získáte popisovač odkazující na profil uživatele přidružený `CAccessToken` k objektu.

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač ukazující na profil uživatele nebo hodnotu NULL, pokud žádný profil neexistuje.

##  <a name="getsource"></a>CAccessToken:: GetSource

Voláním této metody načtete zdroj `CAccessToken` objektu.

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSource*<br/>
Ukazatel na strukturu [TOKEN_SOURCE](/windows/desktop/api/winnt/ns-winnt-token_source) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="getstatistics"></a>CAccessToken:: getstatistics

Voláním této metody získáte informace spojené s `CAccessToken` objektem.

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Parametry

*pStatistics*<br/>
Ukazatel na strukturu [TOKEN_STATISTICS](/windows/desktop/api/winnt/ns-winnt-token_statistics) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="getterminalservicessessionid"></a>CAccessToken::GetTerminalServicesSessionId

Voláním této metody získáte ID relace Terminálové služby přidružené k danému `CAccessToken` objektu.

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Parametry

*pdwSessionId*<br/>
ID relace Terminálové služby.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="getthreadtoken"></a>CAccessToken::GetThreadToken

Zavolejte tuto metodu pro inicializaci `CAccessToken` s tokenem z daného vlákna.

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu se porovnají se seznamem DACL tokenu, aby bylo možné zjistit, které přístupy jsou uděleny nebo odepřeny.

*hThread*<br/>
Zpracování vlákna, u kterého je otevřen přístupový token.

*bOpenAsSelf*<br/>
Označuje, zda má být provedena kontroly přístupu proti kontextu zabezpečení vlákna, které volá `GetThreadToken` metodu, nebo proti kontextu zabezpečení procesu volajícího vlákna.

Pokud má tento parametr hodnotu FALSE, kontroly přístupu se provádí pomocí kontextu zabezpečení volajícího vlákna. Pokud vlákno zosobňuje klienta, může to být tento kontext zabezpečení klientským procesem. Je-li tento parametr TRUE, je provedena kontroly přístupu pomocí kontextu zabezpečení procesu pro volající vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="gettokenid"></a>CAccessToken::GetTokenId

Voláním této metody získáte ID tokenu přidruženého `CAccessToken` k objektu.

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid*<br/>
Ukazatel na identifikátor [LUID](/windows/desktop/api/winnt/ns-winnt-luid) , který získá ID tokenu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="gettype"></a>CAccessToken:: GetType

Voláním této metody získáte typ `CAccessToken` tokenu objektu.

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Parametry

*pType*<br/>
Adresa proměnné [TOKEN_TYPE](/windows/desktop/api/winnt/ne-winnt-token_type) , která po úspěchu obdrží typ tokenu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Typ výčtu TOKEN_TYPE obsahuje hodnoty, které rozlišují primární token a token zosobnění.

##  <a name="getuser"></a>CAccessToken:: GetUser

Zavolejte tuto metodu k identifikaci uživatele přidruženého `CAccessToken` k objektu.

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na objekt [třídy CSID](../../atl/reference/csid-class.md) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

##  <a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser

Voláním této metody získáte popisovač odkazující na profil uživatele přidružený `CAccessToken` k objektu.

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač ukazující na profil uživatele nebo hodnotu NULL, pokud žádný profil neexistuje.

##  <a name="impersonate"></a>CAccessToken:: Impersonate

Voláním této metody přiřadíte zosobnění `CAccessToken` k vláknu.

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*hThread*<br/>
Zpracujte vlákno, kterému chcete přiřadit token zosobnění. Tento popisovač se musí otevřít s přístupovými právy TOKEN_IMPERSONATE. Pokud má *hThread* hodnotu null, metoda způsobí, že vlákno přestane používat token zosobnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, `CAccessToken` Pokud nemá platný ukazatel na token.

[Třída CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se dá použít k automatickému vrácení zosobněných přístupových tokenů.

##  <a name="impersonateloggedonuser"></a>  CAccessToken::ImpersonateLoggedOnUser

Zavolejte tuto metodu, pokud chcete volajícímu vláknu dovolit zosobnit kontext zabezpečení přihlášeného uživatele.

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

> [!IMPORTANT]
>  Pokud se volání funkce zosobnění z nějakého důvodu nepovede, klient není zosobněn a požadavek klienta se provede v kontextu zabezpečení procesu, ze kterého bylo volání provedeno. Pokud je proces spuštěný jako vysoce privilegovaný účet nebo jako člen skupiny pro správu, může být uživatel schopný provádět akce, které by jinak nepovolovaly. Proto by měla být vrácená hodnota pro tuto funkci vždy potvrzena.

##  <a name="istokenrestricted"></a>CAccessToken::IsTokenRestricted

Voláním této metody otestujete, `CAccessToken` zda objekt obsahuje seznam omezených identifikátorů SID.

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud objekt obsahuje seznam omezení SID, FALSE, pokud nejsou k dispozici žádné identifikátory SID nebo pokud se metoda nezdařila.

##  <a name="loaduserprofile"></a>CAccessToken:: LoadUserProfile nastavenými

Voláním této metody načtete profil uživatele přidružený `CAccessToken` k objektu.

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

V sestavení ladění dojde k chybě kontrolního výrazu, pokud `CAccessToken` neobsahuje platný token, nebo pokud profil uživatele již existuje.

##  <a name="logonuser"></a>CAccessToken:: LogonUser

Voláním této metody vytvoříte přihlašovací relaci pro uživatele přidruženého k zadaným přihlašovacím údajům.

```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*pszUserName*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje uživatelské jméno. Toto je název uživatelského účtu, ke kterému se chcete přihlásit.

*pszDomain*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje název domény nebo serveru, jehož databáze účtů obsahuje účet *pszUserName* .

*pszPassword*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje heslo k nešifrovaným textům uživatelského účtu zadaného parametrem *pszUserName*.

*dwLogonType*<br/>
Určuje typ operace přihlášení, která se má provést. Další podrobnosti naleznete v tématu [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) .

*dwLogonProvider*<br/>
Určuje poskytovatele přihlášení. Další podrobnosti naleznete v tématu [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Přístupový token, který je výsledkem přihlášení, bude přidružen `CAccessToken`k. Aby tato metoda byla `CAccessToken` úspěšná, musí objekt obsahovat oprávnění SE_TCB_NAME a identifikovat držitele jako součást základu důvěryhodného počítače. Další informace o požadovaných oprávněních naleznete v tématu [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) .

##  <a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken

Volání této metody ze serveru com, který zpracovává volání od klienta za účelem inicializace `CAccessToken` přístupového tokenu z klienta modelu COM.

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu se porovnají se seznamem DACL tokenu, aby bylo možné zjistit, které přístupy jsou uděleny nebo odepřeny.

*bImpersonate*<br/>
Pokud má hodnotu TRUE, aktuální vlákno zosobní volajícího klienta modelu COM, pokud se toto volání úspěšně dokončí. Pokud má hodnotu FALSE, bude přístupový token otevřený, ale po dokončení tohoto volání nebude vlákno mít token zosobnění.

*bOpenAsSelf*<br/>
Označuje, zda má být provedena kontroly přístupu proti kontextu zabezpečení vlákna, které volá metodu [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) , nebo proti kontextu zabezpečení procesu volajícího vlákna.

Pokud má tento parametr hodnotu FALSE, kontroly přístupu se provádí pomocí kontextu zabezpečení volajícího vlákna. Pokud vlákno zosobňuje klienta, může to být tento kontext zabezpečení klientským procesem. Je-li tento parametr TRUE, je provedena kontroly přístupu pomocí kontextu zabezpečení procesu pro volající vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

[Třída CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se dá použít k automatickému vrácení zosobněných přístupových tokenů vytvořených nastavením příznaku *bImpersonate* na hodnotu true.

##  <a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeClientToken

Volání této metody ze serveru, který přijímá požadavky přes pojmenovaný kanál k inicializaci `CAccessToken` s přístupovým tokenem z klienta.

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hPipe*<br/>
Popisovač k pojmenovanému kanálu.

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu se porovnají se seznamem DACL tokenu, aby bylo možné zjistit, které přístupy jsou uděleny nebo odepřeny.

*bImpersonate*<br/>
Pokud má hodnotu TRUE, aktuální vlákno zosobní klienta volajícího kanálu, pokud se toto volání úspěšně dokončí. Pokud má hodnotu FALSE, bude přístupový token otevřený, ale po dokončení tohoto volání nebude vlákno mít token zosobnění.

*bOpenAsSelf*<br/>
Označuje, zda má být provedena kontroly přístupu proti kontextu zabezpečení vlákna, které volá metodu [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) , nebo proti kontextu zabezpečení procesu volajícího vlákna.

Pokud má tento parametr hodnotu FALSE, kontroly přístupu se provádí pomocí kontextu zabezpečení volajícího vlákna. Pokud vlákno zosobňuje klienta, může to být tento kontext zabezpečení klientským procesem. Je-li tento parametr TRUE, je provedena kontroly přístupu pomocí kontextu zabezpečení procesu pro volající vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

[Třída CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se dá použít k automatickému vrácení zosobněných přístupových tokenů vytvořených nastavením příznaku *bImpersonate* na hodnotu true.

##  <a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken

Voláním této metody ze serveru, který zpracovává volání z klienta RPC pro inicializaci `CAccessToken` s přístupovým tokenem z klienta.

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*BindingHandle*<br/>
Popisovač vazby na serveru, který představuje vazbu na klienta.

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu se porovnají se seznamem DACL tokenu, aby bylo možné zjistit, které přístupy jsou uděleny nebo odepřeny.

*bImpersonate*<br/>
Pokud má hodnotu TRUE, aktuální vlákno zosobní volajícího klienta RPC, pokud se toto volání úspěšně dokončí. Pokud má hodnotu FALSE, bude přístupový token otevřený, ale po dokončení tohoto volání nebude vlákno mít token zosobnění.

*bOpenAsSelf*<br/>
Označuje, zda má být provedena kontroly přístupu proti kontextu zabezpečení vlákna, které volá metodu [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) , nebo proti kontextu zabezpečení procesu volajícího vlákna.

Pokud má tento parametr hodnotu FALSE, kontroly přístupu se provádí pomocí kontextu zabezpečení volajícího vlákna. Pokud vlákno zosobňuje klienta, může to být tento kontext zabezpečení klientským procesem. Je-li tento parametr TRUE, je provedena kontroly přístupu pomocí kontextu zabezpečení procesu pro volající vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

[Třída CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se dá použít k automatickému vrácení zosobněných přístupových tokenů vytvořených nastavením příznaku *bImpersonate* na hodnotu true.

##  <a name="openthreadtoken"></a>CAccessToken:: OpenThreadToken –

Voláním této metody nastavíte úroveň zosobnění a potom inicializujete `CAccessToken` token z daného vlákna.

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu se porovnají se seznamem DACL tokenu, aby bylo možné zjistit, které přístupy jsou uděleny nebo odepřeny.

*bImpersonate*<br/>
Je-li nastavena hodnota TRUE, vlákno bude po dokončení této metody ponecháno na požadované úrovni zosobnění. V případě hodnoty FALSE se vlákno vrátí na původní úroveň zosobnění.

*bOpenAsSelf*<br/>
Označuje, zda má být provedena kontroly přístupu proti kontextu zabezpečení vlákna, které volá metodu [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) , nebo proti kontextu zabezpečení procesu volajícího vlákna.

Pokud má tento parametr hodnotu FALSE, kontroly přístupu se provádí pomocí kontextu zabezpečení volajícího vlákna. Pokud vlákno zosobňuje klienta, může to být tento kontext zabezpečení klientským procesem. Je-li tento parametr TRUE, je provedena kontroly přístupu pomocí kontextu zabezpečení procesu pro volající vlákno.

*sil*<br/>
Určuje [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-security_impersonation_level) Výčtový typ, který poskytuje úroveň zosobnění tokenu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

`OpenThreadToken`je podobný jako [CAccessToken:: GetThreadToken](#getthreadtoken), ale nastaví úroveň zosobnění před inicializací `CAccessToken` z přístupového tokenu vlákna.

[Třída CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) se dá použít k automatickému vrácení zosobněných přístupových tokenů vytvořených nastavením příznaku *bImpersonate* na hodnotu true.

##  <a name="privilegecheck"></a>CAccessToken::P rivilegeCheck

Voláním této metody určíte, zda je v `CAccessToken` objektu povolena zadaná sada oprávnění.

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Parametry

*RequiredPrivileges*<br/>
Ukazatel na strukturu [PRIVILEGE_SET](/windows/desktop/api/winnt/ns-winnt-privilege_set) .

*pbResult*<br/>
Ukazatel na hodnotu, kterou metody nastaví, aby označoval, zda jsou v `CAccessToken` objektu povoleny některá nebo všechna zadaná oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Když `PrivilegeCheck` se vrátí `Attributes` , člen každé struktury [LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-luid_and_attributes) se nastaví na SE_PRIVILEGE_USED_FOR_ACCESS, pokud je povolené příslušné oprávnění. Tato metoda volá funkci [PrivilegeCheck](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-privilegecheck) Win32.

##  <a name="revert"></a>CAccessToken:: Revert

Voláním této metody zabráníte vláknu v použití tokenu zosobnění.

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*hThread*<br/>
Zpracování vlákna, které se má vrátit z zosobnění Pokud má *hThread* hodnotu null, předpokládá se aktuální vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Reverze tokenů zosobnění se dá provést automaticky pomocí [třídy CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md).

##  <a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl

Voláním této metody nastavíte výchozí seznam DACL `CAccessToken` objektu.

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Parametry

*rDacl*<br/>
Nové výchozí informace [třídy CDacl](../../atl/reference/cdacl-class.md)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Výchozím seznamem DACL je seznam DACL, který se ve výchozím nastavení používá, když se v tomto důsledku vytvoří nové objekty s tímto tokenem přístupu.

##  <a name="setowner"></a>CAccessToken::SetOwner

Voláním této metody nastavíte vlastníka `CAccessToken` objektu.

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Objekt [třídy CSID](../../atl/reference/csid-class.md) obsahující informace o vlastníkovi

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Vlastníkem je výchozí vlastník, který se používá pro nové objekty vytvořené v době, kdy je tento přístupový token platný.

##  <a name="setprimarygroup"></a>CAccessToken::SetPrimaryGroup

Voláním této metody nastavte primární skupinu `CAccessToken` objektu.

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Objekt [třídy CSID](../../atl/reference/csid-class.md) obsahující informace o primární skupině.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Primární skupina je výchozí skupina pro nové objekty vytvořené v době, kdy je tento přístupový token platný.

## <a name="see-also"></a>Viz také:

[Ukázka ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Přístupové tokeny](/windows/desktop/SecAuthZ/access-tokens)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
