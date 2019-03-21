---
title: Kompilátor upozornění (úroveň 4) C4701
ms.date: 11/04/2016
f1_keywords:
- C4701
helpviewer_keywords:
- C4701
ms.assetid: d7c76c66-1f3f-4d3c-abe4-5d94c84a5a1f
ms.openlocfilehash: 7d9b0041428af62c4b9d7a9a170547ab75222e94
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278421"
---
# <a name="compiler-warning-level-4-c4701"></a>Kompilátor upozornění (úroveň 4) C4701

potenciální neinicializovaná lokální proměnná "name" použít

Lokální proměnná *název* možná použili bez se přiřadí hodnota. To může vést k nepředvídatelným výsledkům.

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

[Upozornění kompilátoru (úroveň 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)<br/>
[Upozornění, / SDL a vylepšení detekce neinicializované proměnné](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)