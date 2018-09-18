---
title: Chyba kompilátoru C3771 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3771
dev_langs:
- C++
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2af9f58c533927b326ac39ff2f0c555d156dcaf3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079424"
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