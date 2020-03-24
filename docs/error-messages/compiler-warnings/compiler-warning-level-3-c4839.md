---
title: Upozornění kompilátoru (úroveň 3) C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: 2c238dc16359583bf55f7590d2ce7c0363d66df7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198572"
---
# <a name="compiler-warning-level-3-c4839"></a>Upozornění kompilátoru (úroveň 3) C4839

> nestandardní použití třídy*Type*jako argumentu funkce variadické

Třídy nebo struktury, které jsou předány funkci variadické, například `printf`, musí být triviálním kopírováním. Při předání takových objektů kompilátor jednoduše vytvoří bitovou kopii a nevolá konstruktor nebo destruktor.

Toto upozornění je k dispozici od začátku v aplikaci Visual Studio 2017.

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

Chcete-li chybu opravit, můžete zavolat členskou funkci, která vrací triviální kopírovací typ,

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

Pro řetězce sestavené a spravované pomocí `operator LPCWSTR()` `CStringW`by měly být použity k přetypování `CStringW` objektu na ukazatel jazyka C očekávaný řetězcem formátu.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
