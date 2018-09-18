---
title: C4840 kompilátoru (úroveň 4) upozornění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/13/2018
ms.topic: error-reference
f1_keywords:
- C4840
dev_langs:
- C++
helpviewer_keywords:
- C4840
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c43ce60d319c427877b77a043df7c30bd00edc9b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025877"
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