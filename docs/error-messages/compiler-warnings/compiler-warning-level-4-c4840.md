---
title: Kompilátor C4840 upozornění (úroveň 4)
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: a757004659c1a9d2ce858cfae5ddfbc6c024d782
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586430"
---
# <a name="compiler-warning-level-4-c4840"></a>Kompilátor C4840 upozornění (úroveň 4)

> nepřenositelné použití třídy*typ*"jako argumentu variadické funkce

## <a name="remarks"></a>Poznámky

Třídy nebo struktury, které jsou předány variadické funkce musí být snadno kopírovatelná. Při předávání těchto objektů, kompilátor jednoduše vytvoří bitové kopie a nevolá konstruktor nebo destruktor.

Toto upozornění je k dispozici od verze Visual Studio 2017.

## <a name="example"></a>Příklad

Následující ukázka generuje C4840 a ukazuje, jak ho opravit:

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

Pro řetězce vytvořené a spravují s použitím `CStringW`, poskytnutého `operator LPCWSTR()` by měla sloužit k přetypování `CStringW` ukazatel na řetězec ve stylu jazyka C ve formátovacím řetězci byl očekáván objekt:

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```