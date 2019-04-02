---
title: IsBaseOfStrict – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
ms.openlocfilehash: 85aeb71ceaa162cc6366836dd286f2f9983d34e2
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786751"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Parametry

*základ*<br/>
Základní typ.

*Odvozené*<br/>
Odvozeného typu.

## <a name="remarks"></a>Poznámky

Ověřuje, zda je jeden typ základ jiného.

První šablona testuje, jestli typ je odvozen od základního typu, který může přinést **true** nebo **false**. Druhá šablona testuje, jestli je typ odvozený od sebe sama, který vždy dává **false**.

## <a name="members"></a>Členové

### <a name="public-constants"></a>Veřejné konstanty

Name                            | Popis
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::value](#value) | Označuje, zda je jeden typ základ jiného.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IsBaseOfStrict`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="value"></a>IsBaseOfStrict::value

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Poznámky

Označuje, zda je jeden typ základ jiného.

`value` je **true** Pokud typ `Base` je základní třídu typu `Derived`, v opačném případě je **false**.
