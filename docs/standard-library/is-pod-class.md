---
title: is_pod – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_pod
dev_langs:
- C++
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b52479cc433f59d76dd40cfb752550e51652892d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856769"
---
# <a name="ispod-class"></a>is_pod – třída

Testy, pokud je typ POD.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>Parametry

*T* typ, který má dotaz.

## <a name="remarks"></a>Poznámky

`is_pod<T>::value` je `true` Pokud typ *T* je prostý staré dat (POD). V opačném případě je `false`.

Aritmetické typy, výčtové typy, typy ukazatelů a ukazatel na typy členů jsou POD.

Odchylka nákladů kvalifikovaný verzi POD typu samotné je typ POD.

Pole POD se POD.

Struktura nebo union, jsou všechny obsahující data nestatické POD, je sám POD Pokud má:

- Žádné uživatele deklarovaný konstruktory.

- Žádné datové nestatické soukromé nebo chráněné členy.

- Žádné základní třídy.

- Žádné virtuální funkce.

- Žádné datové nestatické členy odkazového typu.

- Operátor přiřazení žádné uživatelem definované kopírování.

- Žádné – destruktor definovaný uživatelem.

Proto můžete rekurzivně sestavení POD struktury a pole, které obsahují POD struktury a pole.

## <a name="example"></a>Příklad

```cpp
// std__type_traits__is_pod.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial {
    int val;
};

struct throws {
    throws() {}  // User-declared ctor, so not POD

    int val;
};

int main() {
    std::cout << "is_pod<trivial> == " << std::boolalpha
        << std::is_pod<trivial>::value << std::endl;
    std::cout << "is_pod<int> == " << std::boolalpha
        << std::is_pod<int>::value << std::endl;
    std::cout << "is_pod<throws> == " << std::boolalpha
        << std::is_pod<throws>::value << std::endl;

    return (0);
}
```

```Output
is_pod<trivial> == true
is_pod<int> == true
is_pod<throws> == false
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<type_traits >

**Namespace:** – std

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)<br/>
