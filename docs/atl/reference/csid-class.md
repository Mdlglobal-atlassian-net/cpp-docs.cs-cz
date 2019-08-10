---
title: CSid – třída
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
ms.openlocfilehash: fb496e3bd58d0fe134c37b240eb2698302c6aa64
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915701"
---
# <a name="csid-class"></a>CSid – třída

Tato třída je obálkou `SID` struktury (identifikátoru zabezpečení).

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSid
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|[ID CSid:: CSidArray](#csidarray)|Pole `CSid` objektů.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[ID CSid:: CSid](#csid)|Konstruktor|
|[CSid::~CSid](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSid:: account.](#accountname)|Vrátí název účtu přidruženého `CSid` k objektu.|
|[CSid::D omain](#domain)|Vrátí název domény přidružené `CSid` k objektu.|
|[CSid::EqualPrefix](#equalprefix)|Testuje `SID` předpony (identifikátor zabezpečení) pro rovnost.|
|[CSid:: GetLength](#getlength)|Vrátí délku `CSid` objektu.|
|[ID CSid:: GetPSID](#getpsid)|Vrátí ukazatel na `SID` strukturu.|
|[ID CSid:: GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Vrátí ukazatel na `SID_IDENTIFIER_AUTHORITY` strukturu.|
|[ID CSid:: GetSubAuthority](#getsubauthority)|Vrátí zadanou podautoritu ve `SID` struktuře.|
|[ID CSid:: GetSubAuthorityCount](#getsubauthoritycount)|Vrátí počet podúřadů.|
|[CSid:: IsValid](#isvalid)|Testuje platnost `CSid` objektu.|
|[ID CSid:: LoadAccount](#loadaccount)|Aktualizuje objekt daného názvu a domény účtu nebo existující `SID` struktury. `CSid`|
|[ID CSid:: SID](#sid)|Vrátí řetězec ID.|
|[ID CSid:: SidNameUse](#sidnameuse)|Vrátí popis stavu `CSid` objektu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Operátor přiřazení|
|[operátor const SID *](#operator_const_sid__star)|Přetypování `SID` objektu na ukazatel na strukturu. `CSid`|

### <a name="global-operators"></a>Globální operátory

|||
|-|-|
|[operator = = – operátor](#operator_eq_eq)|Testuje dva objekty popisovače zabezpečení pro rovnost|
|[! = – operátor](#operator_neq)|Testuje dva objekty popisovače zabezpečení pro nerovnost|
|[podnikatel\<](#operator_lt)|Porovná relativní hodnotu dvou objektů popisovače zabezpečení.|
|[operátor >](#operator_gt)|Porovná relativní hodnotu dvou objektů popisovače zabezpečení.|
|[podnikatel\<=](#operator_lt__eq)|Porovná relativní hodnotu dvou objektů popisovače zabezpečení.|
|[operátor > =](#operator_gt__eq)|Porovná relativní hodnotu dvou objektů popisovače zabezpečení.|

## <a name="remarks"></a>Poznámky

`SID` Struktura je struktura s proměnlivou délkou, která slouží k jednoznačné identifikaci uživatelů nebo skupin.

Aplikace by neměly měnit `SID` strukturu přímo, ale místo toho používají metody poskytované v této obálkové třídě. Viz také [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)a [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Úvod do modelu řízení přístupu v systému Windows naleznete v tématu [Access Control](/windows/desktop/SecAuthZ/access-control) v Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="accountname"></a>CSid:: account.

Vrátí název účtu přidruženého `CSid` k objektu.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí LPCTSTR ukazující na název účtu.

### <a name="remarks"></a>Poznámky

Tato metoda se pokusí najít název zadaného `SID` (identifikátoru zabezpečení). Úplné podrobnosti najdete v tématu [funkce LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Pokud není `SID` možné najít žádný název účtu, `AccountName` vrátí prázdný řetězec. K tomu může dojít, pokud časový limit sítě brání této metodě v hledání názvu. K tomu dochází taky u identifikátorů zabezpečení, které nemají odpovídající název účtu, `SID` jako je například, který identifikuje přihlašovací relaci.

##  <a name="csid"></a>ID CSid:: CSid

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

*zarovnání indirekce RHS*<br/>
Existující `CSid` struktura objektu nebo `SID` (identifikátor zabezpečení).

*IdentifierAuthority*<br/>
Autorita.

*nSubAuthorityCount*<br/>
Počet podúřadů.

*pszAccountName*<br/>
Název účtu.

*pszSystem*<br/>
Název systému. Tento řetězec může být název vzdáleného počítače. Pokud je tento řetězec NULL, použije se místo toho místní systém.

*pSid*<br/>
Ukazatel na `SID` strukturu.

### <a name="remarks"></a>Poznámky

Konstruktor inicializuje `CSid` objekt, nastavení interního datového členu na *SidTypeInvalid*nebo zkopírováním nastavení `CSid` `SID`z existujícího nebo existujícího účtu.

Pokud se inicializace nezdaří, konstruktor vyvolá [třídu CAtlException](../../atl/reference/catlexception-class.md).

##  <a name="dtor"></a>CSid:: ~ CSid

Destruktor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny prostředky, které objekt získal.

##  <a name="csidarray"></a>ID CSid:: CSidArray

Pole objektů [CSID](../../atl/reference/csid-class.md) .

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Poznámky

Tato definice typedef určuje typ pole, který lze použít k načtení identifikátorů zabezpečení ze seznamu řízení přístupu (ACL). Viz [CACL:: GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

##  <a name="domain"></a>CSid::D omain

Vrátí název domény přidružené `CSid` k objektu.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

`LPCTSTR` Vrátí ukazující na doménu.

### <a name="remarks"></a>Poznámky

Tato metoda se pokusí najít název zadaného `SID` (identifikátoru zabezpečení). Úplné podrobnosti najdete v tématu [funkce LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Pokud není `SID` možné najít žádný název účtu, `Domain` vrátí doménu jako prázdný řetězec. K tomu může dojít, pokud časový limit sítě brání této metodě v hledání názvu. K tomu dochází taky u identifikátorů zabezpečení, které nemají odpovídající název účtu, `SID` jako je například, který identifikuje přihlašovací relaci.

##  <a name="equalprefix"></a>ID CSid:: EqualPrefix

Testuje `SID` předpony (identifikátor zabezpečení) pro rovnost.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
Struktura nebo`CSid` objekt pro porovnání (identifikátorzabezpečení).`SID`

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Další podrobnosti najdete v tématu [EqualPrefixSid](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) v Windows SDK.

##  <a name="getlength"></a>CSid:: GetLength

Vrátí délku `CSid` objektu.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku `CSid` objektu v bajtech.

### <a name="remarks"></a>Poznámky

`CSid` Pokud struktura není platná, návratová hodnota není definována. Před voláním `GetLength`pomocí členské funkce [CSID:: IsValid](#isvalid) ověřte, zda `CSid` je platný.

> [!NOTE]
>  V části ladění sestavení funkce způsobí vyhodnocení v případě, `CSid` že objekt není platný.

##  <a name="getpsid"></a>ID CSid:: GetPSID

Vrátí ukazatel na `SID` strukturu (identifikátor zabezpečení).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu `CSid` podkladové `SID` struktury objektu.

##  <a name="getpsid_identifier_authority"></a>ID CSid:: GetPSID_IDENTIFIER_AUTHORITY

Vrátí ukazatel na `SID_IDENTIFIER_AUTHORITY` strukturu.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí adresu `SID_IDENTIFIER_AUTHORITY` struktury. Pokud dojde k chybě, návratová hodnota není definována. K selhání může dojít v `CSid` případě, že objekt není platný. v takovém případě metoda [CSID:: IsValid](#isvalid) vrátí hodnotu false. Funkci `GetLastError` lze volat pro rozšířené informace o chybě.

> [!NOTE]
>  V části ladění sestavení funkce způsobí vyhodnocení v případě, `CSid` že objekt není platný.

##  <a name="getsubauthority"></a>ID CSid:: GetSubAuthority

Vrátí zadanou podautoritu ve `SID` struktuře (identifikátoru zabezpečení).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parametry

*nSubAuthority*<br/>
Podautorita.

### <a name="return-value"></a>Návratová hodnota

Vrátí podautoritu, na kterou odkazuje *NSubAuthority.* Hodnota subauthority je relativní identifikátor (RID).

### <a name="remarks"></a>Poznámky

Parametr *NSubAuthority* Určuje hodnotu indexu identifikující prvek pole podautority, který bude metoda vracet. Metoda neprovede pro tuto hodnotu žádné ověřovací testy. Aplikace může volat identifikátor [CSID:: GetSubAuthorityCount](#getsubauthoritycount) , aby zjistila rozsah přijatelných hodnot.

> [!NOTE]
>  V části ladění sestavení funkce způsobí vyhodnocení v případě, `CSid` že objekt není platný.

##  <a name="getsubauthoritycount"></a>ID CSid:: GetSubAuthorityCount

Vrátí počet podúřadů.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, návratová hodnota je počet podautorit.

Pokud se metoda nezdařila, návratová hodnota není definována. Metoda se nezdařila `CSid` , pokud je objekt neplatný. Chcete-li získat rozšířené informace o `GetLastError`chybě, zavolejte.

> [!NOTE]
>  V části ladění sestavení funkce způsobí vyhodnocení v případě, `CSid` že objekt není platný.

##  <a name="isvalid"></a>CSid:: IsValid

Testuje platnost `CSid` objektu.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, `CSid` Pokud je objekt platný, false, pokud není. Pro tuto metodu nejsou k dispozici žádné rozšířené informace o chybě. Nevolejte `GetLastError`.

### <a name="remarks"></a>Poznámky

`IsValid` Metoda ověří`CSid` objekt tím, že ověřuje, zda se číslo revize nachází v známém rozsahu a že počet subúřadů je menší než maximální hodnota.

##  <a name="loadaccount"></a>ID CSid:: LoadAccount

`CSid` Aktualizuje objekt daného názvu a domény účtu nebo existující struktury identifikátoru SID (identifikátoru zabezpečení).

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

*pszSystem*<br/>
Název systému. Tento řetězec může být název vzdáleného počítače. Pokud je tento řetězec NULL, použije se místo toho místní systém.

*pSid*<br/>
Ukazatel na strukturu [identifikátoru SID](/windows/desktop/api/winnt/ns-winnt-sid) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání. Chcete-li získat rozšířené informace o `GetLastError`chybě, zavolejte.

### <a name="remarks"></a>Poznámky

`LoadAccount`pokusí se najít identifikátor zabezpečení pro zadaný název. Další podrobnosti najdete v tématu [funkce LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida) .

##  <a name="operator_eq"></a>CSid:: operator =

Operátor přiřazení

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
(Identifikátor zabezpečení) nebo `CSid` přiřadit k `CSid` objektu. `SID`

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktualizovaný `CSid` objekt.

##  <a name="operator_eq_eq"></a>CSid:: operator = =

Testuje dva objekty popisovače zabezpečení pro rovnost.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na levé straně operátoru = =. `SID`

*zarovnání indirekce RHS*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na pravé straně operátoru = =. `SID`

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou popisovače zabezpečení stejné, jinak FALSE.

##  <a name="operator_neq"></a>CSid:: operator! =

Testuje dva objekty popisovače zabezpečení pro nerovnost.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na levé straně operátoru! =. `SID`

*zarovnání indirekce RHS*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na pravé straně operátoru! =. `SID`

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud popisovače zabezpečení nejsou stejné, jinak FALSE.

##  <a name="operator_lt"></a>CSid:: operator&lt;

Porovná relativní hodnotu dvou objektů popisovače zabezpečení.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na levé straně operátoru! =. `SID`

*zarovnání indirekce RHS*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na pravé straně operátoru! =. `SID`

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je *LHS* menší než *Zarovnání indirekce RHS*, v opačném případě false.

##  <a name="operator_lt__eq"></a>CSid:: operator&lt;=

Porovná relativní hodnotu dvou objektů popisovače zabezpečení.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na levé straně operátoru! =. `SID`

*zarovnání indirekce RHS*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na pravé straně operátoru! =. `SID`

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je *LHS* menší nebo roven *Zarovnání indirekce RHS*, v opačném případě false.

##  <a name="operator_gt"></a>CSid:: operator&gt;

Porovná relativní hodnotu dvou objektů popisovače zabezpečení.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na levé straně operátoru! =. `SID`

*zarovnání indirekce RHS*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na pravé straně operátoru! =. `SID`

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je *LHS* větší než *Zarovnání indirekce RHS*, v opačném případě false.

##  <a name="operator_gt__eq"></a>CSid:: operator&gt;=

Porovná relativní hodnotu dvou objektů popisovače zabezpečení.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na levé straně operátoru! =. `SID`

*zarovnání indirekce RHS*<br/>
(Identifikátor zabezpečení) nebo `CSid` , který se zobrazí na pravé straně operátoru! =. `SID`

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je *LHS* větší než nebo rovno *Zarovnání INDIREKCE RHS*, jinak false.

##  <a name="operator_const_sid__star"></a>ID CSid:: operator const SID\*

Přetypování `SID` objektu na ukazatel na strukturu (identifikátor zabezpečení). `CSid`

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Vrátí adresu `SID` struktury.

##  <a name="sid"></a>ID CSid:: SID

Vrátí strukturu `SID` (identifikátor zabezpečení) jako řetězec.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

`SID` Vrátí strukturu jako řetězec ve formátu vhodném pro zobrazení, ukládání nebo přenos. Ekvivalent [funkce ConvertSidToStringSid](/windows/desktop/api/sddl/nf-sddl-convertsidtostringsida).

##  <a name="sidnameuse"></a>ID CSid:: SidNameUse

Vrátí popis stavu `CSid` objektu.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu datového člena, který ukládá hodnotu popisující stav `CSid` objektu.

|Value|Popis|
|-----------|-----------------|
|SidTypeUser|Označuje uživatele `SID` (identifikátor zabezpečení).|
|SidTypeGroup|Označuje skupinu `SID`.|
|SidTypeDomain|Označuje doménu `SID`.|
|SidTypeAlias|Označuje alias `SID`.|
|SidTypeWellKnownGroup|`SID` Označuje pro dobře známou skupinu.|
|SidTypeDeletedAccount|`SID` Označuje pro odstraněný účet.|
|SidTypeInvalid|Indikuje neplatný `SID`.|
|SidTypeUnknown|Označuje neznámý `SID` typ.|
|SidTypeComputer|`SID` Označuje pro počítač.|

### <a name="remarks"></a>Poznámky

Chcete-li aktualizovat objekt před voláním `CSid` metody `SidNameUse` , která vrátí svůj stav, zavolejte identifikátor [CSID:: LoadAccount](#loadaccount) . `SidNameUse`nemění stav objektu (voláním metody `LookupAccountName` nebo `LookupAccountSid`), ale vrací pouze aktuální stav.

## <a name="see-also"></a>Viz také:

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)<br/>
[Operátory](../../atl/reference/atl-operators.md)
