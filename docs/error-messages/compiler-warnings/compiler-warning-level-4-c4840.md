---
title: Upozornění kompilátoru (úroveň 4) C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: 649083d66d0c7a0ef11c742e56cbfb70e2e9b75f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185201"
---
# <a name="compiler-warning-level-4-c4840"></a>Upozornění kompilátoru (úroveň 4) C4840

> nepřenosné použití třídy*Type*jako argumentu funkce variadické

## <a name="remarks"></a>Poznámky

Třídy nebo struktury, které jsou předány funkci variadické, musí být triviální kopírovatelné. Při předání takových objektů kompilátor jednoduše vytvoří bitovou kopii a nevolá konstruktor nebo destruktor.

Toto upozornění je k dispozici od začátku v aplikaci Visual Studio 2017.

## <a name="example"></a>Příklad

Následující ukázka generuje C4840 a ukazuje, jak ji opravit:

```cpp
// C4840.cpp
// compile by using: cl /EHsc /W4 C4840.cpp
#include <stdio.h>

int main()
{
    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);

    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                       // as an argument to a variadic function
    // To correct the error, you can perform a static cast
    // to convert the object before passing it:
    printf("%i\n", static_cast<int>(s));
}
```

Pro řetězce sestavené a spravované pomocí `operator LPCWSTR()` `CStringW`by se měly použít k přetypování `CStringW` objektu na ukazatel řetězce ve stylu C, který je očekáván formátovacím řetězcem:

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
