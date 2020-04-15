---
title: Třída CDacl
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
ms.openlocfilehash: 1540c90e3538d763708e161ba6c1a5e459bb2bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327142"
---
# <a name="cdacl-class"></a>Třída CDacl

Tato třída je obálka pro strukturu DACL (volitelný seznam řízení přístupu).

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CDacl : public CAcl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|Konstruktor|
|[CDacl::~CDacl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|Přidá k objektu povolenou položku `CDacl` ACE (položka řízení přístupu).|
|[CDacl::AddDeniedAce](#adddeniedace)|Přidá odepřené ACE `CDacl` k objektu.|
|[CDacl::GetAceCount](#getacecount)|Vrátí počet položek Řízení přístupu (položky `CDacl` řízení přístupu) v objektu.|
|[CDacl::RemoveAce](#removeace)|Odebere z objektu konkrétní ace (zadávání řízení přístupu). `CDacl`|
|[CDacl::OdstranitAllAces](#removeallaces)|Odebere všechny ACE obsažené v `CDacl` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CDacl::operátor =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

Popisovač zabezpečení objektu může obsahovat seznam DACL. Seznam DACL obsahuje nula nebo více položek Řízení přístupu (položky řízení přístupu), které identifikují uživatele a skupiny, kteří mají přístup k objektu. Pokud dacl je prázdný (to znamená, že obsahuje nula ACE), žádný přístup je explicitně udělena, takže přístup je implicitně odepřen. Pokud však popisovač zabezpečení objektu nemá seznam DACL, objekt není chráněn a všichni mají úplný přístup.

Chcete-li načíst dacl objektu, musíte být vlastníkem objektu nebo mít READ_CONTROL přístup k objektu. Chcete-li změnit dacl objektu, musíte mít WRITE_DAC přístup k objektu.

Pomocí metod třídy, které jsou k dispozici, můžete vytvořit, přidat, odebrat a odstranit ace z objektu. `CDacl` Viz také [AtlGetDacl](security-global-functions.md#atlgetdacl) a [AtlSetDacl](security-global-functions.md#atlsetdacl).

Úvod k modelu řízení přístupu v systému Windows najdete v tématu [Řízení přístupu](/windows/win32/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cacl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="cdacladdallowedace"></a><a name="addallowedace"></a>CDacl::AddAllowedAce

Přidá k objektu povolenou položku `CDacl` ACE (položka řízení přístupu).

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
[CSid](../../atl/reference/csid-class.md) objekt.

*Maska přístupu*<br/>
Určuje masku přístupových práv, která `CSid` mají být povolena pro zadaný objekt.

*AceFlags*<br/>
Sada bitových příznaků, které řídí dědičnost ACE.

*pObjectType*<br/>
Typ objektu.

*pInheritedObjectType*<br/>
Typ zděděného objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud `CDacl` je ace přidána k objektu, NEPRAVDA při selhání.

### <a name="remarks"></a>Poznámky

Objekt `CDacl` obsahuje nula nebo více položek ACE (položky řízení přístupu), které identifikují uživatele a skupiny, kteří mají přístup k objektu. Tato metoda přidá ACE, který `CDacl` umožňuje přístup k objektu.

Viz [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) popis různých příznaků, které lze `AceFlags` nastavit v parametru.

## <a name="cdacladddeniedace"></a><a name="adddeniedace"></a>CDacl::AddDeniedAce

Přidá k objektu odepřené ace `CDacl` (položka řízení přístupu).

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
Objekt. `CSid`

*Maska přístupu*<br/>
Určuje masku přístupových práv, která `CSid` mají být odepřena pro zadaný objekt.

*AceFlags*<br/>
Sada bitových příznaků, které řídí dědičnost ACE. Výchozí hodnota je 0 v první podobě metody.

*pObjectType*<br/>
Typ objektu.

*pInheritedObjectType*<br/>
Typ zděděného objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud `CDacl` je ace přidána k objektu, NEPRAVDA při selhání.

### <a name="remarks"></a>Poznámky

Objekt `CDacl` obsahuje nula nebo více položek ACE (položky řízení přístupu), které identifikují uživatele a skupiny, kteří mají přístup k objektu. Tato metoda přidá ACE, který `CDacl` odepře přístup k objektu.

Viz [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) popis různých příznaků, které lze `AceFlags` nastavit v parametru.

## <a name="cdaclcdacl"></a><a name="cdacl"></a>CDacl::CDacl

Konstruktor

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Existující `ACL` struktura (seznam řízení přístupu).

### <a name="remarks"></a>Poznámky

Objekt `CDacl` lze volitelně vytvořit pomocí `ACL` existující struktury. Je důležité si uvědomit, že pouze DACL (volitelný seznam řízení přístupu), a nikoli Seznam SACL (seznam řízení přístupu systému), by měly být předány jako tento parametr. V sestavení ladění předávání SACL způsobí ASSERT. V sestavení verze předávání sacl způsobí, že ACE (položky řízení přístupu) v acl ignorovány a dojde k žádné chybě.

## <a name="cdaclcdacl"></a><a name="dtor"></a>CDacl::~CDacl

Destruktor.

```
~CDacl () throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny prostředky získané objektem, včetně všech položek Řízení přístupu (položky řízení přístupu) pomocí [CDacl::RemoveAllAces](#removeallaces).

## <a name="cdaclgetacecount"></a><a name="getacecount"></a>CDacl::GetAceCount

Vrátí počet položek Řízení přístupu (položky `CDacl` řízení přístupu) v objektu.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet objektů Řízení a řízení `CDacl` obsažených v objektu.

## <a name="cdacloperator-"></a><a name="operator_eq"></a>CDacl::operátor =

Operátor přiřazení.

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Seznam ACL (seznam řízení přístupu), který chcete přiřadit existujícímu objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na `CDacl` aktualizovaný objekt.

### <a name="remarks"></a>Poznámky

Měli byste zajistit, že do této funkce předáte pouze seznam DACL (volitelný seznam řízení přístupu). Předání seznamu SACL (seznam řízení přístupu k systému) do této funkce způsobí ASSERT v sestaveních ladění, ale způsobí žádnou chybu v sestaveních verzí.

## <a name="cdaclremoveace"></a><a name="removeace"></a>CDacl::RemoveAce

Odebere z objektu konkrétní ace (zadávání řízení přístupu). `CDacl`

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky ACE odebrat.

### <a name="remarks"></a>Poznámky

Tato metoda je odvozena z [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="cdaclremoveallaces"></a><a name="removeallaces"></a>CDacl::OdstranitAllAces

Odebere všechny položky ACE (položky řízení přístupu) obsažené v objektu. `CDacl`

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Poznámky

Odebere `ACE` všechny (access-control entry) struktury (pokud existuje) v objektu. `CDacl`

## <a name="see-also"></a>Viz také

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[Třída CAcl](../../atl/reference/cacl-class.md)<br/>
[Seznamy acl](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Esa](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
