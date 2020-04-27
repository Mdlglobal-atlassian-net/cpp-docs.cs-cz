---
title: CAcl – třída
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAcl class
ms.assetid: 20bcb9af-dc1c-4737-b923-3864776680d6
ms.openlocfilehash: 3beef0fc6a75a952956f032d3e0e4cbe4faed86b
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168446"
---
# <a name="cacl-class"></a>CAcl – třída

Tato třída je obálkou struktury `ACL` (seznam řízení přístupu).

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class CAcl
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Pole ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Pole bajtů.|
|[CAcl::CAceTypeArray](#cacetypearray)|Pole bajtů.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|Konstruktor|
|[CAcl:: ~ CAcl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Vrátí počet objektů ACE (Access Control Entry).|
|[CAcl::GetAclEntries](#getaclentries)|Načte položky seznamu řízení přístupu (ACL) z `CAcl` objektu.|
|[CAcl::GetAclEntry](#getaclentry)|Načte všechny informace o položce v `CAcl` objektu.|
|[CAcl:: GetLength](#getlength)|Vrátí délku seznamu ACL.|
|[CAcl::GetPACL](#getpacl)|Vrátí PACL (ukazatel na seznam ACL).|
|[CAcl::-Empty](#isempty)|Testuje `CAcl` objekt pro položky.|
|[CAcl:: IsNull](#isnull)|Vrátí stav `CAcl` objektu.|
|[CAcl::RemoveAce](#removeace)|Odebere z `CAcl` objektu konkrétní položku ACE (řízení přístupu).|
|[CAcl::RemoveAces](#removeaces)|Odebere všechny položky řízení přístupu (ACE) z rozhraní `CAcl` , které platí pro daný. `CSid`|
|[CAcl::SetEmpty](#setempty)|Označí `CAcl` objekt jako prázdný.|
|[CAcl::SetNull](#setnull)|Označí `CAcl` objekt jako null.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAcl:: operator – seznam ACL *](#operator_const_acl__star)|Přetypování `CAcl` objektu na `ACL` strukturu.|
|[CAcl:: operator =](#operator_eq)|Operátor přiřazení|

## <a name="remarks"></a>Poznámky

`ACL` Struktura je hlavičkou seznamu řízení přístupu (ACL). Seznam ACL zahrnuje sekvenční seznam nula nebo více položek [ACE](/windows/win32/SecAuthZ/access-control-entries) (položky řízení přístupu). Jednotlivé položky ACE v seznamu ACL jsou číslovány od 0 do *n-1*, kde *n* je počet položek ACE v seznamu ACL. Když upravujete seznam řízení přístupu (ACL), aplikace odkazuje na položku řízení přístupu (ACE) v seznamu ACL podle jejího indexu.

Existují dva typy seznamů ACL:

- Volitelného

- Systém

Volitelný seznam ACL je řízen vlastníkem objektu nebo kýmkoli uděleným WRITE_DAC přístup k objektu. Určuje přístup konkrétního uživatele a skupiny může být objektem. Vlastník souboru může například použít volitelný seznam řízení přístupu (ACL), který řídí, kteří uživatelé a skupiny můžou a nemají přístup k tomuto souboru.

Objekt může mít také související informace o zabezpečení na úrovni systému, ve formě seznamu ACL systému, který je řízen správcem systému. Seznam řízení přístupu k systému může správcům systému umožnit auditovat jakékoli pokusy o získání přístupu k objektu.

Další podrobnosti najdete v diskuzi [ACL](/windows/win32/SecAuthZ/access-control-lists) v Windows SDK.

Úvod do modelu řízení přístupu v systému Windows naleznete v tématu [Access Control](/windows/win32/SecAuthZ/access-control) v Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

## <a name="caclcaccessmaskarray"></a><a name="caccessmaskarray"></a>CAcl::CAccessMaskArray

Pole objektů ACCESS_MASK.

```cpp
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Poznámky

Tato definice typedef určuje typ pole, které lze použít k uložení přístupových práv používaných v položkách řízení přístupu (ACE).

## <a name="caclcaceflagarray"></a><a name="caceflagarray"></a>CAcl::CAceFlagArray

Pole bajtů.

```cpp
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Poznámky

Tato definice typedef určuje typ pole, který slouží k definování příznaků ovládacího prvku specifického pro položku řízení přístupu (ACE). Úplný seznam možných příznaků najdete v části definice [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

## <a name="caclcacetypearray"></a><a name="cacetypearray"></a>CAcl::CAceTypeArray

Pole bajtů.

```cpp
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Poznámky

Tato definice typedef určuje typ pole, který slouží k definování povahy objektů řízení přístupu (ACE), například ACCESS_ALLOWED_ACE_TYPE nebo ACCESS_DENIED_ACE_TYPE. Úplný seznam možných typů najdete v tématu Definice [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

## <a name="caclcacl"></a><a name="cacl"></a>CAcl::CAcl

Konstruktor

```cpp
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
Existující objekt `CAcl`.

### <a name="remarks"></a>Poznámky

`CAcl` Objekt lze volitelně vytvořit pomocí existujícího `CAcl` objektu.

## <a name="caclcacl"></a><a name="dtor"></a>CAcl:: ~ CAcl

Destruktor.

```cpp
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny prostředky, které objekt získal.

## <a name="caclgetacecount"></a><a name="getacecount"></a>CAcl::GetAceCount

Vrátí počet objektů ACE (Access Control Entry).

```cpp
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet položek ACE v `CAcl` objektu.

## <a name="caclgetaclentries"></a><a name="getaclentries"></a>CAcl::GetAclEntries

Načte položky seznamu řízení přístupu (ACL) z `CAcl` objektu.

```cpp
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSids*<br/>
Ukazatel na pole objektů [CSID](../../atl/reference/csid-class.md) .

*pAccessMasks*<br/>
Masky přístupu.

*pAceTypes*<br/>
Typy položek řízení přístupu (ACE).

*pAceFlags*<br/>
Příznaky ACE.

### <a name="remarks"></a>Poznámky

Tato metoda vyplní parametry pole podrobnostmi všech objektů ACE obsažených v `CAcl` objektu. Pokud nejsou požadovány podrobnosti pro dané pole, použijte hodnotu NULL.

Obsah každého pole odpovídá sobě navzájem, tedy první prvek `CAccessMaskArray` pole odpovídá prvnímu prvku v `CSidArray` poli a tak dále.

Další podrobnosti o typech a příznacích ACE najdete v tématu [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

## <a name="caclgetaclentry"></a><a name="getaclentry"></a>CAcl::GetAclEntry

Načte všechny informace o položce v seznamu řízení přístupu (ACL).

```cpp
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
Index položky seznamu ACL, která se má načíst

*PSID má*<br/>
Objekt [CSID](../../atl/reference/csid-class.md) , na který se vztahuje položka seznamu ACL.

*pMask*<br/>
Maska určující oprávnění pro udělení nebo zamítnutí přístupu.

*pType*<br/>
Typ ACE.

*pFlags*<br/>
Příznaky ACE.

*pObjectType*<br/>
Typ objektu. Tato položka se nastaví na GUID_NULL, pokud typ objektu není zadaný v ACE, nebo pokud ACE není OBJEKTem ACE.

*pInheritedObjectType*<br/>
Typ zděděného objektu. Tato akce bude nastavena na GUID_NULL, pokud není v ACE uveden zděděný typ objektu, nebo pokud ACE není OBJEKTem ACE.

### <a name="remarks"></a>Poznámky

Tato metoda načte všechny informace o individuální položce ACE a poskytne více informací, než [CACL:: GetAclEntries](#getaclentries) zpřístupňuje sám.

Další podrobnosti o typech a příznacích ACE najdete v tématu [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

## <a name="caclgetlength"></a><a name="getlength"></a>CAcl:: GetLength

Vrátí délku seznamu řízení přístupu (ACL).

```cpp
UINT GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí požadovanou délku v bajtech potřebných k uložení `ACL` struktury.

## <a name="caclgetpacl"></a><a name="getpacl"></a>CAcl::GetPACL

Vrátí ukazatel na seznam řízení přístupu (ACL).

```cpp
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `ACL` strukturu.

## <a name="caclisempty"></a><a name="isempty"></a>CAcl::-Empty

Testuje `CAcl` objekt pro položky.

```cpp
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu TRUE, `CAcl` Pokud objekt není null a neobsahuje žádné položky. Vrátí hodnotu FALSE, `CAcl` Pokud má objekt hodnotu null nebo obsahuje alespoň jednu položku.

## <a name="caclisnull"></a><a name="isnull"></a>CAcl:: IsNull

Vrátí stav `CAcl` objektu.

```cpp
bool IsNull() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, `CAcl` Pokud je objekt null, jinak false.

## <a name="cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a>CAcl:: operator – seznam ACL *

Přetypování `CAcl` objektu na strukturu `ACL` (seznam řízení přístupu).

```cpp
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Vrátí adresu `ACL` struktury.

## <a name="cacloperator-"></a><a name="operator_eq"></a>CAcl:: operator =

Operátor přiřazení

```cpp
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
`CAcl` Pro přiřazení k existujícímu objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktualizovaný `CAcl` objekt.

## <a name="caclremoveace"></a><a name="removeace"></a>CAcl::RemoveAce

Odebere z `CAcl` objektu konkrétní položku ACE (řízení přístupu).

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky ACE, která se má odebrat

### <a name="remarks"></a>Poznámky

Tato metoda je odvozena z [CAtlArray:: funkce RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="caclremoveaces"></a><a name="removeaces"></a>CAcl::RemoveAces

Odebere Alls ACE (položky řízení přístupu) z rozhraní `CAcl` , které platí pro daný. `CSid`

```cpp
bool RemoveAces(const CSid& rSid) throw(...)
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
Odkaz na `CSid` objekt.

## <a name="caclsetempty"></a><a name="setempty"></a>CAcl::SetEmpty

Označí `CAcl` objekt jako prázdný.

```cpp
void SetEmpty() throw();
```

### <a name="remarks"></a>Poznámky

`CAcl` Lze nastavit na hodnotu Empty nebo na hodnotu null: tyto dva stavy jsou odlišné.

## <a name="caclsetnull"></a><a name="setnull"></a>CAcl::SetNull

Označí `CAcl` objekt jako null.

```cpp
void SetNull() throw();
```

### <a name="remarks"></a>Poznámky

`CAcl` Lze nastavit na hodnotu Empty nebo na hodnotu null: tyto dva stavy jsou odlišné.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
