---
title: is_pod – třída
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_pod
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
ms.openlocfilehash: 1249e9a3689d4b91334e545ba294c28984898035
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455763"
---
# <a name="ispod-class"></a>is_pod – třída

Testuje, zda je typ POD.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

## <a name="remarks"></a>Poznámky

`is_pod<T>::value`má **hodnotu true** , pokud je typ *T* prostá stará data (pod). V opačném případě je **hodnota false**.

Aritmetické typy, výčtové typy, typy ukazatelů a ukazatele na typy členů jsou POD.

Verze typu POD, která je kvalifikována na základě CV, je typu POD.

Pole POD je samo POD.

Struktura nebo sjednocení, jejichž nestatické datové členy jsou POD, jsou mimo jiné, pokud má:

- Žádné uživatelem deklarované konstruktory.

- Žádné soukromé nebo chráněné nestatické datové členy.

- Žádné základní třídy.

- Žádné virtuální funkce.

- Žádné nestatické datové členy typu odkazu.

- Bez uživatelsky definovaného operátoru přiřazení kopírování.

- Neexistuje žádný uživatelsky definovaný destruktor.

Proto můžete rekurzivně sestavovat struktury POD a pole, která obsahují struktury POD a pole.

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

**Hlavička:** \<type_traits >

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
