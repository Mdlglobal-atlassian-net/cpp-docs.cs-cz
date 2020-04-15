---
title: Třída CSid
ms.date: 03/27/2019
f1_keywords:
- CSid
- ATLSECURITY/ATL::CSid
- ATLSECURITY/ATL::CSid::CSidArray
- ATLSECURITY/ATL::CSid::CSid
- ATLSECURITY/ATL::CSid::AccountName
- ATLSECURITY/ATL::CSid::Domain
- ATLSECURITY/ATL::CSid::EqualPrefix
- ATLSECURITY/ATL::CSid::GetLength
- ATLSECURITY/ATL::CSid::GetPSID
- ATLSECURITY/ATL::CSid::GetPSID_IDENTIFIER_AUTHORITY
- ATLSECURITY/ATL::CSid::GetSubAuthority
- ATLSECURITY/ATL::CSid::GetSubAuthorityCount
- ATLSECURITY/ATL::CSid::IsValid
- ATLSECURITY/ATL::CSid::LoadAccount
- ATLSECURITY/ATL::CSid::Sid
- ATLSECURITY/ATL::CSid::SidNameUse
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
ms.openlocfilehash: 414cf428cebe8105d90b3add93cc7f1e76927c2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330915"
---
# <a name="csid-class"></a>Třída CSid

