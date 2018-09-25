---
title: Isbaseofstrict – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 137f572f01d4aa72b9141c3ca172426fdb575b48
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169521"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename Base,
   typename Derived
>

struct IsBaseOfStrict;
template <
   typename Base
>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Parametry

*základ*<br/>
Základní typ.

*Odvozené*<br/>
Odvozeného typu.

## <a name="remarks"></a>Poznámky

Ověřuje, zda je jeden typ základ jiného.

První šablona testuje, jestli typ je odvozen od základního typu, který může přinést `true` nebo `false`. Druhá šablona testuje, jestli je typ odvozený od sebe sama, který vždy dává `false`.

## <a name="members"></a>Členové

### <a name="public-constants"></a>Veřejné konstanty

Název                            | Popis
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::value](#value) | Označuje, zda je jeden typ základ jiného.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IsBaseOfStrict`

## <a name="requirements"></a>Požadavky

**Záhlaví:** internal.h

**Namespace:** Microsoft::WRL:: details –

## <a name="value"></a>IsBaseOfStrict::value

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Poznámky

Označuje, zda je jeden typ základ jiného.

`value` je `true` Pokud typ `Base` je základní třídu typu `Derived`, v opačném případě je `false`.
