---
title: Chyba kompilátoru C3771
ms.date: 11/04/2016
f1_keywords:
- C3771
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
ms.openlocfilehash: 6c29ad6007d33c43ae1e4758ae05caa9109053e3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165727"
---
# <a name="compiler-error-c3771"></a>Chyba kompilátoru C3771

identifikátor: deklarace typu Friend se v nejbližším oboru oboru názvů nedá najít.

V aktuálním oboru názvů nelze nalézt deklaraci šablony třídy pro zadaný *identifikátor* šablony.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Ujistěte se, že deklarace šablony třídy pro identifikátor šablony je definována v aktuálním oboru názvů nebo že identifikátor šablony je plně kvalifikovaný název.

## <a name="example"></a>Příklad

Následující příklad kódu deklaruje šablonu třídy a funkci v oboru názvů `NA`, ale pokusí se deklarovat šablonu funkce Friend v oboru názvů `NB`.

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
