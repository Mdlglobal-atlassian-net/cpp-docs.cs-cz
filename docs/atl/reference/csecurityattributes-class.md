---
title: Třída CSecurityAttributes
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: e0ac813008a028bb233adfb4c7409a0ad62a6b78
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746500"
---
# <a name="csecurityattributes-class"></a>Třída CSecurityAttributes

Tato třída je tenký obálka pro strukturu atributů zabezpečení.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSecurityAttributes::Nastavit](#set)|Volání této metody nastavit atributy `CSecurityAttributes` objektu.|

## <a name="remarks"></a>Poznámky

Struktura `SECURITY_ATTRIBUTES` obsahuje [popisovač zabezpečení](/windows/win32/api/winnt/ns-winnt-security_descriptor) použitý pro vytvoření objektu a určuje, zda je popisovač načtený zadáním této struktury dědičný.

Úvod k modelu řízení přístupu v systému Windows najdete v tématu [Řízení přístupu](/windows/win32/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

## <a name="csecurityattributescsecurityattributes"></a><a name="csecurityattributes"></a>CSecurityAttributes::CSecurityAttributes

Konstruktor

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>Parametry

*rSecurityDescriptor*<br/>
Odkaz na popisovač zabezpečení.

*bInheritsHandle*<br/>
Určuje, zda je vrácený popisovač zděděn při vytvoření nového procesu. Pokud je tento člen true, nový proces dědí popisovač.

## <a name="csecurityattributesset"></a><a name="set"></a>CSecurityAttributes::Nastavit

Volání této metody nastavit atributy `CSecurityAttributes` objektu.

```cpp
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Parametry

*rSecurityDescriptor*<br/>
Odkaz na popisovač zabezpečení.

*bInheritHandle*<br/>
Určuje, zda je vrácený popisovač zděděn při vytvoření nového procesu. Pokud je tento člen true, nový proces dědí popisovač.

### <a name="remarks"></a>Poznámky

Tato metoda se používá konstruktoru k `CSecurityAttributes` inicializaci objektu.

## <a name="see-also"></a>Viz také

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[popisovač zabezpečení](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
