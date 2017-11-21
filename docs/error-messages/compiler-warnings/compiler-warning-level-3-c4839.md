---
title: "Kompilátoru (úroveň 3) upozornění C4839 | Microsoft Docs"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords: C4839
dev_langs: C++
helpviewer_keywords: C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2f7bee6a9d391ab026b8df6cb1cb509de818d700
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warning-level-4-c4839"></a>C4839 kompilátoru upozornění (úroveň 4)

> nestandardní použití třídy se*typu*' jako argument funkce variadická

Ve Visual Studio 2017, třídy a struktury, která se budou předávat variadická fungovat, jako `printf` musí být trivially kopírovatelná. Při předávání tyto objekty, kompilátor jednoduše vytvoří bitové kopie a nevyvolá konstruktoru nebo destruktor.

## <a name="example"></a>Příklad

Následující ukázka generuje C4839:

```cpp
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

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

Chcete-li chybu opravit, můžete zavolat členské funkce, která vrátí hodnotu typu trivially kopírovatelná

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

jinak provést statické přetypování převést objekt před jeho odesláním:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Pro řetězce vytvořené a spravují pomocí `CStringW`, poskytnutého `operator LPCWSTR()` se má použít k přetypování `CStringW` objekt, který má ukazatel C očekávaný řetězec formátu.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```