Tato třída je obálka `SID` pro (identifikátor zabezpečení) struktury.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSid
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CSid::CSidArray](#csidarray)|Pole `CSid` objektů.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSid::CSid](#csid)|Konstruktor|
|[CSid::~CSid](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSid::Název_účtu](#accountname)|Vrátí název účtu přidruženého `CSid` k objektu.|
|[CSid::Domain](#domain)|Vrátí název domény přidružené k `CSid` objektu.|
|[CSid::EqualPrefix](#equalprefix)|Testy `SID` (identifikátor zabezpečení) předpony pro rovnost.|
|[CSid::GetLength](#getlength)|Vrátí délku `CSid` objektu.|
|[CSid::GetPSID](#getpsid)|Vrátí ukazatel na `SID` strukturu.|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Vrátí ukazatel na `SID_IDENTIFIER_AUTHORITY` strukturu.|
|[CSid::GetSubAuthority](#getsubauthority)|Vrátí zadaný podřízený `SID` orgán ve struktuře.|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Vrátí počet podchodů.|
|[CSid::IsValid](#isvalid)|Testuje `CSid` platnost objektu.|
|[CSid::Načíst účet](#loadaccount)|Aktualizuje `CSid` objekt s názvem účtu a doménou nebo existující `SID` strukturou.|
|[CSid::Sid](#sid)|Vrátí řetězec ID.|
|[CSid::SidNameUse](#sidnameuse)|Vrátí popis stavu objektu. `CSid`|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Operátor přiřazení.|
|[operátor const SID *](#operator_const_sid__star)|Předává `CSid` objekt na ukazatel `SID` na strukturu.|

### <a name="global-operators"></a>Globální operátoři

|||
|-|-|
|[operátor ==](#operator_eq_eq)|Testuje dva objekty popisovače zabezpečení pro rovnost.|
|[operátor !=](#operator_neq)|Testuje dva objekty popisovače zabezpečení pro nerovnost.|
|[Operátor\<](#operator_lt)|Porovná relativní hodnotu dvou objektů popisovače zabezpečení.|
|[>operátora](#operator_gt)|Porovná relativní hodnotu dvou objektů popisovače zabezpečení.|
|[Operátor\<=](#operator_lt__eq)|Porovná relativní hodnotu dvou objektů popisovače zabezpečení.|
|[operátor >=](#operator_gt__eq)|Porovná relativní hodnotu dvou objektů popisovače zabezpečení.|

## <a name="remarks"></a>Poznámky

Struktura `SID` je struktura proměnné délky, která slouží k jednoznačné identifikaci uživatelů nebo skupin.

Aplikace by neměly upravovat `SID` strukturu přímo, ale místo toho použít metody uvedené v této třídě obálky. Viz také [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)a [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Úvod k modelu řízení přístupu v systému Windows najdete v tématu [Řízení přístupu](/windows/win32/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="csidaccountname"></a><a name="accountname"></a>CSid::Název_účtu

Vrátí název účtu přidruženého `CSid` k objektu.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí lPCTSTR odkazující na název účtu.

### <a name="remarks"></a>Poznámky

Tato metoda se pokusí najít název `SID` pro zadaný (identifikátor zabezpečení). Podrobné informace naleznete v tématu [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Pokud nelze najít `SID` žádný název `AccountName` účtu pro tento, vrátí prázdný řetězec. Tato situace může nastat, pokud časový časový výtku sítě brání této metodě najít název. Dochází také pro identifikátory zabezpečení bez odpovídající název `SID` účtu, jako je například který identifikuje relaci přihlášení.

## <a name="csidcsid"></a><a name="csid"></a>CSid::CSid

Konstruktor

```
CSid() throw();
CSid(const SID& rhs) throw(...);
CSid(const CSid& rhs) throw(...);

CSid(
    const SID_IDENTIFIER_AUTHORITY& IdentifierAuthority,
    BYTE nSubAuthorityCount,
    ...) throw(...);

explicit CSid(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

explicit CSid(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Existující `CSid` struktura `SID` objektu nebo (identifikátor zabezpečení).

*IdentifikátorAuthority*<br/>
Autorita.

*nPočet subauthorityCount*<br/>
Počet podautorit.

*pszAccountName*<br/>
Název účtu.

*pszSystém*<br/>
Název systému. Tento řetězec může být název vzdáleného počítače. Pokud je tento řetězec null, místo toho se použije místní systém.

*pSid*<br/>
Ukazatel na `SID` strukturu.

### <a name="remarks"></a>Poznámky

Konstruktor inicializuje `CSid` objekt, nastaví interní datový člen na *SidTypeInvalid*nebo zkopírováním nastavení z existujícího `CSid`nebo `SID`existujícího účtu.

Pokud se inicializace nezdaří, konstruktor vyvolá [třídu CAtlException](../../atl/reference/catlexception-class.md).

## <a name="csidcsid"></a><a name="dtor"></a>CSid::~CSid

Destruktor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny prostředky získané objektem.

## <a name="csidcsidarray"></a><a name="csidarray"></a>CSid::CSidArray

Pole [CSid](../../atl/reference/csid-class.md) objektů.

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Poznámky

Tento typedef určuje typ pole, který lze použít k načtení identifikátorů zabezpečení z seznamu ACL (seznam řízení přístupu). Viz [CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

## <a name="csiddomain"></a><a name="domain"></a>CSid::Domain

Vrátí název domény přidružené k `CSid` objektu.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `LPCTSTR` směrování na doménu.

### <a name="remarks"></a>Poznámky

Tato metoda se pokusí najít název `SID` pro zadaný (identifikátor zabezpečení). Podrobné informace naleznete v tématu [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Pokud `SID` nelze najít žádný název `Domain` účtu pro tento účet, vrátí doménu jako prázdný řetězec. Tato situace může nastat, pokud časový časový výtku sítě brání této metodě najít název. Dochází také pro identifikátory zabezpečení bez odpovídající název `SID` účtu, jako je například který identifikuje relaci přihlášení.

## <a name="csidequalprefix"></a><a name="equalprefix"></a>CSid::EqualPrefix

Testy `SID` (identifikátor zabezpečení) předpony pro rovnost.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Struktura `SID` (identifikátor zabezpečení) `CSid` nebo objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Další podrobnosti naleznete v [tématu EqualPrefixSid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) v sadě Windows SDK.

## <a name="csidgetlength"></a><a name="getlength"></a>CSid::GetLength

Vrátí délku `CSid` objektu.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku v bajtů objektu. `CSid`

### <a name="remarks"></a>Poznámky

Pokud `CSid` struktura není platná, vrácená hodnota není definována. Před `GetLength`voláním použijte členovou funkci [CSid::IsValid](#isvalid) k ověření platné `CSid` funkce.

> [!NOTE]
> Pod ladění sestavení funkce způsobí ASSERT, `CSid` pokud objekt není platný.

## <a name="csidgetpsid"></a><a name="getpsid"></a>CSid::GetPSID

Vrátí ukazatel na `SID` strukturu (identifikátor zabezpečení).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu základní `CSid` `SID` struktury objektu.

## <a name="csidgetpsid_identifier_authority"></a><a name="getpsid_identifier_authority"></a>CSid::GetPSID_IDENTIFIER_AUTHORITY

Vrátí ukazatel na `SID_IDENTIFIER_AUTHORITY` strukturu.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí `SID_IDENTIFIER_AUTHORITY` adresu struktury. Pokud se nezdaří, vrácená hodnota není definována. K selhání může `CSid` dojít, pokud objekt není platný, v takovém případě [csid::IsValid](#isvalid) metoda vrátí FALSE. Funkce `GetLastError` může být volána pro rozšířené informace o chybě.

> [!NOTE]
> Pod ladění sestavení funkce způsobí ASSERT, `CSid` pokud objekt není platný.

## <a name="csidgetsubauthority"></a><a name="getsubauthority"></a>CSid::GetSubAuthority

Vrátí zadaný podřízený `SID` orgán ve struktuře (identifikátor zabezpečení).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parametry

*nSubAautorita*<br/>
Podmocní.

### <a name="return-value"></a>Návratová hodnota

Vrátí podřízený úřad, na který *odkazuje nSubAuthority.* Hodnota subauthority je relativní identifikátor (RID).

### <a name="remarks"></a>Poznámky

Parametr *nSubAuthority* určuje hodnotu indexu identifikující prvek pole subauthority, který metoda vrátí. Metoda provádí žádné ověřovací testy na tuto hodnotu. Aplikace může volat [CSid::GetSubAuthorityCount](#getsubauthoritycount) ke zjištění rozsahu přijatelné hodnoty.

> [!NOTE]
> Pod ladění sestavení funkce způsobí ASSERT, `CSid` pokud objekt není platný.

## <a name="csidgetsubauthoritycount"></a><a name="getsubauthoritycount"></a>CSid::GetSubAuthorityCount

Vrátí počet podchodů.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrácená hodnota je počet podautority.

Pokud se metoda nezdaří, vrácená hodnota není definována. Metoda se nezdaří, `CSid` pokud je objekt neplatný. Chcete-li získat rozšířené `GetLastError`informace o chybě, volejte .

> [!NOTE]
> Pod ladění sestavení funkce způsobí ASSERT, `CSid` pokud objekt není platný.

## <a name="csidisvalid"></a><a name="isvalid"></a>CSid::IsValid

Testuje `CSid` platnost objektu.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu `CSid` PRAVDA, pokud je objekt platný, NEPRAVDA, pokud ne. Pro tuto metodu nejsou k dispozici žádné rozšířené informace o chybě. nevolejte `GetLastError`.

### <a name="remarks"></a>Poznámky

Metoda `IsValid` ověří `CSid` objekt ověřením, že číslo revize je v rámci známého rozsahu a že počet podautorit je menší než maximální.

## <a name="csidloadaccount"></a><a name="loadaccount"></a>CSid::Načíst účet

Aktualizuje `CSid` objekt s názvem a doménou účtu nebo existující strukturu IDENTIFIKÁTOR SID (identifikátor zabezpečení).

```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszAccountName*<br/>
Název účtu.

*pszSystém*<br/>
Název systému. Tento řetězec může být název vzdáleného počítače. Pokud je tento řetězec null, místo toho se použije místní systém.

*pSid*<br/>
Ukazatel na strukturu [SID.](/windows/win32/api/winnt/ns-winnt-sid)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu. Chcete-li získat rozšířené `GetLastError`informace o chybě, volejte .

### <a name="remarks"></a>Poznámky

`LoadAccount`pokusí se najít identifikátor zabezpečení pro zadaný název. Další podrobnosti najdete v [tématu LookupAccountSid.](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw)

## <a name="csidoperator-"></a><a name="operator_eq"></a>CSid::operátor =

Operátor přiřazení.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo přiřadit `CSid` k objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na `CSid` aktualizovaný objekt.

## <a name="csidoperator-"></a><a name="operator_eq_eq"></a>CSid::operátor ==

Testuje dva objekty popisovače zabezpečení pro rovnost.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na levé straně operátoru ==.

*rhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na pravé straně operátoru ==.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud jsou popisovače zabezpečení stejné, jinak FALSE.

## <a name="csidoperator-"></a><a name="operator_neq"></a>CSid::operátor !=

Testuje dva objekty popisovače zabezpečení pro nerovnost.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na levé straně operátoru !=.

*rhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na pravé straně operátoru !=.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud popisovače zabezpečení nejsou stejné, jinak FALSE.

## <a name="csidoperator-lt"></a><a name="operator_lt"></a>CSid::operátor&lt;

Porovná relativní hodnotu dvou objektů popisovače zabezpečení.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na levé straně operátoru !=.

*rhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na pravé straně operátoru !=.

### <a name="return-value"></a>Návratová hodnota

TRUE Pokud *je lhs* menší než *rhs*, jinak FALSE.

## <a name="csidoperator-lt"></a><a name="operator_lt__eq"></a>CSid::operátor&lt;=

Porovná relativní hodnotu dvou objektů popisovače zabezpečení.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na levé straně operátoru !=.

*rhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na pravé straně operátoru !=.

### <a name="return-value"></a>Návratová hodnota

TRUE Pokud je *lhs* menší nebo rovno *rhs*, jinak FALSE.

## <a name="csidoperator-gt"></a><a name="operator_gt"></a>CSid::operátor&gt;

Porovná relativní hodnotu dvou objektů popisovače zabezpečení.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na levé straně operátoru !=.

*rhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na pravé straně operátoru !=.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud *je hodnota lhs* větší než *rhs*, jinak FALSE.

## <a name="csidoperator-gt"></a><a name="operator_gt__eq"></a>CSid::operátor&gt;=

Porovná relativní hodnotu dvou objektů popisovače zabezpečení.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na levé straně operátoru !=.

*rhs*<br/>
(identifikátor `SID` zabezpečení) `CSid` nebo který se zobrazí na pravé straně operátoru !=.

### <a name="return-value"></a>Návratová hodnota

TRUE Pokud je *hodnota lhs* větší nebo rovna *rhs*, jinak FALSE.

## <a name="csidoperator-const-sid-"></a><a name="operator_const_sid__star"></a>CSid::operátor const SID\*

Předává `CSid` objekt na ukazatel `SID` (identifikátor zabezpečení) struktury.

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Vrátí adresu `SID` struktury.

## <a name="csidsid"></a><a name="sid"></a>CSid::Sid

Vrátí `SID` strukturu (identifikátor zabezpečení) jako řetězec.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `SID` strukturu jako řetězec ve formátu vhodném pro zobrazení, ukládání nebo přenos. Ekvivalent [ConvertSidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw).

## <a name="csidsidnameuse"></a><a name="sidnameuse"></a>CSid::SidNameUse

Vrátí popis stavu objektu. `CSid`

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu datového člena, který ukládá hodnotu `CSid` popisující stav objektu.

|Hodnota|Popis|
|-----------|-----------------|
|SidTypeUser|Označuje uživatele `SID` (identifikátor zabezpečení).|
|Skupina SidType|Označuje skupinu `SID`.|
|Doména SidType|Označuje doménu `SID`.|
|SidTypeAlias|Označuje alias `SID`.|
|SidTypeWellKnownSkupina|Označuje `SID` pro známé skupiny.|
|SidTypeDeletedAccount|Označuje `SID` a pro odstraněný účet.|
|SidTypeNeplatné|Označuje neplatný `SID`.|
|SidTypeNeznámý|Označuje neznámý `SID` typ.|
|SidTypePočítač|Označuje `SID` pro počítač.|

### <a name="remarks"></a>Poznámky

Volání [CSid::LoadAccount](#loadaccount) aktualizovat `CSid` objekt `SidNameUse` před voláním vrátit jeho stav. `SidNameUse`nezmění stav objektu (voláním nebo `LookupAccountName` `LookupAccountSid`), ale vrátí pouze aktuální stav.

## <a name="see-also"></a>Viz také

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)<br/>
[Operátory](../../atl/reference/atl-operators.md)
