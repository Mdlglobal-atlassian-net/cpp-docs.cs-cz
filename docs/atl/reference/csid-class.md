---
title: CSID – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97c88b73499948db4e8fc0645b2d59f7b92b3cfe
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753175"
---
# <a name="csid-class"></a>CSID – třída

Tato třída představuje obálku pro `SID` strukturu (security identifier).

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSid
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CSid::CSidArray](#csidarray)|Pole `CSid` objekty.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSid::CSid](#csid)|Konstruktor|
|[Identifikační číslo volané stanice:: ~ identifikační číslo volané stanice](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSid::AccountName](#accountname)|Vrátí název účtu přidruženého k `CSid` objektu.|
|[CSid::Domain](#domain)|Vrátí název domény přidružené k `CSid` objektu.|
|[CSid::EqualPrefix](#equalprefix)|Testy `SID` předpony (security identifier) pro rovnost.|
|[CSid::GetLength](#getlength)|Vrátí délku objektu `CSid` objektu.|
|[CSid::GetPSID](#getpsid)|Vrací ukazatel `SID` struktury.|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Vrací ukazatel `SID_IDENTIFIER_AUTHORITY` struktury.|
|[CSid::GetSubAuthority](#getsubauthority)|Vrátí zadaný podautority v `SID` struktury.|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Vrátí počet podautority.|
|[CSid::IsValid](#isvalid)|Testy `CSid` objekt platnost.|
|[CSid::LoadAccount](#loadaccount)|Aktualizace `CSid` objekt dle názvu účtu a doménu nebo z existujícího `SID` struktury.|
|[CSid::Sid](#sid)|Vrátí řetězec ID.|
|[CSid::SidNameUse](#sidnameuse)|Vrátí popis stavu `CSid` objektu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#operator_eq)|Operátor přiřazení.|
|[operátor SID const *](#operator_const_sid__star)|Přetypování `CSid` na ukazatel na objekt `SID` struktury.|

### <a name="global-operators"></a>Globální operátory

|||
|-|-|
|[Operator ==](#operator_eq_eq)|Testuje dva objekty popisovač zabezpečení pro rovnost|
|[Operator! =](#operator_neq)|Testuje dva objekty popisovač zabezpečení pro nerovnost|
|[– Operátor \<](#operator_lt_)|Porovná relativní hodnotu dvou objektů popisovač zabezpečení.|
|[Operator >](#operator_gt_)|Porovná relativní hodnotu dvou objektů popisovač zabezpečení.|
|[– Operátor \<=](#operator_lt__eq)|Porovná relativní hodnotu dvou objektů popisovač zabezpečení.|
|[Operator > =](#operator_gt__eq)|Porovná relativní hodnotu dvou objektů popisovač zabezpečení.|

## <a name="remarks"></a>Poznámky

`SID` Struktura je struktura proměnné délky sloužící k jednoznačné identifikaci uživatele nebo skupiny.

Aplikace by neměla změnit `SID` struktura přímo, ale místo toho použijte metody poskytované v této obálkové třídy. Viz také [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid), a [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="accountname"></a>  CSid::AccountName

Vrátí název účtu přidruženého k `CSid` objektu.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí LPCTSTR odkazující na název účtu.

### <a name="remarks"></a>Poznámky

Tato metoda se pokusí najít název zadaného `SID` (security identifier). Úplné podrobnosti najdete v tématu [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Pokud žádný název účtu pro `SID` najdete, `AccountName` vrátí prázdný řetězec. Tato situace může nastat, pokud vypršel časový limit sítě zabraňuje tato metoda vyhledání názvu. Dojde k také pro identifikátory zabezpečení bez odpovídající názvu účtu, jako je například přihlášení `SID` identifikující přihlašovací relace.

##  <a name="csid"></a>  CSid::CSid

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

*Zarovnání indirekce RHS*  
Existující `CSid` objektu nebo `SID` strukturu (security identifier).

*IdentifierAuthority*  
Oprávnění.

*nSubAuthorityCount*  
Počet podautority.

*pszAccountName*  
Název účtu.

*pszSystem*  
Název systému. Tento řetězec může být název vzdáleného počítače. Pokud tento řetězec hodnotu NULL, použije se místo toho místní systém.

*psid má*  
Ukazatel `SID` struktury.

### <a name="remarks"></a>Poznámky

Konstruktor inicializuje `CSid` objekt nastavení na interní datový člen *SidTypeInvalid*, nebo zkopírováním nastavení z existující `CSid`, `SID`, nebo existující účet.

Jestliže se inicializace nezdaří, vyvolá výjimku konstruktoru [catlexception – třída](../../atl/reference/catlexception-class.md).

##  <a name="dtor"></a>  Identifikační číslo volané stanice:: ~ identifikační číslo volané stanice

Destruktor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny prostředky získané v objektu.

##  <a name="csidarray"></a>  CSid::CSidArray

Pole [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekty.

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Poznámky

Tato definice typu Určuje typ pole, který slouží k načtení identifikátory zabezpečení ze seznamu ACL portu (seznam řízení přístupu). Zobrazit [CAcl::GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

##  <a name="domain"></a>  CSid::Domain

Vrátí název domény přidružené k `CSid` objektu.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `LPCTSTR` odkazující na doménu.

### <a name="remarks"></a>Poznámky

Tato metoda se pokusí najít název zadaného `SID` (security identifier). Úplné podrobnosti najdete v tématu [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida).

Pokud žádný název účtu pro `SID` najdete, `Domain` vrátí název domény jako prázdný řetězec. Tato situace může nastat, pokud vypršel časový limit sítě zabraňuje tato metoda vyhledání názvu. Dojde k také pro identifikátory zabezpečení bez odpovídající názvu účtu, jako je například přihlášení `SID` identifikující přihlašovací relace.

##  <a name="equalprefix"></a>  CSid::EqualPrefix

Testy `SID` předpony (security identifier) pro rovnost.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*  
`SID` Strukturu (security identifier) nebo `CSid` objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Zobrazit [EqualPrefixSid](https://msdn.microsoft.com/library/windows/desktop/aa446621) v sadě Windows SDK pro další podrobnosti.

##  <a name="getlength"></a>  CSid::GetLength

Vrátí délku objektu `CSid` objektu.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku v bajtech `CSid` objektu.

### <a name="remarks"></a>Poznámky

Pokud `CSid` struktura není platná, návratová hodnota není definována. Před voláním `GetLength`, použijte [CSid::IsValid](#isvalid) členské funkce a ověřte, zda `CSid` je platný.

> [!NOTE]
>  V části sestavení pro ladění funkce způsobí ASSERT, pokud `CSid` objekt není platný.

##  <a name="getpsid"></a>  CSid::GetPSID

Vrací ukazatel `SID` struktury (security identifier).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí adresu `CSid` podkladového objektu `SID` struktury.

##  <a name="getpsid_identifier_authority"></a>  CSid::GetPSID_IDENTIFIER_AUTHORITY

Vrací ukazatel `SID_IDENTIFIER_AUTHORITY` struktury.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí adresu `SID_IDENTIFIER_AUTHORITY` struktury. Pokud selže, návratová hodnota není definována. Selhání může dojít, pokud `CSid` objekt není platný, v takovém případě [CSid::IsValid](#isvalid) metoda vrátí hodnotu FALSE. Funkce `GetLastError` lze volat pro rozšířené informace o chybě.

> [!NOTE]
>  V části sestavení pro ladění funkce způsobí ASSERT, pokud `CSid` objekt není platný.

##  <a name="getsubauthority"></a>  CSid::GetSubAuthority

Vrátí zadaný podautority v `SID` strukturu (security identifier).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parametry

*nSubAuthority*  
Podautority.

### <a name="return-value"></a>Návratová hodnota

Vrátí podautority odkazuje *nSubAuthority.* Hodnota podautority je relativní identifikátor (RID).

### <a name="remarks"></a>Poznámky

*NSubAuthority* parametr určuje hodnotu indexu identifikace prvek podautority pole, metoda vrátí. Metoda provádí žádné ověřovací testy na této hodnotě. Aplikace může volat [CSid::GetSubAuthorityCount](#getsubauthoritycount) ke zjištění rozsahu přijatelných hodnot.

> [!NOTE]
>  V části sestavení pro ladění funkce způsobí ASSERT, pokud `CSid` objekt není platný.

##  <a name="getsubauthoritycount"></a>  CSid::GetSubAuthorityCount

Vrátí počet podautority.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrácená hodnota je počet podautority.

Jestliže metoda selže, návratová hodnota není definována. Metoda selže, pokud `CSid` objekt je neplatný. Chcete-li získat rozšířené informace o chybě, volejte `GetLastError`.

> [!NOTE]
>  V části sestavení pro ladění funkce způsobí ASSERT, pokud `CSid` objekt není platný.

##  <a name="isvalid"></a>  CSid::IsValid

Testy `CSid` objekt platnost.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud `CSid` je objekt platný, FALSE. Pokud tomu tak není. Neexistuje žádné rozšířené informace o chybě pro tuto metodu; Nevolejte `GetLastError`.

### <a name="remarks"></a>Poznámky

`IsValid` Metoda ověřuje `CSid` objektu tak, že ověříte, že číslo revize je v určeném rozsahu a, počet subauthorities je menší než maximum.

##  <a name="loadaccount"></a>  CSid::LoadAccount

Aktualizace `CSid` objekt dle názvu účtu a doménu nebo existující strukturu identifikátoru SID (security identifier).

```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>Parametry

*pszAccountName*  
Název účtu.

*pszSystem*  
Název systému. Tento řetězec může být název vzdáleného počítače. Pokud tento řetězec hodnotu NULL, použije se místo toho místní systém.

*psid má*  
Ukazatel [SID](/windows/desktop/api/winnt/ns-winnt-_sid) struktury.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE. Chcete-li získat rozšířené informace o chybě, volejte `GetLastError`.

### <a name="remarks"></a>Poznámky

`LoadAccount` pokusí se najít identifikátor zabezpečení pro zadaný název. Zobrazit [LookupAccountSid](/windows/desktop/api/winbase/nf-winbase-lookupaccountsida) další podrobnosti.

##  <a name="operator_eq"></a>  CSid::operator =

Operátor přiřazení.

```
CSid& operator= (const CSid& rhs) throw(...);  
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*  
`SID` (Security identifier) nebo `CSid` přiřadit `CSid` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktualizovaný `CSid` objektu.

##  <a name="operator_eq_eq"></a>  CSid::operator ==

Testuje dva objekty popisovač zabezpečení pro rovnost.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na levé straně == – operátor.

*Zarovnání indirekce RHS*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na pravé straně == – operátor.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud popisovače zabezpečení jsou stejné, jinak hodnota FALSE.

##  <a name="operator_neq"></a>  CSid::operator! =

Testuje dva objekty popisovač zabezpečení pro nerovnost.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na levé straně! = – operátor.

*Zarovnání indirekce RHS*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na pravé straně! = – operátor.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud popisovače zabezpečení nejsou stejné; jinak hodnota FALSE.

##  <a name="operator_lt"></a>  CSid::operator &lt;

Porovná relativní hodnotu dvou objektů popisovač zabezpečení.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na levé straně! = – operátor.

*Zarovnání indirekce RHS*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na pravé straně! = – operátor.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě *lhs* je menší než *zarovnání indirekce rhs*; jinak hodnota FALSE.

##  <a name="operator_lt__eq"></a>  CSid::operator &lt;=

Porovná relativní hodnotu dvou objektů popisovač zabezpečení.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na levé straně! = – operátor.

*Zarovnání indirekce RHS*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na pravé straně! = – operátor.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě *lhs* je menší než nebo rovna hodnotě *zarovnání indirekce rhs*; jinak hodnota FALSE.

##  <a name="operator_gt"></a>  CSid::operator &gt;

Porovná relativní hodnotu dvou objektů popisovač zabezpečení.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parametry

*lhs*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na levé straně! = – operátor.

*Zarovnání indirekce RHS*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na pravé straně! = – operátor.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě *lhs* je větší než *zarovnání indirekce rhs*; jinak hodnota FALSE.

##  <a name="operator_gt__eq"></a>  CSid::operator &gt;=

Porovná relativní hodnotu dvou objektů popisovač zabezpečení.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parametry

*lhs*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na levé straně! = – operátor.

*Zarovnání indirekce RHS*  
`SID` (Security identifier) nebo `CSid` , který se zobrazí na pravé straně! = – operátor.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě *lhs* je větší než nebo rovna hodnotě *zarovnání indirekce rhs*; jinak hodnota FALSE.

##  <a name="operator_const_sid__star"></a>  CSid::operator const SID \*

Přetypování `CSid` na ukazatel na objekt `SID` strukturu (security identifier).

```  
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Vrátí adresu `SID` struktury.

##  <a name="sid"></a>  CSid::Sid

Vrátí `SID` strukturu (security identifier) jako řetězec.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `SID` struktura jako řetězec ve formátu vhodném pro zobrazení, úložiště nebo přenos. Ekvivalentní [funkce ConvertSidToStringSid](/windows/desktop/api/sddl/nf-sddl-convertsidtostringsida).

##  <a name="sidnameuse"></a>  CSid::SidNameUse

Vrátí popis stavu `CSid` objektu.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu datového člena, který ukládá hodnotu popisující stav `CSid` objektu.

|Hodnota|Popis|
|-----------|-----------------|
|SidTypeUser|Označuje uživatele `SID` (security identifier).|
|SidTypeGroup|Určuje skupinu `SID`.|
|SidTypeDomain|Určuje doménu `SID`.|
|SidTypeAlias|Signalizuje možnost vytvořit zástupce `SID`.|
|SidTypeWellKnownGroup|Označuje `SID` pro známá skupina.|
|SidTypeDeletedAccount|Označuje `SID` odstraněného účtu.|
|SidTypeInvalid|Určuje neplatnou `SID`.|
|SidTypeUnknown|Určuje neznámou `SID` typu.|
|SidTypeComputer|Označuje `SID` pro počítač.|

### <a name="remarks"></a>Poznámky

Volání [CSid::LoadAccount](#loadaccount) aktualizovat `CSid` objekt před voláním `SidNameUse` vrátit svůj stav. `SidNameUse` nedojde ke změně stavu objektu (pomocí volání do `LookupAccountName` nebo `LookupAccountSid`), ale pouze vrátí aktuální stav.

## <a name="see-also"></a>Viz také

[Ukázka zabezpečení](../../visual-cpp-samples.md)   
[Přehled tříd](../../atl/atl-class-overview.md)   
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)   
[Operátory](../../atl/reference/atl-operators.md)
