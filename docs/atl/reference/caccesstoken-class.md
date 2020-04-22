---
title: Třída CAccessToken
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
ms.openlocfilehash: f7a2ee2f9d633c1ed743621eec5b2f7cc04c0e0b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748824"
---
# <a name="caccesstoken-class"></a>Třída CAccessToken

Tato třída je obálka pro přístupový token.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAccessToken
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAccessToken::~CAccessToken](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAccessToken::Připojit](#attach)|Volání této metody převzít vlastnictví popisovače daného tokenu přístupu.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Volání této metody k určení, pokud je `CAccessToken` povolena zadaná identifikátor SID v objektu.|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Volání této metody k vytvoření nového tokenu přístupu zosobnění.|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Volání této metody k vytvoření nového primárního tokenu.|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Volání této metody k vytvoření nového procesu spuštěného `CAccessToken` v kontextu zabezpečení uživatele reprezentovaného objektem.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Volání této metody k vytvoření `CAccessToken` nového, omezený objekt.|
|[CAccessToken::Detach](#detach)|Volání této metody odvolat vlastnictví přístupového tokenu.|
|[CAccessToken::DisablePrivilege](#disableprivilege)|Volání této metody zakázat `CAccessToken` oprávnění v objektu.|
|[CAccessToken::DisablePrivileges](#disableprivileges)|Volání této metody zakázat jedno nebo `CAccessToken` více oprávnění v objektu.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Volání této metody povolit `CAccessToken` oprávnění v objektu.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Volání této metody povolit jedno nebo `CAccessToken` více oprávnění v objektu.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Volání této metody `CAccessToken` vrátit objektu výchozí DACL.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Volání této metody `CAccessToken` získat objekt rovná přístupový token v platnosti pro aktuální vlákno.|
|[CAccessToken::GetGroups](#getgroups)|Volání této metody `CAccessToken` vrátit skupiny tokenů objektu.|
|[CAccessToken::GetHandle](#gethandle)|Volání této metody k načtení popisovače přístupového tokenu.|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Volání této metody získat úroveň zosobnění z přístupového tokenu.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Volání této metody získat ID přihlašovací relace `CAccessToken` přidružené k objektu.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Volání této metody získat přihlašovací IDENTIFIKÁTOR SID přidružené k objektu. `CAccessToken`|
|[CAccessToken::GetOwner](#getowner)|Volání této metody získat vlastníka `CAccessToken` přidružené k objektu.|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Volání této metody získat primární skupiny přidružené k objektu. `CAccessToken`|
|[CAccessToken::GetPrivileges](#getprivileges)|Volání této metody získat oprávnění spojená s objektem. `CAccessToken`|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Volání této metody k `CAccessToken` inicializaci s přístupový token z daného procesu.|
|[CAccessToken::GetProfile](#getprofile)|Volání této metody získat popisovač ukazuje na `CAccessToken` profil uživatele přidružené k objektu.|
|[CAccessToken::GetSource](#getsource)|Volání této metody získat zdroj `CAccessToken` objektu.|
|[CAccessToken::GetStatistics](#getstatistics)|Volání této metody získat informace `CAccessToken` spojené s objektem.|
|[CAccessToken::Id getterminalservicessessionid](#getterminalservicessessionid)|Volání této metody získat ID relace Terminálové služby přidružené k objektu. `CAccessToken`|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Volání této metody k `CAccessToken` inicializaci s token z daného vlákna.|
|[CAccessToken::GetTokenId](#gettokenid)|Volání této metody získat ID tokenu přidružené k objektu. `CAccessToken`|
|[CAccessToken::GetType](#gettype)|Volání této metody získat typ `CAccessToken` tokenu objektu.|
|[CAccessToken::GetUser](#getuser)|Volání této metody k identifikaci `CAccessToken` uživatele přidruženého k objektu.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Volání této metody získat popisovač ukazuje na `CAccessToken` profil uživatele přidružené k objektu.|
|[CAccessToken::Zosobnit](#impersonate)|Volání této metody přiřadit zosobnění `CAccessToken` vlákno.|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Volání této metody povolit volající vlákno zosobnit kontext zabezpečení přihlášeného uživatele.|
|[CAccessToken::IsTokenrestricted](#istokenrestricted)|Volání této metody k `CAccessToken` testování, pokud objekt obsahuje seznam zakázaných identifikátorů SID.|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Volání této metody načíst profil `CAccessToken` uživatele přidružené k objektu.|
|[CAccessToken::LogonUser](#logonuser)|Volání této metody k vytvoření přihlašovací relace pro uživatele přidružené k dané pověření.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Volání této metody z v rámci serveru COM zpracování volání `CAccessToken` z klienta inicializovat s přístupový token z klienta COM.|
|[CAccessToken::OpenNamedPipeDToken](#opennamedpipeclienttoken)|Volání této metody ze serveru s požadavky přes pojmenovaný kanál `CAccessToken` k inicializaci s přístupový token z klienta.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Volání této metody ze serveru zpracování volání z klienta RPC inicializovat `CAccessToken` s přístupový token z klienta.|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Volání této metody nastavit úroveň zosobnění a `CAccessToken` potom inicializovat s token z daného vlákna.|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Volání této metody k určení, zda zadaná `CAccessToken` sada oprávnění jsou povoleny v objektu.|
|[CAccessToken::Vrátit zpět](#revert)|Volání této metody zastavit vlákno, které používá token zosobnění.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Volání této metody nastavit výchozí DACL objektu. `CAccessToken`|
|[CAccessToken::SetOwner](#setowner)|Volání této metody nastavit vlastníka objektu. `CAccessToken`|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Volání této metody nastavit primární `CAccessToken` skupinu objektu.|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/win32/SecAuthZ/access-tokens) je objekt, který popisuje kontext zabezpečení procesu nebo vlákna a je přidělen každému uživateli přihlášenému k systému Windows.

Úvod k modelu řízení přístupu v systému Windows najdete v tématu [Řízení přístupu](/windows/win32/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="caccesstokenattach"></a><a name="attach"></a>CAccessToken::Připojit

Volání této metody převzít vlastnictví popisovače daného tokenu přístupu.

```cpp
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Parametry

*hToken*<br/>
Popisovač přístupového tokenu.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k chybě `CAccessToken` kontrolního výrazu, pokud objekt již vlastní přístupový token.

## <a name="caccesstokencaccesstoken"></a><a name="dtor"></a>CAccessToken::~CAccessToken

Destruktor.

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

## <a name="caccesstokenchecktokenmembership"></a><a name="checktokenmembership"></a>CAccessToken::CheckTokenMembership

Volání této metody k určení, pokud je `CAccessToken` povolena zadaná identifikátor SID v objektu.

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Odkaz na objekt [třídy CSid.](../../atl/reference/csid-class.md)

*pbIsMember*<br/>
Ukazatel na proměnnou, která přijímá výsledky kontroly.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Metoda `CheckTokenMembership` kontroluje přítomnost SID v uživateli a skupiny SID přístupového tokenu. Pokud je k dispozici identifikátor SID a má atribut SE_GROUP_ENABLED, *pbIsMember* je nastavena na hodnotu TRUE; v opačném případě je nastavena na hodnotu FALSE.

V sestavení chodu dojde k chybě kontrolního výrazu, pokud *pbIsMember* není platný ukazatel.

> [!NOTE]
> Objekt `CAccessToken` musí být token zosobnění a nikoli primární token.

## <a name="caccesstokencreateimpersonationtoken"></a><a name="createimpersonationtoken"></a>CAccessToken::CreateImpersonationToken

Volání této metody k vytvoření přístupového tokenu zosobnění.

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Parametry

*Pimp*<br/>
Ukazatel na `CAccessToken` nový objekt.

*sil*<br/>
Určuje [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) typ s výčtem, který poskytuje úroveň zosobnění nového tokenu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

`CreateImpersonationToken`volá [DuplicateToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetoken) k vytvoření nového tokenu zosobnění.

## <a name="caccesstokencreateprimarytoken"></a><a name="createprimarytoken"></a>CAccessToken::CreatePrimaryToken

Volání této metody k vytvoření nového primárního tokenu.

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPri*<br/>
Ukazatel na `CAccessToken` nový objekt.

*dwDesiredAccess*<br/>
Určuje požadovaná přístupová práva pro nový token. Výchozí MAXIMUM_ALLOWED požaduje všechna přístupová práva, která jsou platná pro volajícího. Další informace o přístupových právech najdete v tématu [Přístupová práva a masky přístupu.](/windows/win32/SecAuthZ/access-rights-and-access-masks)

*atributy pToken*<br/>
Ukazatel na [strukturu SECURITY_ATTRIBUTES,](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) která určuje popisovač zabezpečení pro nový token a určuje, zda podřízené procesy mohou token dědit. Pokud *pTokenAttributes* je NULL, token získá výchozí popisovač zabezpečení a popisovač nelze zdědit.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

`CreatePrimaryToken`volá [DuplicateTokenEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex) k vytvoření nového primárního tokenu.

## <a name="caccesstokencreateprocessasuser"></a><a name="createprocessasuser"></a>CAccessToken::CreateProcessAsUser

Volání této metody k vytvoření nového procesu spuštěného `CAccessToken` v kontextu zabezpečení uživatele reprezentovaného objektem.

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

*pNázev_aplikace*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který určuje modul, který má být spuštěn. Tento parametr nemusí být null.

*pCommandLine*<br/>
Ukazatel na řetězec s nulovým ukončením, který určuje příkazový řádek, který má být spuštěn.

*pInformace o procesu*<br/>
Ukazatel na [PROCESS_INFORMATION strukturu,](/windows/win32/api/processthreadsapi/ns-processthreadsapi-process_information) která obdrží identifikační informace o novém procesu.

*pStartupInfo*<br/>
Ukazatel na strukturu [STARTUPINFO,](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfow) která určuje, jak by se mělo zobrazit hlavní okno pro nový proces.

*dwCreationFlags*<br/>
Určuje další příznaky, které řídí třídu priority a vytvoření procesu. Seznam příznaků naleznete v seznamu příznaků ve funkci [Win32 CreateProcessAsUser.](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw)

*bLoadProfile*<br/>
Pokud TRUE, profil uživatele je načten s [LoadUserProfile](/windows/win32/api/userenv/nf-userenv-loaduserprofilew).

*pProcessAttributes*<br/>
Ukazatel na [strukturu SECURITY_ATTRIBUTES,](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) která určuje popisovač zabezpečení pro nový proces a určuje, zda podřízené procesy mohou dědit vrácený popisovač. Pokud *pProcessAttributes* je NULL, proces získá výchozí popisovač zabezpečení a popisovač nelze zdědit.

*atributy pThreadAttributes*<br/>
Ukazatel na [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) strukturu, která určuje popisovač zabezpečení pro nové vlákno a určuje, zda podřízené procesy mohou dědit vrácený popisovač. Pokud *pThreadAttributes* je NULL, vlákno získá výchozí popisovač zabezpečení a popisovač nelze zdědit.

*bZdědit*<br/>
Označuje, zda nový proces dědí popisovače z volajícího procesu. Pokud TRUE, každý dědičný otevřený popisovač v procesu volání je zděděn novým procesem. Zděděné popisovače mají stejnou hodnotu a přístupová oprávnění jako původní popisovače.

*pCurrentDirectory*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který určuje aktuální jednotku a adresář pro nový proces. Řetězec musí být úplná cesta, která obsahuje písmeno jednotky. Pokud je tento parametr null, nový proces bude mít stejnou aktuální jednotku a adresář jako volající proces.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

`CreateProcessAsUser`Používá `CreateProcessAsUser` funkci Win32 k vytvoření nového procesu, který běží `CAccessToken` v kontextu zabezpečení uživatele reprezentovaného objektem. Viz popis [CreateProcessAsUser](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessasuserw) funkce pro úplnou diskusi o požadované parametry.

Aby byla tato metoda `CAccessToken` úspěšná, musí být objekt obsahovat oprávnění AssignPrimaryToken (pokud se nejedná o omezený token) a oprávnění IncreaseQuota.

## <a name="caccesstokencreaterestrictedtoken"></a><a name="createrestrictedtoken"></a>CAccessToken::CreateRestrictedToken

Volání této metody k vytvoření `CAccessToken` nového, omezený objekt.

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Parametry

*token uomezenín*<br/>
Nový, omezený `CAccessToken` objekt.

*SidsChcete-li zakázat*<br/>
Objekt, `CTokenGroups` který určuje pouze odepřít identifikátory SID.

*SidsToRestrict*<br/>
Objekt, `CTokenGroups` který určuje omezující identifikátory SID.

*OprávněníkaKOdstranění*<br/>
Objekt, `CTokenPrivileges` který určuje oprávnění k odstranění v tokenu s omezeným přístupem. Výchozí nastavení vytvoří prázdný objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

`CreateRestrictedToken`používá [CreateRestrictedToken](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) Win32 funkce k `CAccessToken` vytvoření nového objektu, s omezeními.

> [!IMPORTANT]
> Při `CreateRestrictedToken`použití , ujistěte se, že následující: existující token je platný (a není zadán uživatelem) a *SidsToDisable* a *PrivilegesToDelete* jsou platné (a nejsou zadány uživatelem). Pokud metoda vrátí hodnotu NEPRAVDA, zamítnete funkci.

## <a name="caccesstokendetach"></a><a name="detach"></a>CAccessToken::Detach

Volání této metody odvolat vlastnictví přístupového tokenu.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač, `CAccessToken` který byl odpojen.

### <a name="remarks"></a>Poznámky

Tato metoda odvolá `CAccessToken`vlastnictví 's přístupový token.

## <a name="caccesstokendisableprivilege"></a><a name="disableprivilege"></a>CAccessToken::DisablePrivilege

Volání této metody zakázat `CAccessToken` oprávnění v objektu.

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec obsahující oprávnění k `CAccessToken` zakázání v objektu.

*pPreviousState*<br/>
Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokendisableprivileges"></a><a name="disableprivileges"></a>CAccessToken::DisablePrivileges

Volání této metody zakázat jedno nebo `CAccessToken` více oprávnění v objektu.

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*oprávnění*<br/>
Ukazatel na pole řetězců obsahující oprávnění k zakázání `CAccessToken` v objektu.

*pPreviousState*<br/>
Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokenenableprivilege"></a><a name="enableprivilege"></a>CAccessToken::EnablePrivilege

Volání této metody povolit `CAccessToken` oprávnění v objektu.

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec obsahující oprávnění povolit `CAccessToken` v objektu.

*pPreviousState*<br/>
Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokenenableprivileges"></a><a name="enableprivileges"></a>CAccessToken::EnablePrivileges

Volání této metody povolit jedno nebo `CAccessToken` více oprávnění v objektu.

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*oprávnění*<br/>
Ukazatel na pole řetězců obsahující oprávnění, která chcete `CAccessToken` v objektu povolit.

*pPreviousState*<br/>
Ukazatel na `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokengetdefaultdacl"></a><a name="getdefaultdacl"></a>CAccessToken::GetDefaultDacl

Volání této metody `CAccessToken` vrátit objektu výchozí DACL.

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl*<br/>
Ukazatel na objekt [třídy CDacl,](../../atl/reference/cdacl-class.md) který obdrží výchozí seznam DACL objektu. `CAccessToken`

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byl obnoven výchozí seznam DACL, jinak NEPRAVDA.

## <a name="caccesstokengeteffectivetoken"></a><a name="geteffectivetoken"></a>CAccessToken::GetEffectiveToken

Volání této metody `CAccessToken` získat objekt rovná přístupový token v platnosti pro aktuální vlákno.

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu jsou porovnány s seznamem DACL tokenu k určení, které přístupy jsou uděleny nebo odepřeny.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokengetgroups"></a><a name="getgroups"></a>CAccessToken::GetGroups

Volání této metody `CAccessToken` vrátit skupiny tokenů objektu.

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSkupiny*<br/>
Ukazatel na objekt [třídy CTokenGroups,](../../atl/reference/ctokengroups-class.md) který obdrží informace o skupině.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokengethandle"></a><a name="gethandle"></a>CAccessToken::GetHandle

Volání této metody k načtení popisovače přístupového tokenu.

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač `CAccessToken` přístupového tokenu objektu.

## <a name="caccesstokengetimpersonationlevel"></a><a name="getimpersonationlevel"></a>CAccessToken::GetImpersonationLevel

Volání této metody získat úroveň zosobnění z přístupového tokenu.

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Parametry

*úroveň zosobnění*<br/>
Ukazatel na [typ výčtu SECURITY_IMPERSONATION_LEVEL,](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) který obdrží informace o úrovni zosobnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokengetlogonsessionid"></a><a name="getlogonsessionid"></a>CAccessToken::GetLogonSessionId

Volání této metody získat ID přihlašovací relace `CAccessToken` přidružené k objektu.

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid*<br/>
Ukazatel na [luid,](/windows/win32/api/winnt/ns-winnt-luid) který obdrží ID přihlašovací relace.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k chybě kontrolního *výrazu, pokud je pluid* neplatnou hodnotou.

## <a name="caccesstokengetlogonsid"></a><a name="getlogonsid"></a>CAccessToken::GetLogonSid

Volání této metody získat přihlašovací IDENTIFIKÁTOR SID přidružené k objektu. `CAccessToken`

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na objekt [třídy CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k chybě kontrolního výrazu, pokud *pSid* je neplatná hodnota.

## <a name="caccesstokengetowner"></a><a name="getowner"></a>CAccessToken::GetOwner

Volání této metody získat vlastníka `CAccessToken` přidružené k objektu.

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na objekt [třídy CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Vlastník je ve výchozím nastavení nastaven na všechny objekty vytvořené v době, kdy je tento přístupový token v platnosti.

## <a name="caccesstokengetprimarygroup"></a><a name="getprimarygroup"></a>CAccessToken::GetPrimaryGroup

Volání této metody získat primární skupiny přidružené k objektu. `CAccessToken`

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na objekt [třídy CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Skupina je ve výchozím nastavení nastavena na všechny objekty vytvořené v době, kdy je tento přístupový token v platnosti.

## <a name="caccesstokengetprivileges"></a><a name="getprivileges"></a>CAccessToken::GetPrivileges

Volání této metody získat oprávnění spojená s objektem. `CAccessToken`

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPrivileges*<br/>
Ukazatel na objekt [třídy CTokenPrivileges,](../../atl/reference/ctokenprivileges-class.md) který obdrží oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokengetprocesstoken"></a><a name="getprocesstoken"></a>CAccessToken::GetProcessToken

Volání této metody k `CAccessToken` inicializaci s přístupový token z daného procesu.

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu jsou porovnány s seznamem DACL tokenu k určení, které přístupy jsou uděleny nebo odepřeny.

*hProces*<br/>
Zpracování procesu, jehož přístupový token je otevřen. Pokud je použita výchozí hodnota NULL, použije se aktuální proces.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Volá funkci [OpenProcessToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32.

## <a name="caccesstokengetprofile"></a><a name="getprofile"></a>CAccessToken::GetProfile

Volání této metody získat popisovač ukazuje na `CAccessToken` profil uživatele přidružené k objektu.

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač odkazující na profil uživatele nebo hodnotu NULL, pokud neexistuje žádný profil.

## <a name="caccesstokengetsource"></a><a name="getsource"></a>CAccessToken::GetSource

Volání této metody získat zdroj `CAccessToken` objektu.

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Parametry

*pZdroj*<br/>
Ukazatel na [TOKEN_SOURCE](/windows/win32/api/winnt/ns-winnt-token_source) strukturu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokengetstatistics"></a><a name="getstatistics"></a>CAccessToken::GetStatistics

Volání této metody získat informace `CAccessToken` spojené s objektem.

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Parametry

*pStatistiky*<br/>
Ukazatel na [TOKEN_STATISTICS](/windows/win32/api/winnt/ns-winnt-token_statistics) strukturu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokengetterminalservicessessionid"></a><a name="getterminalservicessessionid"></a>CAccessToken::Id getterminalservicessessionid

Volání této metody získat ID relace Terminálové služby přidružené k objektu. `CAccessToken`

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Parametry

*pdwSessionId*<br/>
ID relace Terminálové služby.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokengetthreadtoken"></a><a name="getthreadtoken"></a>CAccessToken::GetThreadToken

Volání této metody k `CAccessToken` inicializaci s token z daného vlákna.

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu jsou porovnány s seznamem DACL tokenu k určení, které přístupy jsou uděleny nebo odepřeny.

*hVlákno*<br/>
Popisovač podprocesu, jehož přístupový token je otevřen.

*bOpenAsSelf*<br/>
Označuje, zda má být provedena kontrola přístupu proti `GetThreadToken` kontextu zabezpečení vlákna volajícího metody nebo proti kontextu zabezpečení procesu volajícího vlákna.

Pokud je tento parametr FALSE, kontrola přístupu se provádí pomocí kontextu zabezpečení pro volající vlákno. Pokud vlákno je zosobnění klienta, tento kontext zabezpečení může být klientský proces. Pokud je tento parametr TRUE, kontrola přístupu se provádí pomocí kontextu zabezpečení procesu pro volající vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokengettokenid"></a><a name="gettokenid"></a>CAccessToken::GetTokenId

Volání této metody získat ID tokenu přidružené k objektu. `CAccessToken`

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid*<br/>
Ukazatel na [LUID,](/windows/win32/api/winnt/ns-winnt-luid) který obdrží ID tokenu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokengettype"></a><a name="gettype"></a>CAccessToken::GetType

Volání této metody získat typ `CAccessToken` tokenu objektu.

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Parametry

*pTyp*<br/>
Adresa [proměnné TOKEN_TYPE,](/windows/win32/api/winnt/ne-winnt-token_type) která při úspěchu obdrží typ tokenu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Typ výčtu TOKEN_TYPE obsahuje hodnoty, které rozlišují mezi primárním tokenem a tokenem zosobnění.

## <a name="caccesstokengetuser"></a><a name="getuser"></a>CAccessToken::GetUser

Volání této metody k identifikaci `CAccessToken` uživatele přidruženého k objektu.

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSid*<br/>
Ukazatel na objekt [třídy CSid.](../../atl/reference/csid-class.md)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="caccesstokenhkeycurrentuser"></a><a name="hkeycurrentuser"></a>CAccessToken::HKeyCurrentUser

Volání této metody získat popisovač ukazuje na `CAccessToken` profil uživatele přidružené k objektu.

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač odkazující na profil uživatele nebo hodnotu NULL, pokud neexistuje žádný profil.

## <a name="caccesstokenimpersonate"></a><a name="impersonate"></a>CAccessToken::Zosobnit

Volání této metody přiřadit zosobnění `CAccessToken` vlákno.

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*hVlákno*<br/>
Zpracovat vlákno přiřadit token zosobnění. Tento popisovač musí být otevřen s TOKEN_IMPERSONATE přístupová práva. Pokud *hThread* je NULL, metoda způsobí, že vlákno přestat používat token zosobnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k chybě `CAccessToken` kontrolního výrazu, pokud nemá platný ukazatel na token.

[Třída CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) slouží k automatickému vrácení zosobněných přístupových tokenů.

## <a name="caccesstokenimpersonateloggedonuser"></a><a name="impersonateloggedonuser"></a>CAccessToken::ImpersonateLoggedOnUser

Volání této metody povolit volající vlákno zosobnit kontext zabezpečení přihlášeného uživatele.

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

> [!IMPORTANT]
> Pokud volání funkce zosobnění z nějakého důvodu selže, klient není zosobněn a požadavek klienta je proveden v kontextu zabezpečení procesu, ze kterého bylo volání provedeno. Pokud je proces spuštěn jako vysoce privilegovaný účet nebo jako člen skupiny pro správu, uživatel může být schopen provádět akce, které by jinak byly zakázány. Proto vrácená hodnota pro tuto funkci by měla být vždy potvrzena.

## <a name="caccesstokenistokenrestricted"></a><a name="istokenrestricted"></a>CAccessToken::IsTokenrestricted

Volání této metody k `CAccessToken` testování, pokud objekt obsahuje seznam zakázaných identifikátorů SID.

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud objekt obsahuje seznam omezujících identifikátorů SID, NEPRAVDA, pokud neexistují žádná omezující identifikátory SID nebo pokud se metoda nezdaří.

## <a name="caccesstokenloaduserprofile"></a><a name="loaduserprofile"></a>CAccessToken::LoadUserProfile

Volání této metody načíst profil `CAccessToken` uživatele přidružené k objektu.

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

V sestaveních ladění dojde k chybě `CAccessToken` kontrolního výrazu, pokud neobsahuje platný token nebo pokud profil uživatele již existuje.

## <a name="caccesstokenlogonuser"></a><a name="logonuser"></a>CAccessToken::LogonUser

Volání této metody k vytvoření přihlašovací relace pro uživatele přidružené k dané pověření.

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
Ukazatel na řetězec s ukončeným hodnotou null, který určuje uživatelské jméno. Toto je název uživatelského účtu, ke který se chcete přihlásit.

*pszDoména*<br/>
Ukazatel na řetězec s nulovým ukončením, který určuje název domény nebo serveru, jehož databáze účtů obsahuje účet *pszUserName.*

*pszPassword*<br/>
Ukazatel na řetězec s nulovým ukončením, který určuje heslo ve stavu prostého textu pro uživatelský účet určený *pszUserName*.

*dwLogonType*<br/>
Určuje typ operace přihlášení, která má být vyvedena. Další podrobnosti naleznete v tématu [LogonUser.](/windows/win32/api/winbase/nf-winbase-logonuserw)

*dwLogonProvider*<br/>
Určuje zprostředkovatele přihlášení. Další podrobnosti naleznete v tématu [LogonUser.](/windows/win32/api/winbase/nf-winbase-logonuserw)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Přístupový token vyplývající z přihlášení bude přidružen `CAccessToken`k . Aby byla tato metoda `CAccessToken` úspěšná, musí být objekt SE_TCB_NAME oprávněnía, identifikující držitele jako součást důvěryhodné ho režii počítače. Další informace týkající se požadovaných oprávnění naleznete v tématu [LogonUser.](/windows/win32/api/winbase/nf-winbase-logonuserw)

## <a name="caccesstokenopencomclienttoken"></a><a name="opencomclienttoken"></a>CAccessToken::OpenCOMClientToken

Volání této metody z v rámci serveru COM zpracování volání `CAccessToken` z klienta inicializovat s přístupový token z klienta COM.

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu jsou porovnány s seznamem DACL tokenu k určení, které přístupy jsou uděleny nebo odepřeny.

*bZidit*<br/>
Pokud true, aktuální vlákno bude zosobnit volajícího klienta COM, pokud toto volání úspěšně dokončeno. Pokud false, přístupový token bude otevřen, ale vlákno nebude mít token zosobnění po dokončení tohoto volání.

*bOpenAsSelf*<br/>
Označuje, zda má být provedena kontrola přístupu proti kontextu zabezpečení vlákna volajícího metodu [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) nebo proti kontextu zabezpečení procesu pro volající vlákno.

Pokud je tento parametr FALSE, kontrola přístupu se provádí pomocí kontextu zabezpečení pro volající vlákno. Pokud vlákno je zosobnění klienta, tento kontext zabezpečení může být klientský proces. Pokud je tento parametr TRUE, kontrola přístupu se provádí pomocí kontextu zabezpečení procesu pro volající vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

[Třídu CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) lze použít k automatickému vrácení zosobněných přístupových tokenů vytvořených nastavením příznaku *bImpersonate* na hodnotu TRUE.

## <a name="caccesstokenopennamedpipeclienttoken"></a><a name="opennamedpipeclienttoken"></a>CAccessToken::OpenNamedPipeDToken

Volání této metody ze serveru s požadavky přes pojmenovaný kanál `CAccessToken` k inicializaci s přístupový token z klienta.

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hPotrubí*<br/>
Popisovač pojmenovaného kanálu.

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu jsou porovnány s seznamem DACL tokenu k určení, které přístupy jsou uděleny nebo odepřeny.

*bZidit*<br/>
Pokud true, aktuální vlákno bude zosobnit volajícího klienta kanálu, pokud toto volání úspěšně dokončena. Pokud false, přístupový token bude otevřen, ale vlákno nebude mít token zosobnění po dokončení tohoto volání.

*bOpenAsSelf*<br/>
Označuje, zda má být provedena kontrola přístupu proti kontextu zabezpečení vlákna volajícího metodu [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) nebo proti kontextu zabezpečení procesu pro volající vlákno.

Pokud je tento parametr FALSE, kontrola přístupu se provádí pomocí kontextu zabezpečení pro volající vlákno. Pokud vlákno je zosobnění klienta, tento kontext zabezpečení může být klientský proces. Pokud je tento parametr TRUE, kontrola přístupu se provádí pomocí kontextu zabezpečení procesu pro volající vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

[Třídu CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) lze použít k automatickému vrácení zosobněných přístupových tokenů vytvořených nastavením příznaku *bImpersonate* na hodnotu TRUE.

## <a name="caccesstokenopenrpcclienttoken"></a><a name="openrpcclienttoken"></a>CAccessToken::OpenRPCClientToken

Volání této metody ze serveru zpracování volání z klienta RPC inicializovat `CAccessToken` s přístupový token z klienta.

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
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu jsou porovnány s seznamem DACL tokenu k určení, které přístupy jsou uděleny nebo odepřeny.

*bZidit*<br/>
Pokud true, aktuální vlákno bude zosobnit volajícího klienta RPC, pokud toto volání úspěšně dokončeno. Pokud false, přístupový token bude otevřen, ale vlákno nebude mít token zosobnění po dokončení tohoto volání.

*bOpenAsSelf*<br/>
Označuje, zda má být provedena kontrola přístupu proti kontextu zabezpečení vlákna volajícího metodu [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) nebo proti kontextu zabezpečení procesu pro volající vlákno.

Pokud je tento parametr FALSE, kontrola přístupu se provádí pomocí kontextu zabezpečení pro volající vlákno. Pokud vlákno je zosobnění klienta, tento kontext zabezpečení může být klientský proces. Pokud je tento parametr TRUE, kontrola přístupu se provádí pomocí kontextu zabezpečení procesu pro volající vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

[Třídu CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) lze použít k automatickému vrácení zosobněných přístupových tokenů vytvořených nastavením příznaku *bImpersonate* na hodnotu TRUE.

## <a name="caccesstokenopenthreadtoken"></a><a name="openthreadtoken"></a>CAccessToken::OpenThreadToken

Volání této metody nastavit úroveň zosobnění a `CAccessToken` potom inicializovat s token z daného vlákna.

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje masku přístupu, která určuje požadované typy přístupu k přístupovému tokenu. Tyto požadované typy přístupu jsou porovnány s seznamem DACL tokenu k určení, které přístupy jsou uděleny nebo odepřeny.

*bZidit*<br/>
Pokud TRUE, vlákno zůstane na požadované úrovni zosobnění po dokončení této metody. Pokud false, vlákno se vrátí na původní úroveň zosobnění.

*bOpenAsSelf*<br/>
Označuje, zda má být provedena kontrola přístupu proti kontextu zabezpečení vlákna volajícího metodu [GetThreadToken](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) nebo proti kontextu zabezpečení procesu pro volající vlákno.

Pokud je tento parametr FALSE, kontrola přístupu se provádí pomocí kontextu zabezpečení pro volající vlákno. Pokud vlákno je zosobnění klienta, tento kontext zabezpečení může být klientský proces. Pokud je tento parametr TRUE, kontrola přístupu se provádí pomocí kontextu zabezpečení procesu pro volající vlákno.

*sil*<br/>
Určuje [SECURITY_IMPERSONATION_LEVEL](/windows/win32/api/winnt/ne-winnt-security_impersonation_level) typ s výčtem, který poskytuje úroveň zosobnění tokenu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

`OpenThreadToken`je podobný [CAccessToken::GetThreadToken](#getthreadtoken), ale nastaví úroveň zosobnění před inicializací `CAccessToken` z přístupového tokenu vlákna.

[Třídu CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) lze použít k automatickému vrácení zosobněných přístupových tokenů vytvořených nastavením příznaku *bImpersonate* na hodnotu TRUE.

## <a name="caccesstokenprivilegecheck"></a><a name="privilegecheck"></a>CAccessToken::PrivilegeCheck

Volání této metody k určení, zda zadaná `CAccessToken` sada oprávnění jsou povoleny v objektu.

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Parametry

*Požadovaná oprávnění*<br/>
Ukazatel na [PRIVILEGE_SET](/windows/win32/api/winnt/ns-winnt-privilege_set) strukturu.

*pbVýsledek*<br/>
Ukazatel na hodnotu, kterou metoda nastaví k označení, zda `CAccessToken` jsou v objektu povolena některá nebo všechna zadaná oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Když `PrivilegeCheck` vrátí `Attributes` člen každé [LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes) struktury je nastavena na SE_PRIVILEGE_USED_FOR_ACCESS, pokud je povolena odpovídající oprávnění. Tato metoda volá funkci [PrivilegeCheck](/windows/win32/api/securitybaseapi/nf-securitybaseapi-privilegecheck) Win32.

## <a name="caccesstokenrevert"></a><a name="revert"></a>CAccessToken::Vrátit zpět

Volání této metody zastavit vlákno z použití tokenu zosobnění.

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*hVlákno*<br/>
Zpracovat vlákno vrátit z zosobnění. Pokud *hThread* je NULL, předpokládá se aktuální vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Reverze zosobnění tokeny lze provést automaticky s [CAutoRevertImpersonation Class](../../atl/reference/cautorevertimpersonation-class.md).

## <a name="caccesstokensetdefaultdacl"></a><a name="setdefaultdacl"></a>CAccessToken::SetDefaultDacl

Volání této metody nastavit výchozí DACL objektu. `CAccessToken`

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Parametry

*rDacl*<br/>
Nové výchozí informace [o třídě CDacl.](../../atl/reference/cdacl-class.md)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Výchozí seznam DACL je seznam DACL, který se používá ve výchozím nastavení při vytváření nových objektů s tímto přístupovým tokenem.

## <a name="caccesstokensetowner"></a><a name="setowner"></a>CAccessToken::SetOwner

Volání této metody nastavit vlastníka objektu. `CAccessToken`

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[CSid Class](../../atl/reference/csid-class.md) objekt obsahující informace vlastníka.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Vlastník je výchozí vlastník, který se používá pro nové objekty vytvořené v době, kdy je tento přístupový token v platnosti.

## <a name="caccesstokensetprimarygroup"></a><a name="setprimarygroup"></a>CAccessToken::SetPrimaryGroup

Volání této metody nastavit primární `CAccessToken` skupinu objektu.

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[CSid Class](../../atl/reference/csid-class.md) objekt obsahující informace o primární skupině.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Primární skupina je výchozí skupinou pro nové objekty vytvořené v době, kdy je tento přístupový token v platnosti.

## <a name="see-also"></a>Viz také

[Ukázka zabezpečení ATL](../../overview/visual-cpp-samples.md)<br/>
[Přístupové tokeny](/windows/win32/SecAuthZ/access-tokens)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
