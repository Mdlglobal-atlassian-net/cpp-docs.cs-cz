---
title: continue – příkaz (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: b3790ecfde0af958b3244cfdaa61524ba78d6267
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180274"
---
# <a name="continue-statement-c"></a>continue – příkaz (C++)

Vynutí přenos řízení na řídicí výraz nejmenšího ohraničujícího do [smyčky](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)nebo [while](../cpp/while-statement-cpp.md) .

## <a name="syntax"></a>Syntaxe

```
continue;
```

## <a name="remarks"></a>Poznámky

Zbývající příkazy v aktuální iteraci nejsou provedeny. Další iterace smyčky je určena následujícím způsobem:

- Ve smyčce **do** nebo **while** začíná další iterace přehodnocením řídicího výrazu příkazu **do** nebo **while** .

- Ve smyčce **for** (pomocí `for`syntaxe (`init-expr`; `cond-expr`; `loop-expr`)) se spustí klauzule `loop-expr`. Poté je znovu vyhodnocena klauzule `cond-expr` a v závislosti na výsledku dojde k ukončení smyčky nebo k jiné iteraci.

Následující příklad ukazuje, jak lze pomocí příkazu **Continue** obejít oddíly kódu a zahájit další iteraci smyčky.

## <a name="example"></a>Příklad

```cpp
// continue_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        i++;
        printf_s("before the continue\n");
        continue;
        printf("after the continue, should never print\n");
     } while (i < 3);

     printf_s("after the do loop\n");
}
```

```Output
before the continue
before the continue
before the continue
after the do loop
```

## <a name="see-also"></a>Viz také

[Jump – příkazy](../cpp/jump-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
