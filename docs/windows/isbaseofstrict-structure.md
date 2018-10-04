---
title: Isbaseofstrict – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/03/2018
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
ms.openlocfilehash: 9fc41bdccf9cce3d455d4effd3541731929e5de2
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789264"
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
