---
title: CDacl – třída
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
ms.openlocfilehash: a37ef47a4ea89d9ec24fac417e5b715bd2602fd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496932"
---
# <a name="cdacl-class"></a>CDacl – třída

Tato třída je obálkou pro seznam DACL (volitelný seznam řízení přístupu).

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CDacl : public CAcl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|Konstruktor|
|[CDacl::~CDacl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|Přidá do `CDacl` objektu povolený záznam ACE (řízení přístupu).|
|[CDacl::AddDeniedAce](#adddeniedace)|Přidá do `CDacl` objektu objekt ACE s odepřeným přístupem.|
|[CDacl::GetAceCount](#getacecount)|Vrátí počet položek řízení přístupu (ACE) v `CDacl` objektu.|
|[CDacl::RemoveAce](#removeace)|Odebere z `CDacl` objektu konkrétní položku ACE (řízení přístupu).|
|[CDacl::RemoveAllAces](#removeallaces)|Odebere všechny položky řízení přístupu obsažené v `CDacl` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CDacl:: operator =](#operator_eq)|Operátor přiřazení|

## <a name="remarks"></a>Poznámky

Popisovač zabezpečení objektu může obsahovat DACL. DACL obsahuje nula nebo více položek řízení přístupu (ACE), které identifikují uživatele a skupiny, kteří mají k tomuto objektu přístup. Pokud je seznam DACL prázdný (to znamená, že obsahuje nulové položky ACE), neudělí se přístup explicitně, takže se přístup implicitně odepře. Pokud však popisovač zabezpečení objektu nemá DACL, je objekt nechráněn a každý má úplný přístup.

Chcete-li načíst seznam DACL objektu, musíte být vlastníkem objektu nebo mít READ_CONTROL přístup k objektu. Chcete-li změnit DACL objektu, musíte mít WRITE_DAC přístup k objektu.

Použijte metody třídy poskytované k vytváření, přidávání, odebírání a odstraňování položek řízení přístupu (ACE `CDacl` ) z objektu. Viz také [AtlGetDacl](security-global-functions.md#atlgetdacl) a [AtlSetDacl](security-global-functions.md#atlsetdacl).

Úvod do modelu řízení přístupu v systému Windows naleznete v tématu [Access Control](/windows/win32/SecAuthZ/access-control) v Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="addallowedace"></a>  CDacl::AddAllowedAce

Přidá do `CDacl` objektu povolený záznam ACE (řízení přístupu).

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
Objekt [CSID](../../atl/reference/csid-class.md) .

*AccessMask*<br/>
Určuje masku přístupových práv, která mají být pro zadaný `CSid` objekt povolena.

*AceFlags*<br/>
Sada bitových příznaků, které řídí dědění ACE.

*pObjectType*<br/>
Typ objektu.

*pInheritedObjectType*<br/>
Typ zděděného objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je položka ACE přidána `CDacl` do objektu, hodnota false při selhání.

### <a name="remarks"></a>Poznámky

`CDacl` Objekt obsahuje nula nebo více položek řízení přístupu (ACE), které identifikují uživatele a skupiny, kteří mají přístup k objektu. Tato metoda přidá položku ACE, která umožňuje přístup k `CDacl` objektu.

Popis [](/windows/win32/api/winnt/ns-winnt-ace_header) různých příznaků, které lze nastavit v `AceFlags` parametru, naleznete v tématu ACE_HEADER.

##  <a name="adddeniedace"></a>CDacl::AddDeniedAce

Přidá do `CDacl` objektu zamítnutý přístup ACE (položka řízení přístupu).

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
Určuje masku přístupových práv, která se mají Odepřít pro zadaný `CSid` objekt.

*AceFlags*<br/>
Sada bitových příznaků, které řídí dědění ACE. Výchozí hodnota je 0 v prvním formuláři metody.

*pObjectType*<br/>
Typ objektu.

*pInheritedObjectType*<br/>
Typ zděděného objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je položka ACE přidána `CDacl` do objektu, hodnota false při selhání.

### <a name="remarks"></a>Poznámky

`CDacl` Objekt obsahuje nula nebo více položek řízení přístupu (ACE), které identifikují uživatele a skupiny, kteří mají přístup k objektu. Tato metoda přidá ACE, které odepře přístup k `CDacl` objektu.

Popis [](/windows/win32/api/winnt/ns-winnt-ace_header) různých příznaků, které lze nastavit v `AceFlags` parametru, naleznete v tématu ACE_HEADER.

##  <a name="cdacl"></a>CDacl::CDacl

Konstruktor

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
Existující `ACL` struktura (seznam řízení přístupu).

### <a name="remarks"></a>Poznámky

Objekt může být volitelně vytvořen pomocí existující `ACL` struktury. `CDacl` Je důležité si uvědomit, že jako tento parametr by měl být předán pouze seznam DACL (volitelný seznam řízení přístupu), nikoli seznam SACL (seznam řízení přístupu k systému). V ladicích sestaveních, předávání SACL způsobí vyhodnocení. V sestavách vydaných verzí bude předávání seznamu SACL způsobit ignorování položek ACE (řízení přístupu) v seznamu ACL a nebude k dispozici žádná chyba.

##  <a name="dtor"></a>  CDacl::~CDacl

Destruktor.

```
~CDacl () throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny prostředky, které objekt získal, včetně všech položek řízení přístupu (ACE) pomocí [CDacl:: RemoveAllAces](#removeallaces).

##  <a name="getacecount"></a>CDacl::GetAceCount

Vrátí počet položek řízení přístupu (ACE) v `CDacl` objektu.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet položek řízení přístupu obsažených v `CDacl` objektu.

##  <a name="operator_eq"></a>CDacl:: operator =

Operátor přiřazení

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
Seznam řízení přístupu (ACL) pro přiřazení k existujícímu objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktualizovaný `CDacl` objekt.

### <a name="remarks"></a>Poznámky

Měli byste se ujistit, že k této funkci budete předávat jenom DACL (volitelný seznam řízení přístupu). Předání příkazu SACL (seznam řízení přístupu k systému) do této funkce způsobí, že se v sestavení ladění vyvolá kontrolní výraz, ale v sestaveních pro vydání nedojde k žádné chybě.

##  <a name="removeace"></a>CDacl::RemoveAce

Odebere z `CDacl` objektu konkrétní položku ACE (řízení přístupu).

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky ACE, která se má odebrat

### <a name="remarks"></a>Poznámky

Tato metoda je odvozena z [CAtlArray:: funkce RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeallaces"></a>CDacl::RemoveAllAces

Odebere všechny položky řízení přístupu (ACE) obsažené v `CDacl` objektu.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Poznámky

Odebere všechny `ACE` (pokud existují) strukturu (pokud existuje) `CDacl` v objektu.

## <a name="see-also"></a>Viz také:

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[CAcl – třída](../../atl/reference/cacl-class.md)<br/>
[Seznamy ACL](/windows/win32/SecAuthZ/access-control-lists)<br/>
[ACE](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
