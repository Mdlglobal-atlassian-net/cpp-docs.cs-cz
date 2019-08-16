---
title: CSecurityAttributes – třída
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: ebffbea120101a77450a5e8da3cdb6e34723e7be
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496504"
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes – třída

Tato třída je tenkou obálkou pro strukturu atributů zabezpečení.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

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
|[CSecurityAttributes:: set](#set)|Zavolejte tuto metodu pro nastavení atributů `CSecurityAttributes` objektu.|

## <a name="remarks"></a>Poznámky

Struktura obsahuje popisovač zabezpečení, který se používá pro vytvoření objektu a určuje, zda popisovač načtený zadáním této struktury je dědičný. [](/windows/win32/api/winnt/ns-winnt-security_descriptor) `SECURITY_ATTRIBUTES`

Úvod do modelu řízení přístupu v systému Windows naleznete v tématu [Access Control](/windows/win32/SecAuthZ/access-control) v Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsecurity. h

##  <a name="csecurityattributes"></a>CSecurityAttributes::CSecurityAttributes

Konstruktor

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>Parametry

*rSecurityDescriptor*<br/>
Odkaz na popisovač zabezpečení

*bInheritsHandle*<br/>
Určuje, zda je vrácený popisovač děděn při vytvoření nového procesu. Pokud je tento člen pravdivý, nový proces zdědí popisovač.

##  <a name="set"></a>CSecurityAttributes:: set

Zavolejte tuto metodu pro nastavení atributů `CSecurityAttributes` objektu.

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Parametry

*rSecurityDescriptor*<br/>
Odkaz na popisovač zabezpečení

*bInheritHandle*<br/>
Určuje, zda je vrácený popisovač děděn při vytvoření nového procesu. Pokud je tento člen pravdivý, nový proces zdědí popisovač.

### <a name="remarks"></a>Poznámky

Tato metoda je používána konstruktorem k inicializaci `CSecurityAttributes` objektu.

## <a name="see-also"></a>Viz také:

[Ukázka zabezpečení](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[popisovač zabezpečení](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Globální funkce zabezpečení](../../atl/reference/security-global-functions.md)
