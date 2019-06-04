---
title: Csecurityattributes – třída
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: b26de7a2a3426ed2fe86bd7ef50f6c5410fa5364
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503199"
---
# <a name="csecurityattributes-class"></a>Csecurityattributes – třída

Tato třída představuje dynamického zajišťování obálku pro strukturu atributy zabezpečení.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSecurityAttributes::Set](#set)|Volejte tuto metodu za účelem nastavení atributů `CSecurityAttributes` objektu.|

## <a name="remarks"></a>Poznámky

`SECURITY_ATTRIBUTES` Struktura obsahuje [popisovače zabezpečení](/windows/desktop/api/winnt/ns-winnt-_security_descriptor) používají k vytvoření objektu a určuje, zda je popisovač načíst tak, že zadáte tuto strukturu odvoditelný.

Úvod do modelu řízení přístupu ve Windows najdete v tématu [řízení přístupu](/windows/desktop/SecAuthZ/access-control) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity.h

##  <a name="csecurityattributes"></a>  CSecurityAttributes::CSecurityAttributes

Konstruktor

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>Parametry

*rSecurityDescriptor*<br/>
Odkaz na popisovač zabezpečení.

*bInheritsHandle*<br/>
Určuje, zda Vrácený popisovač se dědí, když se vytvoří nový proces. Pokud je tento člen má hodnotu true, nový proces zdědí popisovač.

##  <a name="set"></a>  CSecurityAttributes::Set

Volejte tuto metodu za účelem nastavení atributů `CSecurityAttributes` objektu.

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Parametry

*rSecurityDescriptor*<br/>
Odkaz na popisovač zabezpečení.

*bInheritHandle*<br/>
Určuje, zda Vrácený popisovač se dědí, když se vytvoří nový proces. Pokud je tento člen má hodnotu true, nový proces zdědí popisovač.

### <a name="remarks"></a>Poznámky

Tato metoda používá konstruktor k inicializaci `CSecurityAttributes` objektu.

## <a name="see-also"></a>Viz také:

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[Popisovač zabezpečení](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
