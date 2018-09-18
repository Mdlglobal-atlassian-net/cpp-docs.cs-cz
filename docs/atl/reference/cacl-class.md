---
title: Cacl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAcl
- ATLSECURITY/ATL::CAcl
- ATLSECURITY/ATL::CAcl::CAccessMaskArray
- ATLSECURITY/ATL::CAcl::CAceFlagArray
- ATLSECURITY/ATL::CAcl::CAceTypeArray
- ATLSECURITY/ATL::CAcl::CAcl
- ATLSECURITY/ATL::CAcl::GetAceCount
- ATLSECURITY/ATL::CAcl::GetAclEntries
- ATLSECURITY/ATL::CAcl::GetAclEntry
- ATLSECURITY/ATL::CAcl::GetLength
- ATLSECURITY/ATL::CAcl::GetPACL
- ATLSECURITY/ATL::CAcl::IsEmpty
- ATLSECURITY/ATL::CAcl::IsNull
- ATLSECURITY/ATL::CAcl::RemoveAce
- ATLSECURITY/ATL::CAcl::RemoveAces
- ATLSECURITY/ATL::CAcl::SetEmpty
- ATLSECURITY/ATL::CAcl::SetNull
dev_langs:
- C++
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db7903dccfd851bb4bf76f1990424f887686d344
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070103"
---
# <a name="cacl-class"></a>Cacl – třída

