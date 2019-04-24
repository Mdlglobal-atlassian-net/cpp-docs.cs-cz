---
title: Cdacl – třída
ms.date: 11/04/2016
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
ms.openlocfilehash: 1beac6106b825c775012b85ccd01226c3dfab795
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258959"
---
# <a name="cdacl-class"></a>Cdacl – třída

Tato třída představuje obálku pro strukturu DACL (seznam volitelných řízení přístupu).

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CDacl : public CAcl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|Konstruktor|
|[CDacl::~CDacl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|Přidá povolený ACE (položky řízení přístupu) `CDacl` objektu.|
|[CDacl::AddDeniedAce](#adddeniedace)|Přidá ACE odepření `CDacl` objektu.|
|[CDacl::GetAceCount](#getacecount)|Vrátí počet položek řízení přístupu (položky řízení přístupu) `CDacl` objektu.|
|[CDacl::RemoveAce](#removeace)|Odebere z konkrétní ACE (položky řízení přístupu) `CDacl` objektu.|
|[CDacl::RemoveAllAces](#removeallaces)|Odebere všechny položky obsažené v řízení přístupu `CDacl` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CDacl::operator =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

Popisovač zabezpečení objektu může obsahovat seznam DACL. DACL obsahuje nula nebo víc položek řízení přístupu (položky řízení přístupu), které identifikují uživatele a skupiny, kteří mohou přistupovat k objektu. Pokud je prázdný DACL (to znamená, neobsahuje žádnou ACE), přístup se explicitně udělí oprávnění, takže implicitně byl odepřen přístup. Pokud není popisovač zabezpečení objektu DACL, objekt není chráněný a všichni mají úplný přístup.

K načtení objektu DACL, musí být vlastníka objektu nebo mít READ_CONTROL přístup k objektu. Chcete-li změnit DACL objektu, musíte mít WRITE_DAC přístup k objektu.

Použití metod třídy zadaná k vytvoření, přidat, odebrat nebo odstranit položky řízení přístupu z `CDacl` objektu. Viz také [AtlGetDacl](security-global-functions.md#atlgetdacl) a [AtlSetDacl](security-global-functions.md#atlsetdacl).

Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="addallowedace"></a>  CDacl::AddAllowedAce

Přidá povolený ACE (položky řízení přístupu) `CDacl` objektu.

```
bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
A [identifikační číslo volané stanice](../../atl/reference/csid-class.md) objektu.

*AccessMask*<br/>
Určuje masku přístupová práva, povolit pro danou `CSid` objektu.

*AceFlags*<br/>
Sadu bitových příznaků, které řídí ACE dědičnosti.

*pObjectType*<br/>
Typ objektu.

*pInheritedObjectType*<br/>
Typ zděděných objektů.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud je položka řízení přístupu se přidá do `CDacl` objektu NEPRAVDA při selhání.

### <a name="remarks"></a>Poznámky

A `CDacl` objekt obsahuje nula nebo víc položek řízení přístupu (položky řízení přístupu), které identifikují uživatele a skupiny, kteří mohou přistupovat k objektu. Tato metoda přidá ACE, která umožňuje přístup k `CDacl` objektu.

Zobrazit [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) popis různé příznaky, které je možné nastavit v `AceFlags` parametru.

##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce

Přidá k odepření přístupu (položky řízení přístupu) `CDacl` objektu.

```
bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
A `CSid` objektu.

*AccessMask*<br/>
Určuje masku přístupová práva k odepřen pro zadaný rozbočovač `CSid` objektu.

*AceFlags*<br/>
Sadu bitových příznaků, které řídí ACE dědičnosti. Výchozí hodnota je 0 v prvním metody.

*pObjectType*<br/>
Typ objektu.

*pInheritedObjectType*<br/>
Typ zděděných objektů.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud je položka řízení přístupu se přidá do `CDacl` objektu NEPRAVDA při selhání.

### <a name="remarks"></a>Poznámky

A `CDacl` objekt obsahuje nula nebo víc položek řízení přístupu (položky řízení přístupu), které identifikují uživatele a skupiny, kteří mohou přistupovat k objektu. Tato metoda přidá ACE odepření přístupu k `CDacl` objektu.

Zobrazit [ACE_HEADER](/windows/desktop/api/winnt/ns-winnt-_ace_header) popis různé příznaky, které je možné nastavit v `AceFlags` parametru.

##  <a name="cdacl"></a>  CDacl::CDacl

Konstruktor

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*<br/>
Existující `ACL` struktury (seznamu řízení přístupu).

### <a name="remarks"></a>Poznámky

`CDacl` Objekt můžete případně vytvořit pomocí existující `ACL` struktury. Je důležité si uvědomit pouze DACL (seznam volitelných řízení přístupu), a ne SACL (seznam řízení přístupu systému), by měly být předány jako tento parametr. V ladicím buildu předávání SACL způsobí vyhodnocení. V sestaveních pro vydání předávání SACL způsobí, že položky řízení přístupu (položky řízení přístupu) v seznamu ACL k ignorovat a dojde k žádné chybě.

##  <a name="dtor"></a>  CDacl::~CDacl

Destruktor.

```
~CDacl () throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny prostředky získané v objektu, včetně všech položek řízení přístupu (položky řízení přístupu) pomocí [CDacl::RemoveAllAces](#removeallaces).

##  <a name="getacecount"></a>  CDacl::GetAceCount

Vrátí počet položek řízení přístupu (položky řízení přístupu) `CDacl` objektu.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet součástí položky řízení přístupu `CDacl` objektu.

##  <a name="operator_eq"></a>  CDacl::operator =

Operátor přiřazení.

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*Zarovnání indirekce RHS*<br/>
Seznam ACL (seznam řízení přístupu) přiřadit existující objekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktualizovaný `CDacl` objektu.

### <a name="remarks"></a>Poznámky

Měli byste zajistit, že předáte pouze DACL (seznam volitelných řízení přístupu) pro tuto funkci. Předání SACL (seznam řízení přístupu systému) pro tuto funkci způsobí, že ASSERT v sestavení ladění, ale způsobí, že žádná chyba v sestaveních pro vydání.

##  <a name="removeace"></a>  CDacl::RemoveAce

Odebere z konkrétní ACE (položky řízení přístupu) `CDacl` objektu.

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky ACE odebrat.

### <a name="remarks"></a>Poznámky

Tato metoda je odvozen z [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeallaces"></a>  CDacl::RemoveAllAces

Odebere všechny položky řízení přístupu (položky řízení přístupu) součástí `CDacl` objektu.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Poznámky

Odebere všechny `ACE` strukturu (položky řízení přístupu) (pokud existuje) v `CDacl` objektu.

## <a name="see-also"></a>Viz také:

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[CAcl – třída](../../atl/reference/cacl-class.md)<br/>
[Seznamy ACL](/windows/desktop/SecAuthZ/access-control-lists)<br/>
[Položky řízení přístupu](/windows/desktop/SecAuthZ/access-control-entries)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
