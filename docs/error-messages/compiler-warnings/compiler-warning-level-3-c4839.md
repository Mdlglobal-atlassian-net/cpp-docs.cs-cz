---
title: Kompilátor upozornění (úroveň 3) C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: 09b6e5b8dc984b35df7de96f5cf8610f2b0f16af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536628"
---
# <a name="compiler-warning-level-3-c4839"></a>Kompilátor upozornění (úroveň 3) C4839

> nestandardní použití třídy*typ*"jako argumentu variadické funkce

Třídy nebo struktury, které jsou předány variadické funkce, jako například `printf` musí být snadno kopírovatelná. Při předávání těchto objektů, kompilátor jednoduše vytvoří bitové kopie a nevolá konstruktor nebo destruktor.

Toto upozornění je k dispozici od verze Visual Studio 2017.

## <a name="example"></a>Příklad

Následující ukázka generuje C4839:

```cpp
// C4839.cpp
// compile by using: cl /EHsc /W3 C4839.cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function
}
```

Chcete-li opravit chybu, můžete volat členské funkce, která vrací triviálně kopírovatelné typu

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

Pro řetězce vytvořené a spravují s použitím `CStringW`, poskytnutého `operator LPCWSTR()` by měla sloužit k přetypování `CStringW` objektu na ukazatel C očekává formátovacím řetězcem.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```