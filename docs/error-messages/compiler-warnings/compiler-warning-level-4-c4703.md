---
title: Upozornění (úroveň 4) C4703 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4703
dev_langs:
- C++
helpviewer_keywords:
- C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 202e6605365076f6141dd3ce098327e18a0bfe87
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096573"
---
# <a name="compiler-warning-level-4-c4703"></a>Kompilátor upozornění (úroveň 4) C4703

Potenciálně neinicializovaná lokální proměnná ukazatele použit název

Lokální proměnná ukazatele *název* možná použili bez se přiřadí hodnota. To může vést k nepředvídatelným výsledkům.

## <a name="example"></a>Příklad

Následující kód vygeneruje C4701 a C4703.

```cpp
#include <malloc.h>

void func(int size)
{
    void* p;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr) // C4701 and C4703
        free(p);
}

void main()
{
    func(9);
}
```

```Output
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used

```

Chcete-li opravit toto upozornění, inicializujte proměnné, jak je znázorněno v tomto příkladu:

```cpp
#include <malloc.h>

void func(int size)
{
    void* p = nullptr;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr)
        free(p);
}

void main()
{
    func(9);
}
```

## <a name="see-also"></a>Viz také

[Upozornění kompilátoru (úroveň 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)<br/>
[Upozornění, / SDL a vylepšení detekce neinicializované proměnné](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)