Tato třída představuje obálku pro `ACL` struktury (seznamu řízení přístupu).

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAcl
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Pole ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Pole bajtů.|
|[CAcl::CAceTypeArray](#cacetypearray)|Pole bajtů.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|Konstruktor|
|[Cacl –:: ~ cacl –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Vrátí počet řízení přístupu položky (ACE) objekty.|
|[CAcl::GetAclEntries](#getaclentries)|Načte seznam (ACL) položky řízení přístupu z `CAcl` objektu.|
|[CAcl::GetAclEntry](#getaclentry)|Načte všechny informace o položce v `CAcl` objektu.|
|[CAcl::GetLength](#getlength)|Vrátí délku objektu seznamu ACL.|
|[CAcl::GetPACL](#getpacl)|Vrátí PACL (ukazatel na seznam ACL).|
|[CAcl::IsEmpty](#isempty)|Testy `CAcl` objektu pro položky.|
|[CAcl::IsNull](#isnull)|Vrátí stav `CAcl` objektu.|
|[CAcl::RemoveAce](#removeace)|Odebere z konkrétní ACE (položky řízení přístupu) `CAcl` objektu.|
|[CAcl::RemoveAces](#removeaces)|Odebere všechny položky řízení přístupu (položky řízení přístupu) z `CAcl` , které se týkají daný `CSid`.|
|[CAcl::SetEmpty](#setempty)|Značky `CAcl` objektu jako prázdný.|
|[CAcl::SetNull](#setnull)|Značky `CAcl` objektu jako hodnota NULL.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Seznam ACL const CAcl::operator *](#operator_const_acl__star)|Přetypování `CAcl` objektu `ACL` struktury.|
|[CAcl::operator =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

`ACL` Struktura je hlavička seznamu ACL portu (seznam řízení přístupu). Seznam ACL obsahuje sekvenční seznam nula nebo více [ACE](/windows/desktop/SecAuthZ/access-control-entries) (položky řízení přístupu). Jednotlivé položky řízení přístupu v seznamu ACL portu jsou číslovány od 0 do *n-1*, kde *n* je počet ACE v seznamu ACL. Při úpravě seznamu ACL portu, aplikace se odkazuje na záznam řízení přístupu (ACE) v rámci seznamu ACL podle jeho indexu.

Existují dva typy seznamu ACL:

- Volitelný

- Systém

Volitelný seznam řízení přístupu řídí vlastníka objektu nebo všem uživatelům oprávnění WRITE_DAC přístup k objektu. Určuje konkrétní přístup uživatele a skupiny nesmí být na objekt. Vlastníkovi souboru, například můžete použít volitelný seznam řízení přístupu na ovládací prvek, který uživatelé a skupiny může a nemůže mít přístup k souboru.

Objekt může mít také informace o zabezpečení na úrovni systému spojené s ním, ve formuláři systému řízení přístupu řídí správce systému. Systém seznamu ACL můžete povolit na správce systému a auditovat pokusy o získání přístupu k objektu.

Další podrobnosti najdete v tématu [ACL](/windows/desktop/SecAuthZ/access-control-lists) diskuze v sadě Windows SDK.

Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="caccessmaskarray"></a>  CAcl::CAccessMaskArray

Pole objektů ACCESS_MASK.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Poznámky

Tato definice typu Určuje typ pole, který slouží k ukládání přístupová práva používat v položky řízení přístupu (ACE).

##  <a name="caceflagarray"></a>  CAcl::CAceFlagArray

Pole bajtů.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Poznámky

Tato definice typu Určuje typ pole používá k definování příznaky řízení přístupu položky (ACE) specifické pro typ ovládacího prvku. Zobrazit [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) definice pro úplný seznam příznaků je to možné.

##  <a name="cacetypearray"></a>  CAcl::CAceTypeArray

Pole bajtů.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Poznámky

Tato definice typu určuje sloužících k definování povahy objektů položka (ACE) řízení přístupu, jako je například ACCESS_ALLOWED_ACE_TYPE nebo ACCESS_DENIED_ACE_TYPE typ pole. Zobrazit [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) definice pro úplný seznam možných typů.

##  <a name="cacl"></a>  CAcl::CAcl

Konstruktor

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*<br/>
Existující objekt `CAcl`.

### <a name="remarks"></a>Poznámky

`CAcl` Objekt můžete případně vytvořit pomocí existující `CAcl` objektu.

##  <a name="dtor"></a>  Cacl –:: ~ cacl –

Destruktor.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny prostředky získané v objektu.

##  <a name="getacecount"></a>  CAcl::GetAceCount

Vrátí počet řízení přístupu položky (ACE) objekty.

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet položek ACE v `CAcl` objektu.

##  <a name="getaclentries"></a>  CAcl::GetAclEntries

Načte seznam (ACL) položky řízení přístupu z `CAcl` objektu.

```
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSids*<br/>
Ukazatel na pole [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objekty.

*pAccessMasks*<br/>
Masky přístupu.

*pAceTypes*<br/>
Typy vstupu (ACE) řízení přístupu.

*pAceFlags*<br/>
Příznaky ACE.

### <a name="remarks"></a>Poznámky

Tato metoda vyplní pole parametrů s podrobnostmi o každého objektu ACE součástí `CAcl` objektu. Když podrobnosti pro toto konkrétní pole nejsou vyžadovány, použijte hodnotu NULL.

Obsah každého pole odpovídat k sobě navzájem, tedy první prvek `CAccessMaskArray` pole odpovídá na první prvek v `CSidArray` pole a tak dále.

Zobrazit [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) podrobné informace o typech ACE a příznaky.

##  <a name="getaclentry"></a>  CAcl::GetAclEntry

Načte všechny informace o položce v seznamu řízení přístupu (ACL).

```
void GetAclEntry(
    UINT nIndex,
    CSid* pSid,
    ACCESS_MASK* pMask = NULL,
    BYTE* pType = NULL,
    BYTE* pFlags = NULL,
    GUID* pObjectType = NULL,
    GUID* pInheritedObjectType = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index k položce seznamu ACL k načtení.

*psid má*<br/>
[Identifikační číslo volané stanice](../../atl/reference/csid-class.md) objektu, pro kterou platí položce seznamu ACL.

*pMask*<br/>
Maska určující oprávnění udělit nebo odepřít přístup.

*pType*<br/>
Typu položky ACE.

*pFlags*<br/>
Příznaky ACE.

*pObjectType*<br/>
Typ objektu. Tím se nastaví na GUID_NULL Pokud není zadán typ objektu v ACE nebo pokud je položka řízení přístupu není objektu ACE.

*pInheritedObjectType*<br/>
Typ zděděných objektů. Tím se nastaví na GUID_NULL Pokud není zadaný typ zděděných objektů v této položky řízení přístupu, nebo pokud ACE není objektu ACE.

### <a name="remarks"></a>Poznámky

Tato metoda se načtou všechny informace o jednotlivých prostředí ACE poskytnutí dalších informací, než [CAcl::GetAclEntries](#getaclentries) samostatně zpřístupňuje.

Zobrazit [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) podrobné informace o typech ACE a příznaky.

##  <a name="getlength"></a>  CAcl::GetLength

Vrátí délku objektu seznamu řízení přístupu (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí má požadovanou délku v bajtech nezbytné pro uchování `ACL` struktury.

##  <a name="getpacl"></a>  CAcl::GetPACL

Vrací ukazatel na seznam řízení přístupu (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel `ACL` struktury.

##  <a name="isempty"></a>  CAcl::IsEmpty

Testy `CAcl` objektu pro položky.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí TRUE, pokud `CAcl` objekt nemá hodnotu NULL a neobsahuje žádné položky. Vrátí hodnotu FALSE, pokud `CAcl` objekt má hodnotu NULL nebo obsahuje alespoň jednu položku.

##  <a name="isnull"></a>  CAcl::IsNull

Vrátí stav `CAcl` objektu.

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud `CAcl` objekt má hodnotu NULL, hodnota FALSE v opačném případě.

##  <a name="operator_const_acl__star"></a>  Seznam ACL const CAcl::operator *

Přetypování `CAcl` objektu `ACL` struktury (seznamu řízení přístupu).

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Vrátí adresu `ACL` struktury.

##  <a name="operator_eq"></a>  CAcl::operator =

Operátor přiřazení.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*<br/>
`CAcl` Přiřadit existující objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktualizovaný `CAcl` objektu.

##  <a name="removeace"></a>  CAcl::RemoveAce

Odebere z konkrétní ACE (položky řízení přístupu) `CAcl` objektu.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky ACE odebrat.

### <a name="remarks"></a>Poznámky

Tato metoda je odvozen z [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeaces"></a>  CAcl::RemoveAces

Zruší alls položky řízení přístupu (položky řízení přístupu) `CAcl` , které se týkají daný `CSid`.

```
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Odkaz na `CSid` objektu.

##  <a name="setempty"></a>  CAcl::SetEmpty

Značky `CAcl` objektu jako prázdný.

```
void SetEmpty() throw();
```

### <a name="remarks"></a>Poznámky

`CAcl` Lze nastavit na prázdnou nebo na hodnotu NULL: dva stavy se liší.

##  <a name="setnull"></a>  CAcl::SetNull

Značky `CAcl` objektu jako hodnota NULL.

```
void SetNull() throw();
```

### <a name="remarks"></a>Poznámky

`CAcl` Lze nastavit na prázdnou nebo na hodnotu NULL: dva stavy se liší.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
