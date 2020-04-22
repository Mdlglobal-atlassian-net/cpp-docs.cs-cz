---
title: Třída CSacl
ms.date: 11/04/2016
f1_keywords:
- CSacl
- ATLSECURITY/ATL::CSacl
- ATLSECURITY/ATL::CSacl::CSacl
- ATLSECURITY/ATL::CSacl::AddAuditAce
- ATLSECURITY/ATL::CSacl::GetAceCount
- ATLSECURITY/ATL::CSacl::RemoveAce
- ATLSECURITY/ATL::CSacl::RemoveAllAces
helpviewer_keywords:
- CSacl class
ms.assetid: 8624889b-aebc-4183-9d29-a20f07837f05
ms.openlocfilehash: d5a060555901361ef6c70c6a4f801605eafd92cf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746547"
---
# <a name="csacl-class"></a>Třída CSacl

Tato třída je obálka pro strukturu SACL (seznam řízení přístupu systému).

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSacl : public CAcl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSacl::CSacl](#csacl)|Konstruktor|
|[CSacl::~CSacl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSacl::AddAuditAce](#addauditace)|Přidá do objektu položku řízení přístupu k auditu `CSacl` (ACE).|
|[CSacl::GetAceCount](#getacecount)|Vrátí počet položek řízení přístupu (ACE) `CSacl` v objektu.|
|[CSacl::RemoveAce](#removeace)|Odebere z objektu konkrétní ace (zadávání řízení přístupu). `CSacl`|
|[CSacl::OdstranitAllAces](#removeallaces)|Odebere všechny ACE obsažené v `CSacl` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CSacl::operátor =](#operator_eq)|Operátor přiřazení.|

## <a name="remarks"></a>Poznámky

SACL obsahuje položky řízení přístupu (ACE), které určují typy pokusů o přístup, které generují záznamy auditu v protokolu událostí zabezpečení řadiče domény. Všimněte si, že sacl generuje položky protokolu pouze na řadiči domény, kde došlo k pokusu o přístup, nikoli na každém řadiči domény, který obsahuje repliku objektu.

Chcete-li nastavit nebo načíst kód SACL v popisovači zabezpečení objektu, musí být v přístupovém tokenu žádajícího vlákna povoleno oprávnění SE_SECURITY_NAME. Skupina administrators má toto oprávnění udělené ve výchozím nastavení a může být uděleno jiným uživatelům nebo skupinám. Udělení oprávnění není vše, co je požadováno: před provedením operace definované oprávnění, musí být oprávnění povoleno v tokenu přístupu zabezpečení, aby se projevilo. Model umožňuje oprávnění, která mají být povolena pouze pro určité systémové operace a potom zakázána, pokud již nejsou potřeba. Viz [AtlGetSacl](security-global-functions.md#atlgetsacl) a [AtlSetSacl](security-global-functions.md#atlsetsacl) příklady povolení SE_SECURITY_NAME.

Pomocí metod třídy, které jsou k dispozici, přidejte, `SACL` odeberte, vytvořte a odstraňte ace z objektu. Viz také [AtlGetSacl](security-global-functions.md#atlgetsacl) a [AtlSetSacl](security-global-functions.md#atlsetsacl).

Úvod k modelu řízení přístupu v systému Windows najdete v tématu [Řízení přístupu](/windows/win32/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cacl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="csacladdauditace"></a><a name="addauditace"></a>CSacl::AddAuditAce

Přidá do objektu položku řízení přístupu k auditu `CSacl` (ACE).

```
bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags = 0) throw(...);

bool AddAuditAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    bool bSuccess,
    bool bFailure,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>Parametry

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md) objekt.

*Maska přístupu*<br/>
Určuje masku přístupových práv, která mají `CSid` být auditována pro zadaný objekt.

*bÚspěch*<br/>
Určuje, zda mají být auditovány pokusy o povolený přístup. Nastavte tento příznak na hodnotu true, aby bylo možné auditovat; v opačném případě nastavte na hodnotu false.

*bSelhání*<br/>
Určuje, zda mají být auditovány pokusy o odepření přístupu. Nastavte tento příznak na hodnotu true, aby bylo možné auditovat; v opačném případě nastavte na hodnotu false.

*AceFlags*<br/>
Sada bitových příznaků, které řídí dědičnost ACE.

*pObjectType*<br/>
Typ objektu.

*pInheritedObjectType*<br/>
Typ zděděného objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud `CSacl` je ace přidána k objektu, NEPRAVDA při selhání.

### <a name="remarks"></a>Poznámky

Objekt `CSacl` obsahuje položky řízení přístupu (ACE), které určují typy pokusů o přístup, které generují záznamy auditu v protokolu událostí zabezpečení. Tato metoda přidá takové ACE k objektu. `CSacl`

Popis různých příznaků, které lze nastavit v parametru *AceFlags,* naleznete v [ACE_HEADER.](/windows/win32/api/winnt/ns-winnt-ace_header)

## <a name="csaclcsacl"></a><a name="csacl"></a>CSacl::CSacl

Konstruktor

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
Existující `ACL` struktura (seznam řízení přístupu).

### <a name="remarks"></a>Poznámky

Objekt `CSacl` lze volitelně vytvořit pomocí `ACL` existující struktury. Ujistěte se, že tento parametr je seznam řízení přístupu systému (SACL) a nikoli volitelný seznam řízení přístupu (DACL). V sestavení ladění, pokud dacl je zadán kontrolní výraz dojde. Ve verzi sestavení všechny položky z DACL jsou ignorovány.

## <a name="csaclcsacl"></a><a name="dtor"></a>CSacl::~CSacl

Destruktor.

```
~CSacl() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny prostředky získané objektem, včetně všech položek řízení přístupu (ACE).

## <a name="csaclgetacecount"></a><a name="getacecount"></a>CSacl::GetAceCount

Vrátí počet položek řízení přístupu (ACE) `CSacl` v objektu.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet objektů Řízení a řízení `CSacl` obsažených v objektu.

## <a name="csacloperator-"></a><a name="operator_eq"></a>CSacl::operátor =

Operátor přiřazení.

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*rhs*<br/>
(Seznam `ACL` řízení přístupu) přiřadit k existujícíobjekt.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na `CSacl` aktualizovaný objekt. Ujistěte `ACL` se, že parametr je ve skutečnosti seznam řízení přístupu systému (SACL) a nikoli volitelný seznam řízení přístupu (DACL). V sestavení ladění dojde k kontrolnímu výrazu `ACL` a ve verzi sestavení bude parametr ignorován.

## <a name="csaclremoveace"></a><a name="removeace"></a>CSacl::RemoveAce

Odebere z objektu konkrétní ace (zadávání řízení přístupu). `CSacl`

```cpp
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky ACE odebrat.

### <a name="remarks"></a>Poznámky

Tato metoda je odvozena z [CAtlArray::RemoveAt](../../atl/reference/catlarray-class.md#removeat).

## <a name="csaclremoveallaces"></a><a name="removeallaces"></a>CSacl::OdstranitAllAces

Odebere všechny položky řízení přístupu (ACE) `CSacl` obsažené v objektu.

```cpp
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Poznámky

Odebere `ACE` všechny struktury (pokud `CSacl` existuje) v objektu.

## <a name="see-also"></a>Viz také

[Třída CAcl](../../atl/reference/cacl-class.md)<br/>
[Seznamy acl](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Esa](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
