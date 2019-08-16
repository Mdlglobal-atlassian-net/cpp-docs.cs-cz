---
title: CSacl – třída
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
ms.openlocfilehash: c4bbdfccb2d6d8b167c537b7ae4df57c89438479
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496517"
---
# <a name="csacl-class"></a>CSacl – třída

Tato třída je obálkou struktury SACL (seznam řízení přístupu k systému).

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSacl : public CAcl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSacl::CSacl](#csacl)|Konstruktor|
|[CSacl::~CSacl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSacl::AddAuditAce](#addauditace)|Přidá do `CSacl` objektu položku řízení přístupu auditu (ACE).|
|[CSacl::GetAceCount](#getacecount)|Vrátí počet položek řízení přístupu (ACE) v `CSacl` objektu.|
|[CSacl::RemoveAce](#removeace)|Odebere z `CSacl` objektu konkrétní položku ACE (řízení přístupu).|
|[CSacl::RemoveAllAces](#removeallaces)|Odebere všechny položky řízení přístupu obsažené v `CSacl` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CSacl:: operator =](#operator_eq)|Operátor přiřazení|

## <a name="remarks"></a>Poznámky

Seznam SACL obsahuje položky řízení přístupu (ACE), které určují typy pokusů o přístup, které generují záznamy auditu v protokolu událostí zabezpečení řadiče domény. Všimněte si, že seznam SACL generuje položky protokolu pouze na řadiči domény, kde došlo k pokusu o přístup, nikoli na každém řadiči domény, který obsahuje repliku objektu.

Chcete-li nastavit nebo načíst seznam SACL v popisovači zabezpečení objektu, musí být povoleno oprávnění SE_SECURITY_NAME v přístupovém tokenu žádajícího vlákna. Skupina Administrators má toto oprávnění udělené ve výchozím nastavení a je možné ji udělit ostatním uživatelům nebo skupinám. Je-li uděleno oprávnění, není vyžadováno: před provedením operace definované oprávněním musí být oprávnění povoleno v tokenu přístupu zabezpečení, aby se mohlo projevit. Tento model umožňuje povolit oprávnění jenom pro konkrétní systémové operace a pak je zakázaný, když už nepotřebujete. Příklady povolení SE_SECURITY_NAME naleznete v tématu [AtlGetSacl](security-global-functions.md#atlgetsacl) a [AtlSetSacl](security-global-functions.md#atlsetsacl) .

Použijte metody třídy poskytované k přidávání, odebírání, vytváření a odstraňování položek řízení přístupu (ACE `SACL` ) z objektu. Viz také [AtlGetSacl](security-global-functions.md#atlgetsacl) a [AtlSetSacl](security-global-functions.md#atlsetsacl).

Úvod do modelu řízení přístupu v systému Windows naleznete v tématu [Access Control](/windows/win32/SecAuthZ/access-control) v Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CAcl](../../atl/reference/cacl-class.md)

`CSacl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="addauditace"></a>CSacl::AddAuditAce

Přidá do `CSacl` objektu položku řízení přístupu auditu (ACE).

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
Objekt [CSID](../../atl/reference/csid-class.md)

*AccessMask*<br/>
Určuje masku přístupových práv, která se mají auditovat pro zadaný `CSid` objekt.

*bSuccess*<br/>
Určuje, jestli se mají auditovat povolené pokusy o přístup. Nastavením tohoto příznaku na hodnotu true povolíte auditování. v opačném případě ho nastavte na false.

*bFailure*<br/>
Určuje, jestli se mají auditovat zamítnuté pokusy o přístup. Nastavením tohoto příznaku na hodnotu true povolíte auditování. v opačném případě ho nastavte na false.

*AceFlags*<br/>
Sada bitových příznaků, které řídí dědění ACE.

*pObjectType*<br/>
Typ objektu.

*pInheritedObjectType*<br/>
Typ zděděného objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je položka ACE přidána `CSacl` do objektu, hodnota false při selhání.

### <a name="remarks"></a>Poznámky

`CSacl` Objekt obsahuje položky řízení přístupu (ACE), které určují typy pokusů o přístup, které generují záznamy auditu v protokolu událostí zabezpečení. Tato metoda přidá takovou položku ACE do `CSacl` objektu.

Popis různých příznaků, které lze nastavit v parametru *AceFlags* , naleznete v tématu [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) .

##  <a name="csacl"></a>CSacl::CSacl

Konstruktor

```
CSacl() throw();
CSacl(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
Existující `ACL` struktura (seznam řízení přístupu).

### <a name="remarks"></a>Poznámky

Objekt může být volitelně vytvořen pomocí existující `ACL` struktury. `CSacl` Zajistěte, aby byl tento parametr seznam řízení přístupu (SACL) systému a nikoli volitelný seznam řízení přístupu (DACL). Pokud je v sestavení ladění k dispozici DACL, dojde k zadání kontrolního výrazu. V nástroji vydaná verze sestavování jsou všechny záznamy ze seznamu DACL ignorovány.

##  <a name="dtor"></a>  CSacl::~CSacl

Destruktor.

```
~CSacl() throw();
```

### <a name="remarks"></a>Poznámky

Destruktor uvolní všechny prostředky, které objekt získal, včetně všech položek řízení přístupu (ACE).

##  <a name="getacecount"></a>CSacl::GetAceCount

Vrátí počet položek řízení přístupu (ACE) v `CSacl` objektu.

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet položek řízení přístupu obsažených v `CSacl` objektu.

##  <a name="operator_eq"></a>CSacl:: operator =

Operátor přiřazení

```
CSacl& operator=(const ACL& rhs) throw(...);
```

### <a name="parameters"></a>Parametry

*zarovnání indirekce RHS*<br/>
Seznam řízení přístupu (Access-Control), který se má přiřadit k existujícímu objektu. `ACL`

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktualizovaný `CSacl` objekt. Zajistěte `ACL` , aby byl parametr ve skutečnosti seznam řízení přístupu (SACL) systému, a ne seznam DACL (Discretionary Access Control List). V okně ladění sestavení dojde k kontrolnímu výrazu a v sestavení vydaných `ACL` verzí parametr bude ignorován.

##  <a name="removeace"></a>CSacl::RemoveAce

Odebere z `CSacl` objektu konkrétní položku ACE (řízení přístupu).

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky ACE, která se má odebrat

### <a name="remarks"></a>Poznámky

Tato metoda je odvozena z [CAtlArray:: funkce RemoveAt](../../atl/reference/catlarray-class.md#removeat).

##  <a name="removeallaces"></a>CSacl::RemoveAllAces

Odebere všechny položky řízení přístupu (ACE) obsažené v `CSacl` objektu.

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Poznámky

Odebere všechny `ACE` struktury (pokud existují) `CSacl` v objektu.

## <a name="see-also"></a>Viz také:

[CAcl – třída](../../atl/reference/cacl-class.md)<br/>
[Seznamy ACL](/windows/win32/SecAuthZ/access-control-lists)<br/>
[ACE](/windows/win32/SecAuthZ/access-control-entries)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
