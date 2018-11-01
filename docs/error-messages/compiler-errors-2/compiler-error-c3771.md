---
title: Chyba kompilátoru C3771
ms.date: 11/04/2016
f1_keywords:
- C3771
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
ms.openlocfilehash: 8ff2993cbd5f289ca9208d8c532d7fa8329af086
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453378"
---
# <a name="compiler-error-c3771"></a>Chyba kompilátoru C3771

"identifikátor": deklarace typu friend se nenašel v nejbližším oboru oborů

Deklarace šablony třídy pro zadanou šablonu *identifikátor* nebyl nalezen v aktuálním oboru názvů.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Ujistěte se, že deklarace šablony třídy pro identifikátor šablony je definována v aktuálním oboru názvů nebo že identifikátor šablony je plně kvalifikovaný název.

## <a name="example"></a>Příklad

Následující příklad kódu deklaruje šablony třídy a funkce v oboru názvů `NA`, pokusí se deklarace typu friend šablony funkce v oboru názvů, ale `NB`.

```cpp
// C3771.cpp
// compile with: /c

namespace NA {
template<class T> class A {
    void aFunction(T t) {};
    };
}
// using namespace NA;
namespace NB {
    class X {
        template<class T> friend void A<T>::aFunction(T); // C3771
// try the following line instead
//      template<class T> friend void NA::A<T>::aFunction(T);
// or try "using namespace NA;" instead.
    };
}
```

## <a name="see-also"></a>Viz také

[Šablony](../../cpp/templates-cpp.md)