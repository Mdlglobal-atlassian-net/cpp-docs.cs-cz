---
title: Caccesstoken – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: faa715e8f5333a717689d281ccb89bd2369e9929
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661263"
---
# <a name="caccesstoken-class"></a>Caccesstoken – třída

Tato třída představuje obálku pro přístupový token.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

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
|[CAccessToken::Attach](#attach)|Volejte tuto metodu za účelem převzít vlastnictví popisovač token má přístup.|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|Volejte tuto metodu za účelem zjištění, zda zadaný identifikátor SID je povolen v `CAccessToken` objektu.|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|Voláním této metody lze vytvořit nový přístupový token zosobnění.|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|Volejte tuto metodu za účelem vytvoření nové primární tokenu.|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|Volejte tuto metodu za účelem vytvoření nového procesu spuštěného v kontextu zabezpečení uživatele reprezentován `CAccessToken` objektu.|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|Volejte tuto metodu za účelem vytvoření nové, s omezeným přístupem `CAccessToken` objektu.|
|[CAccessToken::Detach](#detach)|Volejte tuto metodu za účelem odvolat vlastnictví přístupový token.|
|[CAccessToken::DisablePrivilege](#disableprivilege)|Voláním této metody lze zakázat oprávnění v `CAccessToken` objektu.|
|[CAccessToken::DisablePrivileges](#disableprivileges)|Voláním této metody lze zakázat jeden nebo více oprávnění v `CAccessToken` objektu.|
|[CAccessToken::EnablePrivilege](#enableprivilege)|Volejte tuto metodu za účelem povolení oprávnění v `CAccessToken` objektu.|
|[CAccessToken::EnablePrivileges](#enableprivileges)|Voláním této metody lze povolit v jedné nebo více oprávnění `CAccessToken` objektu.|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|Voláním této metody vrátit `CAccessToken` objektu výchozí seznam DACL.|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|Volejte tuto metodu za účelem získání `CAccessToken` objekt roven přístupový token pro aktuální vlákno.|
|[CAccessToken::GetGroups](#getgroups)|Voláním této metody vrátit `CAccessToken` objektu skupiny tokenu.|
|[CAccessToken::GetHandle](#gethandle)|Volejte tuto metodu za účelem načtení popisovače do tokenu přístupu.|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|Volejte tuto metodu za účelem získání úroveň zosobnění z přístupového tokenu.|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|Volání této metody k získání ID relace přihlášení přidružené k `CAccessToken` objektu.|
|[CAccessToken::GetLogonSid](#getlogonsid)|Volejte tuto metodu za účelem získání SID přihlášení přidružené k `CAccessToken` objektu.|
|[CAccessToken::GetOwner](#getowner)|Volejte tuto metodu za účelem získání vlastníka přidružené `CAccessToken` objektu.|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|Volejte tuto metodu za účelem získání primární skupiny spojené s `CAccessToken` objektu.|
|[CAccessToken::GetPrivileges](#getprivileges)|Volejte tuto metodu za účelem získání oprávnění přidružených k `CAccessToken` objektu.|
|[CAccessToken::GetProcessToken](#getprocesstoken)|Voláním této metody lze inicializovat `CAccessToken` s tímto tokenem přístupu z daného procesu.|
|[CAccessToken::GetProfile](#getprofile)|Volejte tuto metodu za účelem získání popisovače odkazující na přiřazený profil uživatele `CAccessToken` objektu.|
|[CAccessToken::GetSource](#getsource)|Volejte tuto metodu za účelem získání zdroj `CAccessToken` objektu.|
|[CAccessToken::GetStatistics](#getstatistics)|Volejte tuto metodu za účelem získání informací o související s `CAccessToken` objektu.|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|Volání této metody k získání ID relace Terminálové služby přidružené `CAccessToken` objektu.|
|[CAccessToken::GetThreadToken](#getthreadtoken)|Voláním této metody lze inicializovat `CAccessToken` pomocí tokenu z dané vlákno.|
|[CAccessToken::GetTokenId](#gettokenid)|Volejte tuto metodu za účelem získání tokenu ID přidružené k `CAccessToken` objektu.|
|[CAccessToken::GetType](#gettype)|Volejte tuto metodu za účelem získání tokenu typu `CAccessToken` objektu.|
|[CAccessToken::GetUser](#getuser)|Voláním této metody k identifikaci uživatele přidruženého k `CAccessToken` objektu.|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|Volejte tuto metodu za účelem získání popisovače odkazující na přiřazený profil uživatele `CAccessToken` objektu.|
|[CAccessToken::Impersonate](#impersonate)|Voláním této metody lze přiřadit zosobnění `CAccessToken` ve vlákně.|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|Voláním této metody lze povolit volající vlákno k zosobnění kontextu zabezpečení přihlášeného uživatele.|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|Voláním této metody, který testuje, jestli `CAccessToken` objekt obsahuje seznam identifikátorů SID s omezeným přístupem.|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|Voláním této metody lze načíst profil uživatele přidružené k `CAccessToken` objektu.|
|[CAccessToken::LogonUser](#logonuser)|Volejte tuto metodu za účelem vytvoření relace přihlášení pro uživatele přidruženého k dané přihlašovací údaje.|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|Volejte tuto metodu z v rámci serveru COM zpracování volání od klienta k inicializaci `CAccessToken` pomocí přístupového tokenu z modelu COM klienta.|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|Volejte tuto metodu z v rámci serveru přijímání žádostí přes pojmenovaný kanál se inicializovat `CAccessToken` pomocí přístupového tokenu z klienta.|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|Volejte tuto metodu z v rámci serveru zpracování volání od klienta k inicializaci `CAccessToken` pomocí přístupového tokenu z klienta.|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|Voláním této metody lze nastavit úroveň zosobnění, kterou následně inicializujete `CAccessToken` pomocí tokenu z dané vlákno.|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|Volejte tuto metodu za účelem určení, jestli jsou v povolené zadanou sadu oprávnění `CAccessToken` objektu.|
|[CAccessToken::Revert](#revert)|Volejte tuto metodu za účelem zastavení podprocesu, který se používá token pro zosobnění.|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|Voláním této metody lze nastavit výchozí seznam DACL `CAccessToken` objektu.|
|[CAccessToken::SetOwner](#setowner)|Voláním této metody lze nastavit vlastníka `CAccessToken` objektu.|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|Voláním této metody lze nastavit primární skupiny `CAccessToken` objektu.|

## <a name="remarks"></a>Poznámky

[Přístupový token](/windows/desktop/SecAuthZ/access-tokens) je objekt, který popisuje proces nebo vlákno kontextu zabezpečení a přidělené každému uživateli přihlášení systému Windows.

Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="attach"></a>  CAccessToken::Attach

Volejte tuto metodu za účelem převzít vlastnictví popisovač token má přístup.

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>Parametry

*hToken*<br/>
Popisovač do tokenu přístupu.

### <a name="remarks"></a>Poznámky

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud `CAccessToken` objektu již je vlastnictví přístupový token.

##  <a name="dtor"></a>  Caccesstoken –:: ~ caccesstoken –

Destruktor.

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="checktokenmembership"></a>  CAccessToken::CheckTokenMembership

Volejte tuto metodu za účelem zjištění, zda zadaný identifikátor SID je povolen v `CAccessToken` objektu.

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Odkaz [CSID – třída](../../atl/reference/csid-class.md) objektu.

*pbIsMember*<br/>
Ukazovat na proměnnou, která přijímá výsledky kontroly.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

`CheckTokenMembership` Metoda zkontroluje přítomnost identifikátor SID uživatele a skupiny SID přístupový token. Pokud je k dispozici identifikátor SID a atribut SE_GROUP_ENABLED *pbIsMember* je nastavena na hodnotu TRUE; jinak vrátí hodnotu, je nastavena na hodnotu FALSE.

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud *pbIsMember* není platný ukazatel.

> [!NOTE]
>  `CAccessToken` Objekt musí být token zosobnění a není primární token.

##  <a name="createimpersonationtoken"></a>  CAccessToken::CreateImpersonationToken

Volejte tuto metodu za účelem vytvoření přístupového tokenu zosobnění.

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>Parametry

*pImp*<br/>
Ukazatel na novou `CAccessToken` objektu.

*sil*<br/>
Určuje [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) Výčtový typ, který poskytuje úroveň zosobnění nový token.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

`CreateImpersonationToken` volání [DuplicateToken](https://msdn.microsoft.com/library/windows/desktop/aa446616) vytvořit nový token zosobnění.

##  <a name="createprimarytoken"></a>  CAccessToken::CreatePrimaryToken

Volejte tuto metodu za účelem vytvoření nové primární tokenu.

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPri*<br/>
Ukazatel na novou `CAccessToken` objektu.

*dwDesiredAccess*<br/>
Určuje požadovaný přístupová práva pro nový token. Výchozí MAXIMUM_ALLOWED, požádá o všechna přístupová práva, které jsou platné pro volajícího. Zobrazit [přístupová práva a masek přístup](/windows/desktop/SecAuthZ/access-rights-and-access-masks) pro další práva na přístup.

*pTokenAttributes*<br/>
Ukazatel [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která určuje popisovač zabezpečení pro nový token a určuje, zda podřízených procesů může dědit token. Pokud *pTokenAttributes* má hodnotu NULL, token, který získá výchozí popisovač zabezpečení a nejde ji zdědit popisovač.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

`CreatePrimaryToken` volání [DuplicateTokenEx](https://msdn.microsoft.com/library/windows/desktop/aa446617) k vytvoření nové primární tokenu.

##  <a name="createprocessasuser"></a>  CAccessToken::CreateProcessAsUser

Volejte tuto metodu za účelem vytvoření nového procesu spuštěného v kontextu zabezpečení uživatele reprezentován `CAccessToken` objektu.

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
Ukazatel na řetězec zakončený hodnotou null, který určuje modulu ke spuštění. Tento parametr nemůže mít hodnotu NULL.

*pCommandLine*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje příkazový řádek ke spuštění.

*pProcessInformation*<br/>
Ukazatel [PROCESS_INFORMATION](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_process_information) struktura, která přijímá identifikační informace o nový proces.

*pStartupInfo*<br/>
Ukazatel [OBVYKLE](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_startupinfoa) struktura, která určuje, jak by měl vypadat hlavního okna pro nový proces.

*dwCreationFlags*<br/>
Určuje další příznaky, které řídí s prioritou a vytvoření procesu. Podívat se na funkci Win32 [CreateProcessAsUser](https://msdn.microsoft.com/library/windows/desktop/ms682429) seznam příznaky.

*bLoadProfile*<br/>
Při hodnotě TRUE se načtení profilu uživatele s [LoadUserProfile](/windows/desktop/api/userenv/nf-userenv-loaduserprofilea).

*pProcessAttributes*<br/>
Ukazatel [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která určuje popisovač zabezpečení pro nový proces a určuje, zda podřízené procesy Vrácený popisovač zdědit. Pokud *pProcessAttributes* má hodnotu NULL, proces získá výchozí popisovač zabezpečení a nejde ji zdědit popisovač.

*pThreadAttributes*<br/>
Ukazatel [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která určuje popisovač zabezpečení pro nové vlákno a určuje, zda podřízené procesy Vrácený popisovač zdědit. Pokud *pThreadAttributes* má hodnotu NULL, vlákno získá výchozí popisovač zabezpečení a nejde ji zdědit popisovač.

*bInherit*<br/>
Určuje, zda nový proces zdědí obslužné rutiny z volajícího procesu. Při hodnotě TRUE se každý odvoditelný otevřený popisovač do volajícího procesu přechází na nový proces. Zděděné popisovače mít stejná oprávnění hodnotu a přístupu jako popisovače původní.

*pCurrentDirectory*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje aktuální jednotky a adresář pro nový proces. Řetězec musí být úplná cesta, která obsahuje písmeno jednotky. Pokud má parametr hodnotu NULL, nový proces bude mít stejný aktuální jednotku a adresář jako volající proces.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

`CreateProcessAsUser` používá `CreateProcessAsUser` Win32 funkci, která vytvoří nový proces, na kterém běží v kontextu zabezpečení uživatele reprezentován `CAccessToken` objektu. Viz popis [CreateProcessAsUser](https://msdn.microsoft.com/library/windows/desktop/ms682429) funkce pro úplnou diskusi o požadované parametry.

Pro tuto metodu za účelem úspěšné `CAccessToken` objektu musí obsahovat AssignPrimaryToken (pokud to není omezený token) a IncreaseQuota oprávnění.

##  <a name="createrestrictedtoken"></a>  CAccessToken::CreateRestrictedToken

Volejte tuto metodu za účelem vytvoření nové, s omezeným přístupem `CAccessToken` objektu.

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>Parametry

*pRestrictedToken*<br/>
Nové, s omezením pomocí specifikátoru `CAccessToken` objektu.

*SidsToDisable*<br/>
A `CTokenGroups` objekt, který určuje SID jenom pro odepření.

*SidsToRestrict*<br/>
A `CTokenGroups` objekt, který určuje omezení SID.

*PrivilegesToDelete*<br/>
A `CTokenPrivileges` objekt, který určuje oprávnění k odstranění tokenu s omezeným přístupem. Výchozí hodnota vytvoří prázdný objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

`CreateRestrictedToken` používá [CreateRestrictedToken](https://msdn.microsoft.com/library/windows/desktop/aa446583) funkci Win32 k vytvoření nového `CAccessToken` objektu s omezeními.

> [!IMPORTANT]
>  Při použití `CreateRestrictedToken`, zajistěte následující: existující token je platný (a není zadaný uživatel) a *SidsToDisable* a *PrivilegesToDelete* jsou platné (a není zadaná uživatelem). Pokud metoda vrátí hodnotu FALSE, zakažte funkce.

##  <a name="detach"></a>  CAccessToken::Detach

Volejte tuto metodu za účelem odvolat vlastnictví přístupový token.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač `CAccessToken` které byl odpojen.

### <a name="remarks"></a>Poznámky

Tato metoda odvolá `CAccessToken`jeho vlastnictví přístupový token.

##  <a name="disableprivilege"></a>  CAccessToken::DisablePrivilege

Voláním této metody lze zakázat oprávnění v `CAccessToken` objektu.

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec, který obsahuje oprávnění, aby tak zakázali ve `CAccessToken` objektu.

*pPreviousState*<br/>
Ukazatel `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="disableprivileges"></a>  CAccessToken::DisablePrivileges

Voláním této metody lze zakázat jeden nebo více oprávnění v `CAccessToken` objektu.

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Ukazatel na pole řetězců obsahující oprávnění k zakázání v `CAccessToken` objektu.

*pPreviousState*<br/>
Ukazatel `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="enableprivilege"></a>  CAccessToken::EnablePrivilege

Volejte tuto metodu za účelem povolení oprávnění v `CAccessToken` objektu.

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszPrivilege*<br/>
Ukazatel na řetězec, který obsahuje oprávnění pro povolení v `CAccessToken` objektu.

*pPreviousState*<br/>
Ukazatel `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="enableprivileges"></a>  CAccessToken::EnablePrivileges

Voláním této metody lze povolit v jedné nebo více oprávnění `CAccessToken` objektu.

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*rPrivileges*<br/>
Ukazatel na pole řetězců obsahující oprávnění pro povolení v `CAccessToken` objektu.

*pPreviousState*<br/>
Ukazatel `CTokenPrivileges` objekt, který bude obsahovat předchozí stav oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="getdefaultdacl"></a>  CAccessToken::GetDefaultDacl

Voláním této metody vrátit `CAccessToken` objektu výchozí seznam DACL.

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>Parametry

*pDacl*<br/>
Ukazatel [cdacl – třída](../../atl/reference/cdacl-class.md) objekt, který se zobrazí `CAccessToken` objektu výchozí seznam DACL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud výchozí seznam DACL byl obnovený, FALSE, jinak.

##  <a name="geteffectivetoken"></a>  CAccessToken::GetEffectiveToken

Volejte tuto metodu za účelem získání `CAccessToken` objekt roven přístupový token pro aktuální vlákno.

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje přístupovou maska, která určuje požadované typy přístupu do tokenu přístupu. Tyto požadované typy přístup jsou porovnávány s DACL tokenu k určení, který přístup je udělen nebo odepřen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="getgroups"></a>  CAccessToken::GetGroups

Voláním této metody vrátit `CAccessToken` objektu skupiny tokenu.

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>Parametry

*pGroups*<br/>
Ukazatel [ctokengroups – třída](../../atl/reference/ctokengroups-class.md) objekt, který se zobrazí informace o skupinách.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="gethandle"></a>  CAccessToken::GetHandle

Volejte tuto metodu za účelem načtení popisovače do tokenu přístupu.

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač `CAccessToken` objektu přístupový token.

##  <a name="getimpersonationlevel"></a>  CAccessToken::GetImpersonationLevel

Volejte tuto metodu za účelem získání úroveň zosobnění z přístupového tokenu.

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>Parametry

*pImpersonationLevel*<br/>
Ukazatel [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) typ výčtu, která se zobrazí informace o úrovni zosobnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="getlogonsessionid"></a>  CAccessToken::GetLogonSessionId

Volání této metody k získání ID relace přihlášení přidružené k `CAccessToken` objektu.

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid*<br/>
Ukazatel [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) který se zobrazí ID relace přihlášení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud *pluid* je neplatná hodnota.

##  <a name="getlogonsid"></a>  CAccessToken::GetLogonSid

Volejte tuto metodu za účelem získání SID přihlášení přidružené k `CAccessToken` objektu.

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*psid má*<br/>
Ukazatel [CSID – třída](../../atl/reference/csid-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud *psid má* je neplatná hodnota.

##  <a name="getowner"></a>  CAccessToken::GetOwner

Volejte tuto metodu za účelem získání vlastníka přidružené `CAccessToken` objektu.

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*psid má*<br/>
Ukazatel [CSID – třída](../../atl/reference/csid-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Jako vlastník je nastavena ve výchozím nastavení na všechny objekty vytvořené během Tento přístupový token je v platnosti.

##  <a name="getprimarygroup"></a>  CAccessToken::GetPrimaryGroup

Volejte tuto metodu za účelem získání primární skupiny spojené s `CAccessToken` objektu.

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*psid má*<br/>
Ukazatel [CSID – třída](../../atl/reference/csid-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení na všechny objekty vytvořené během platí tento přístupový token má tato skupina nastavení.

##  <a name="getprivileges"></a>  CAccessToken::GetPrivileges

Volejte tuto metodu za účelem získání oprávnění přidružených k `CAccessToken` objektu.

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>Parametry

*pPrivileges*<br/>
Ukazatel [ctokenprivileges – třída](../../atl/reference/ctokenprivileges-class.md) objekt, který se zobrazí oprávnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="getprocesstoken"></a>  CAccessToken::GetProcessToken

Voláním této metody lze inicializovat `CAccessToken` s tímto tokenem přístupu z daného procesu.

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje přístupovou maska, která určuje požadované typy přístupu do tokenu přístupu. Tyto požadované typy přístup jsou porovnávány s DACL tokenu k určení, který přístup je udělen nebo odepřen.

*hProcess*<br/>
Popisovač procesu, jehož přístupový token je otevřený. Pokud je použita výchozí hodnota NULL, použije se aktuální proces.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Volání [OpenProcessToken](https://msdn.microsoft.com/library/aa379295) funkci Win32.

##  <a name="getprofile"></a>  CAccessToken::GetProfile

Volejte tuto metodu za účelem získání popisovače odkazující na přiřazený profil uživatele `CAccessToken` objektu.

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač odkazující na profil uživatele, nebo hodnota NULL, pokud neexistuje žádný profil.

##  <a name="getsource"></a>  CAccessToken::GetSource

Volejte tuto metodu za účelem získání zdroj `CAccessToken` objektu.

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSource*<br/>
Ukazatel [TOKEN_SOURCE](/windows/desktop/api/winnt/ns-winnt-_token_source) struktury.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="getstatistics"></a>  CAccessToken::GetStatistics

Volejte tuto metodu za účelem získání informací o související s `CAccessToken` objektu.

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>Parametry

*pStatistics*<br/>
Ukazatel [TOKEN_STATISTICS](/windows/desktop/api/winnt/ns-winnt-_token_statistics) struktury.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="getterminalservicessessionid"></a>  CAccessToken::GetTerminalServicesSessionId

Volání této metody k získání ID relace Terminálové služby přidružené `CAccessToken` objektu.

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>Parametry

*pdwSessionId*<br/>
ID relace Terminálové služby.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="getthreadtoken"></a>  CAccessToken::GetThreadToken

Voláním této metody lze inicializovat `CAccessToken` pomocí tokenu z dané vlákno.

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje přístupovou maska, která určuje požadované typy přístupu do tokenu přístupu. Tyto požadované typy přístup jsou porovnávány s DACL tokenu k určení, který přístup je udělen nebo odepřen.

*hThread*<br/>
Popisovač vlákna, jehož přístupový token je otevřený.

*bOpenAsSelf*<br/>
Určuje, zda má být provedeno proti kontextu zabezpečení volající vlákno je kontrola přístupu `GetThreadToken` metoda nebo proti kontextu zabezpečení procesu pro volajícího vlákna.

Pokud má parametr hodnotu FALSE, je provedena kontrola přístupu v kontextu zabezpečení pro volajícího vlákna. Pokud vlákno provádí zosobnění klienta, může být takový kontext zabezpečení, která procesu klienta. Pokud tento parametr má hodnotu TRUE, provádí kontroly přístupu v kontextu zabezpečení procesu pro volajícího vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="gettokenid"></a>  CAccessToken::GetTokenId

Volejte tuto metodu za účelem získání tokenu ID přidružené k `CAccessToken` objektu.

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>Parametry

*pluid*<br/>
Ukazatel [LUID](/windows/desktop/api/winnt/ns-winnt-_luid) který obdrží Token ID.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="gettype"></a>  CAccessToken::GetType

Volejte tuto metodu za účelem získání tokenu typu `CAccessToken` objektu.

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>Parametry

*pType*<br/>
Adresa [TOKEN_TYPE](/windows/desktop/api/winnt/ne-winnt-_token_type) proměnné, která v případě úspěchu, přijímá typ tokenu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Typ výčtu TOKEN_TYPE obsahuje hodnoty, které rozlišovat mezi primární token a token zosobnění.

##  <a name="getuser"></a>  CAccessToken::GetUser

Voláním této metody k identifikaci uživatele přidruženého k `CAccessToken` objektu.

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>Parametry

*psid má*<br/>
Ukazatel [CSID – třída](../../atl/reference/csid-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="hkeycurrentuser"></a>  CAccessToken::HKeyCurrentUser

Volejte tuto metodu za účelem získání popisovače odkazující na přiřazený profil uživatele `CAccessToken` objektu.

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač odkazující na profil uživatele, nebo hodnota NULL, pokud neexistuje žádný profil.

##  <a name="impersonate"></a>  CAccessToken::Impersonate

Voláním této metody lze přiřadit zosobnění `CAccessToken` ve vlákně.

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*hThread*<br/>
Popisovač vlákna přiřadit token zosobnění. Tento popisovač musí jste otevřeli pomocí TOKEN_IMPERSONATE přístupová práva. Pokud *hThread* má hodnotu NULL, metoda způsobí, že vlákno přestat používat token zosobnění.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud `CAccessToken` nemá platný ukazatel na token.

[Cautorevertimpersonation – třída](../../atl/reference/cautorevertimpersonation-class.md) je možné automaticky vrátit zosobněného přístupové tokeny.

##  <a name="impersonateloggedonuser"></a>  CAccessToken::ImpersonateLoggedOnUser

Voláním této metody lze povolit volající vlákno k zosobnění kontextu zabezpečení přihlášeného uživatele.

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

> [!IMPORTANT]
>  Pokud z nějakého důvodu selže volání funkce zosobnění, není zosobnit klienta a žádost klienta se provádí v kontextu zabezpečení procesu, ze kterého bylo provedeno volání. Pokud je proces spuštěn pod účtem s vysokou úrovní oprávnění, nebo jako člen skupiny pro správu, může být uživatel moct provádět akce, uživatel by jinak zakázán. Proto by měla být potvrzen vždy návratovou hodnotu pro tuto funkci.

##  <a name="istokenrestricted"></a>  CAccessToken::IsTokenRestricted

Voláním této metody, který testuje, jestli `CAccessToken` objekt obsahuje seznam identifikátorů SID s omezeným přístupem.

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud objekt obsahuje seznam omezení SID, FALSE, pokud neexistují žádná omezení identifikátory SID, nebo jestliže metoda selže.

##  <a name="loaduserprofile"></a>  CAccessToken::LoadUserProfile

Voláním této metody lze načíst profil uživatele přidružené k `CAccessToken` objektu.

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

V sestavení ladění, dojde k chybě kontrolního výrazu Pokud `CAccessToken` neobsahuje platný token nebo pokud uživatel profilu již existuje.

##  <a name="logonuser"></a>  CAccessToken::LogonUser

Volejte tuto metodu za účelem vytvoření relace přihlášení pro uživatele přidruženého k dané přihlašovací údaje.

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
Ukazatel na řetězec zakončený hodnotou null, který určuje uživatelské jméno. Toto je název uživatelského účtu k přihlášení.

*pszDomain*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje název domény nebo serveru, jehož účet databáze obsahuje *pszUserName* účtu.

*pszPassword*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje heslo prostého textu pro určený uživatelský účet *pszUserName*.

*dwLogonType*<br/>
Určuje typ operace přihlášení k provedení. Zobrazit [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) další podrobnosti.

*dwLogonProvider*<br/>
Určuje zprostředkovatele přihlášení. Zobrazit [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) další podrobnosti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Přístup k tokenu vyplývající z přihlášení bude přidružen `CAccessToken`. Pro tuto metodu za účelem úspěšné `CAccessToken` objekt musí mít oprávnění SE_TCB_NAME, identifikace držitel jako součást důvěryhodného počítače základní. Zobrazit [LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera) pro další informace týkající se požadovaná oprávnění.

##  <a name="opencomclienttoken"></a>  CAccessToken::OpenCOMClientToken

Volejte tuto metodu z v rámci serveru COM zpracování volání od klienta k inicializaci `CAccessToken` pomocí přístupového tokenu z modelu COM klienta.

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje přístupovou maska, která určuje požadované typy přístupu do tokenu přístupu. Tyto požadované typy přístup jsou porovnávány s DACL tokenu k určení, který přístup je udělen nebo odepřen.

*bImpersonate*<br/>
Při hodnotě TRUE se aktuální vlákno zosobní volající klient modelu COM, pokud se toto volání dokončí úspěšně. Pokud má hodnotu FALSE, otevřou se přístupový token, ale vlákno nebude mít token zosobnění, když toto volání dokončí.

*bOpenAsSelf*<br/>
Určuje, zda má být provedeno proti kontextu zabezpečení volající vlákno je kontrola přístupu [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) metoda nebo proti kontextu zabezpečení procesu pro volajícího vlákna.

Pokud má parametr hodnotu FALSE, je provedena kontrola přístupu v kontextu zabezpečení pro volajícího vlákna. Pokud vlákno provádí zosobnění klienta, může být takový kontext zabezpečení, která procesu klienta. Pokud tento parametr má hodnotu TRUE, provádí kontroly přístupu v kontextu zabezpečení procesu pro volajícího vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

[Cautorevertimpersonation – třída](../../atl/reference/cautorevertimpersonation-class.md) je možné automaticky vrátit zosobněného přístupové tokeny, které jsou vytvořené tak, že nastavíte *bImpersonate* příznak na hodnotu TRUE.

##  <a name="opennamedpipeclienttoken"></a>  CAccessToken::OpenNamedPipeClientToken

Volejte tuto metodu z v rámci serveru přijímání žádostí přes pojmenovaný kanál se inicializovat `CAccessToken` pomocí přístupového tokenu z klienta.

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>Parametry

*hPipe*<br/>
Popisovač pojmenovaného kanálu.

*dwDesiredAccess*<br/>
Určuje přístupovou maska, která určuje požadované typy přístupu do tokenu přístupu. Tyto požadované typy přístup jsou porovnávány s DACL tokenu k určení, který přístup je udělen nebo odepřen.

*bImpersonate*<br/>
Při hodnotě TRUE se aktuální vlákno zosobní volajícího klienta kanálu, pokud se toto volání dokončí úspěšně. Pokud má hodnotu FALSE, otevřou se přístupový token, ale vlákno nebude mít token zosobnění, když toto volání dokončí.

*bOpenAsSelf*<br/>
Určuje, zda má být provedeno proti kontextu zabezpečení volající vlákno je kontrola přístupu [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) metoda nebo proti kontextu zabezpečení procesu pro volajícího vlákna.

Pokud má parametr hodnotu FALSE, je provedena kontrola přístupu v kontextu zabezpečení pro volajícího vlákna. Pokud vlákno provádí zosobnění klienta, může být takový kontext zabezpečení, která procesu klienta. Pokud tento parametr má hodnotu TRUE, provádí kontroly přístupu v kontextu zabezpečení procesu pro volajícího vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

[Cautorevertimpersonation – třída](../../atl/reference/cautorevertimpersonation-class.md) je možné automaticky vrátit zosobněného přístupové tokeny, které jsou vytvořené tak, že nastavíte *bImpersonate* příznak na hodnotu TRUE.

##  <a name="openrpcclienttoken"></a>  CAccessToken::OpenRPCClientToken

Volejte tuto metodu z v rámci serveru zpracování volání od klienta k inicializaci `CAccessToken` pomocí přístupového tokenu z klienta.

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
Určuje přístupovou maska, která určuje požadované typy přístupu do tokenu přístupu. Tyto požadované typy přístup jsou porovnávány s DACL tokenu k určení, který přístup je udělen nebo odepřen.

*bImpersonate*<br/>
Při hodnotě TRUE se aktuální vlákno zosobní volajícího klienta vzdáleného volání Procedur, pokud se toto volání dokončí úspěšně. Pokud má hodnotu FALSE, otevřou se přístupový token, ale vlákno nebude mít token zosobnění, když toto volání dokončí.

*bOpenAsSelf*<br/>
Určuje, zda má být provedeno proti kontextu zabezpečení volající vlákno je kontrola přístupu [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) metoda nebo proti kontextu zabezpečení procesu pro volajícího vlákna.

Pokud má parametr hodnotu FALSE, je provedena kontrola přístupu v kontextu zabezpečení pro volajícího vlákna. Pokud vlákno provádí zosobnění klienta, může být takový kontext zabezpečení, která procesu klienta. Pokud tento parametr má hodnotu TRUE, provádí kontroly přístupu v kontextu zabezpečení procesu pro volajícího vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

[Cautorevertimpersonation – třída](../../atl/reference/cautorevertimpersonation-class.md) je možné automaticky vrátit zosobněného přístupové tokeny, které jsou vytvořené tak, že nastavíte *bImpersonate* příznak na hodnotu TRUE.

##  <a name="openthreadtoken"></a>  CAccessToken::OpenThreadToken

Voláním této metody lze nastavit úroveň zosobnění, kterou následně inicializujete `CAccessToken` pomocí tokenu z dané vlákno.

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>Parametry

*dwDesiredAccess*<br/>
Určuje přístupovou maska, která určuje požadované typy přístupu do tokenu přístupu. Tyto požadované typy přístup jsou porovnávány s DACL tokenu k určení, který přístup je udělen nebo odepřen.

*bImpersonate*<br/>
Při hodnotě TRUE se vlákno zůstanou na úrovni požadované zosobnění po dokončení této metody. Pokud má hodnotu FALSE, vlákno se vrátí k jeho původní úroveň zosobnění.

*bOpenAsSelf*<br/>
Určuje, zda má být provedeno proti kontextu zabezpečení volající vlákno je kontrola přístupu [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread) metoda nebo proti kontextu zabezpečení procesu pro volajícího vlákna.

Pokud má parametr hodnotu FALSE, je provedena kontrola přístupu v kontextu zabezpečení pro volajícího vlákna. Pokud vlákno provádí zosobnění klienta, může být takový kontext zabezpečení, která procesu klienta. Pokud tento parametr má hodnotu TRUE, provádí kontroly přístupu v kontextu zabezpečení procesu pro volajícího vlákna.

*sil*<br/>
Určuje [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level) Výčtový typ, který poskytuje úroveň zosobnění tokenu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

`OpenThreadToken` je podobný [CAccessToken::GetThreadToken](#getthreadtoken), ale nastaví úroveň zosobnění před inicializací `CAccessToken` z tokenu vlákna.

[Cautorevertimpersonation – třída](../../atl/reference/cautorevertimpersonation-class.md) je možné automaticky vrátit zosobněného přístupové tokeny, které jsou vytvořené tak, že nastavíte *bImpersonate* příznak na hodnotu TRUE.

##  <a name="privilegecheck"></a>  CAccessToken::PrivilegeCheck

Volejte tuto metodu za účelem určení, jestli jsou v povolené zadanou sadu oprávnění `CAccessToken` objektu.

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>Parametry

*RequiredPrivileges*<br/>
Ukazatel [PRIVILEGE_SET](/windows/desktop/api/winnt/ns-winnt-_privilege_set) struktury.

*pbResult*<br/>
Nastaví metodu k ukazatel na hodnotu označující, zda jsou povoleny některé nebo všechny zadané oprávnění v `CAccessToken` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Když `PrivilegeCheck` vrátí, `Attributes` členem všech [LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-_luid_and_attributes) struktury nastavená na SE_PRIVILEGE_USED_FOR_ACCESS, pokud je povolené odpovídající oprávnění. Tato metoda volá [PrivilegeCheck](https://msdn.microsoft.com/library/windows/desktop/aa379304) funkci Win32.

##  <a name="revert"></a>  CAccessToken::Revert

Voláním této metody lze zastavit pomocí tokenu zosobnění vlákna.

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>Parametry

*hThread*<br/>
Popisovač vlákna vrátit zosobnění. Pokud *hThread* má hodnotu NULL, předpokládá se aktuální vlákno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

K obnovení zosobnění tokenů lze provádět automaticky s [cautorevertimpersonation – třída](../../atl/reference/cautorevertimpersonation-class.md).

##  <a name="setdefaultdacl"></a>  CAccessToken::SetDefaultDacl

Voláním této metody lze nastavit výchozí seznam DACL `CAccessToken` objektu.

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>Parametry

*rDacl*<br/>
Nové výchozí [cdacl – třída](../../atl/reference/cdacl-class.md) informace.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Výchozí seznam DACL jde DACL, který se používá ve výchozím nastavení při vytvoření nových objektů s tímto tokenem přístupu v platnosti.

##  <a name="setowner"></a>  CAccessToken::SetOwner

Voláním této metody lze nastavit vlastníka `CAccessToken` objektu.

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[CSID – třída](../../atl/reference/csid-class.md) objekt, který obsahuje informace o vlastníkovi.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Vlastník je výchozí vlastníka, který se používá pro nové objekty vytvořené během Tento přístupový token je v platnosti.

##  <a name="setprimarygroup"></a>  CAccessToken::SetPrimaryGroup

Voláním této metody lze nastavit primární skupiny `CAccessToken` objektu.

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[CSID – třída](../../atl/reference/csid-class.md) objekt, který obsahuje informace o primární skupině.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Primární skupina je skupina výchozí pro nové objekty vytvořené během Tento přístupový token je v platnosti.

## <a name="see-also"></a>Viz také

[Ukázka ATLSecurity](../../visual-cpp-samples.md)<br/>
[Přístupové tokeny](/windows/desktop/SecAuthZ/access-tokens)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
