---
title: Třída CAcl
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
ms.openlocfilehash: 458f7cd50462a145d005f3f81d87cc06fc7e01b1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748770"
---
# <a name="cacl-class"></a>Třída CAcl

Tato třída je obálka `ACL` pro (seznam přístupu seznam) struktury.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CAcl
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Název|Popis|
|----------|-----------------|
|[CAcl::CAccessMaskArray](#caccessmaskarray)|Pole ACCESS_MASKs.|
|[CAcl::CAceFlagArray](#caceflagarray)|Pole BYT.|
|[CAcl::CAceTypeArray](#cacetypearray)|Pole BYT.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAcl::CAcl](#cacl)|Konstruktor|
|[CAcl::~CAcl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAcl::GetAceCount](#getacecount)|Vrátí počet objektů položky řízení přístupu (ACE).|
|[CAcl::GetAclEntries](#getaclentries)|Načte položky seznamu řízení přístupu (ACL) z objektu. `CAcl`|
|[CAcl::GetAclEntry](#getaclentry)|Načte všechny informace o položce `CAcl` v objektu.|
|[CAcl::GetLength](#getlength)|Vrátí délku acl.|
|[CAcl::GetPACL](#getpacl)|Vrátí hodnotu PACL (ukazatel na acl).|
|[CAcl::JePrázdný](#isempty)|Testuje `CAcl` objekt pro položky.|
|[CAcl::IsNull](#isnull)|Vrátí stav objektu. `CAcl`|
|[CAcl::RemoveAce](#removeace)|Odebere z objektu konkrétní ace (zadávání řízení přístupu). `CAcl`|
|[CAcl::RemoveAces](#removeaces)|Odebere všechny položky Řízení přístupu (položky řízení `CAcl` `CSid`přístupu) z daného .|
|[CAcl::SetEmpty](#setempty)|Označí `CAcl` objekt jako prázdný.|
|[CAcl::Nastavithodnotu](#setnull)|Označí `CAcl` objekt jako null.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAcl::operátor const ACL *](#operator_const_acl__star)|Přehodí `CAcl` objekt do `ACL` struktury.|
|[CAcl::operátor =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

Struktura `ACL` je záhlaví seznamu Řízení přístupu (seznam řízení přístupu). Seznam ACL obsahuje sekvenční seznam nula nebo více [ace](/windows/win32/SecAuthZ/access-control-entries) (položky řízení přístupu). Jednotlivé aCE v acl jsou číslovány od 0 do *n-1*, kde *n* je počet ACE v acl. Při úpravách acl aplikace odkazuje na položku řízení přístupu (ACE) v rámci acl podle jeho indexu.

Existují dva typy acl:

- Volitelného

- Systém

Volitelný seznam ACL je řízen vlastníkem objektu nebo kýmkoli, komu byl udělen přístup WRITE_DAC k objektu. Určuje přístup, který mohou mít konkrétní uživatelé a skupiny k objektu. Vlastník souboru může například použít volitelný seznam ACL k řízení, kteří uživatelé a skupiny mohou a nemohou mít k souboru přístup.

K objektu mohou být přidruženy také informace o zabezpečení na úrovni systému ve formě systémového seznamu Řízení přístupu řízeného správcem systému. Systém Ový přístup ový přístup může správci systému umožnit auditovat všechny pokusy o získání přístupu k objektu.

Další podrobnosti naleznete v diskusi [acl](/windows/win32/SecAuthZ/access-control-lists) v sadě Windows SDK.

Úvod k modelu řízení přístupu v systému Windows najdete v tématu [Řízení přístupu](/windows/win32/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="caclcaccessmaskarray"></a><a name="caccessmaskarray"></a>CAcl::CAccessMaskArray

Pole ACCESS_MASK objektů.

```
typedef CAtlArray<ACCESS_MASK> CAccessMaskArray;
```

### <a name="remarks"></a>Poznámky

Tento typedef určuje typ pole, který lze použít k ukládání přístupových práv používaných v položkách řízení přístupu (ACE).

## <a name="caclcaceflagarray"></a><a name="caceflagarray"></a>CAcl::CAceFlagArray

Pole BYT.

```
typedef CAtlArray<BYTE> CAceFlagArray;
```

### <a name="remarks"></a>Poznámky

Tento typedef určuje typ pole používaný k definování příznaků ovládacího prvku specifického pro zadávání přístupu (ACE). Úplný seznam možných příznaků naleznete v definici [ACE_HEADER.](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="caclcacetypearray"></a><a name="cacetypearray"></a>CAcl::CAceTypeArray

Pole BYT.

```
typedef CAtlArray<BYTE> CAceTypeArray;
```

### <a name="remarks"></a>Poznámky

Tento typedef určuje typ pole, který slouží k definování povahy objektů položky řízení přístupu (ACE), například ACCESS_ALLOWED_ACE_TYPE nebo ACCESS_DENIED_ACE_TYPE. Úplný seznam možných typů naleznete v definici [ACE_HEADER.](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="caclcacl"></a><a name="cacl"></a>CAcl::CAcl

Konstruktor

```
CAcl() throw();
CAcl(const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Existující objekt `CAcl`.

### <a name="remarks"></a>Poznámky

Objekt `CAcl` lze volitelně vytvořit pomocí `CAcl` existujícího objektu.

## <a name="caclcacl"></a><a name="dtor"></a>CAcl::~CAcl

Destruktor.

```
virtual ~CAcl() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny prostředky získané objektem.

## <a name="caclgetacecount"></a><a name="getacecount"></a>CAcl::GetAceCount

Vrátí počet objektů položky řízení přístupu (ACE).

```
virtual UINT GetAceCount() const throw() = 0;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet položek ACE `CAcl` v objektu.

## <a name="caclgetaclentries"></a><a name="getaclentries"></a>CAcl::GetAclEntries

Načte položky seznamu řízení přístupu (ACL) z objektu. `CAcl`

```cpp
void GetAclEntries(
    CSid::CSidArray* pSids,
    CAccessMaskArray* pAccessMasks = NULL,
    CAceTypeArray* pAceTypes = NULL,
    CAceFlagArray* pAceFlags = NULL) const throw(...);
```

### <a name="parameters"></a>Parametry

*pSids*<br/>
Ukazatel na pole [CSid](../../atl/reference/csid-class.md) objektů.

*pAccessMasky*<br/>
Přístupové masky.

*pAceTypy*<br/>
Typy položky řízení přístupu (ACE).

*pAceFlags*<br/>
ACE vlajky.

### <a name="remarks"></a>Poznámky

Tato metoda vyplní parametry pole podrobnostmi o každém `CAcl` objektu ACE obsaženém v objektu. Hodnotu NULL použijte v případě, že nejsou požadovány podrobnosti pro dané pole.

Obsah každého pole odpovídají navzájem, to znamená, že `CAccessMaskArray` první prvek pole odpovídá první `CSidArray` prvek v poli a tak dále.

Další podrobnosti o typech a vlajkách ACE najdete v [ACE_HEADER.](/windows/win32/api/winnt/ns-winnt-ace_header)

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
Index na položku ACL načíst.

*pSid*<br/>
[CSid](../../atl/reference/csid-class.md) objekt, na který se vztahuje položka ACL.

*pMask*<br/>
Maska určující oprávnění k udělení nebo odepření přístupu.

*pTyp*<br/>
Typ ACE.

*pPříznaky*<br/>
ACE vlajky.

*pObjectType*<br/>
Typ objektu. To bude nastaveno na GUID_NULL pokud typ objektu není zadán v ACE, nebo pokud ACE není objekt ACE.

*pInheritedObjectType*<br/>
Typ zděděného objektu. To bude nastaveno na GUID_NULL pokud typ zděděného objektu není zadán v ACE nebo pokud ACE není objekt ACE.

### <a name="remarks"></a>Poznámky

Tato metoda načte všechny informace o jednotlivých ACE, poskytuje více informací než [CAcl::GetAclEntries](#getaclentries) sám zpřístupní.

Další podrobnosti o typech a vlajkách ACE najdete v [ACE_HEADER.](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="caclgetlength"></a><a name="getlength"></a>CAcl::GetLength

Vrátí délku seznamu řízení přístupu (ACL).

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí požadovanou délku v bajtech, které jsou nezbytné pro uložení `ACL` struktury.

## <a name="caclgetpacl"></a><a name="getpacl"></a>CAcl::GetPACL

Vrátí ukazatel na seznam řízení přístupu (ACL).

```
const ACL* GetPACL() const throw(...);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na `ACL` strukturu.

## <a name="caclisempty"></a><a name="isempty"></a>CAcl::JePrázdný

Testuje `CAcl` objekt pro položky.

```
bool IsEmpty() const throw();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu `CAcl` PRAVDA, pokud objekt nemá hodnotu NULL a neobsahuje žádné položky. Vrátí hodnotu `CAcl` NEPRAVDA, pokud je objekt null nebo obsahuje alespoň jednu položku.

## <a name="caclisnull"></a><a name="isnull"></a>CAcl::IsNull

Vrátí stav objektu. `CAcl`

```
bool IsNull() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu `CAcl` PRAVDA, pokud je objekt null, jinak NEPRAVDA.

## <a name="cacloperator-const-acl-"></a><a name="operator_const_acl__star"></a>CAcl::operátor const ACL *

Přetypována `CAcl` objekt `ACL` (seznam řízení přístupu) struktury.

```
operator const ACL *() const throw(...);
```

### <a name="remarks"></a>Poznámky

Vrátí adresu `ACL` struktury.

## <a name="cacloperator-"></a><a name="operator_eq"></a>CAcl::operátor =

Operátor přiřazení.

```
CAcl& operator= (const CAcl& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Chcete-li `CAcl` přiřadit k existující objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na `CAcl` aktualizovaný objekt.

## <a name="caclremoveace"></a><a name="removeace"></a>CAcl::RemoveAce

Odebere z objektu konkrétní ace (zadávání řízení přístupu). `CAcl`

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky ACE odebrat.

### <a name="remarks"></a>Poznámky

Tato metoda je odvozena z [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="caclremoveaces"></a><a name="removeaces"></a>CAcl::RemoveAces

Odebere všechny Položky Řízení přístupu (položky řízení přístupu) `CAcl` z položek, které se vztahují k dané `CSid`.

```
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

Může `CAcl` být nastavena na prázdné nebo NULL: dva stavy jsou odlišné.

## <a name="caclsetnull"></a><a name="setnull"></a>CAcl::Nastavithodnotu

Označí `CAcl` objekt jako null.

```cpp
void SetNull() throw();
```

### <a name="remarks"></a>Poznámky

Může `CAcl` být nastavena na prázdné nebo NULL: dva stavy jsou odlišné.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
