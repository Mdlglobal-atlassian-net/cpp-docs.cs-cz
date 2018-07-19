---
title: is_pod – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: c655ea4adec0364f35d0b43c637eae9c270cdb0e
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962062"
---
# <a name="ispod-class"></a>is_pod – třída

Testuje, zda je typ POD.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>Parametry

*T* typ dotazu.

## <a name="remarks"></a>Poznámky

`is_pod<T>::value` je **true** Pokud typ *T* je prostý starých dat (POD). V opačném případě je **false**.

Aritmetické typy, výčtové typy, typy ukazatele a typy ukazatelů na členy jsou POD.

Verze cv kvalifikovaný typ POD samotného je typ POD.

Pole POD patří POD.

Struktura nebo sjednocení, jehož nestatických datových členů jsou POD, je samotný POD Pokud má:

- Žádné uživatelem deklarované konstruktory.

- Žádné soukromé nebo chráněné nestatické datové členy.

- Žádné základní třídy.

- Žádné virtuální funkce.

- Žádné nestatické datové členy typu odkazu.

- Žádné uživatelem definovaného kopírovacího operátoru přiřazení.

- Žádné uživatelem definovaný destruktor.

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

**Namespace:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
