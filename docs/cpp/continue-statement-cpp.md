---
title: continue – příkaz (C++)
ms.date: 11/04/2016
f1_keywords:
- continue_cpp
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
ms.openlocfilehash: 6fbc4af6a9a56f3406582ea9ba59f4d5759b88a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607477"
---
# <a name="continue-statement-c"></a>continue – příkaz (C++)

Vynutí přenos řízení na kontrolní výraz nejmenší nadřazené [proveďte](../cpp/do-while-statement-cpp.md), [pro](../cpp/for-statement-cpp.md), nebo [při](../cpp/while-statement-cpp.md) smyčky.

## <a name="syntax"></a>Syntaxe

```
continue;
```

## <a name="remarks"></a>Poznámky

Nebudou provedeny všechny zbývající příkazy v aktuální iteraci. Na další iteraci smyčky je stanoven následujícím způsobem:

- V **proveďte** nebo **při** smyčky, začíná další iterace přehodnocením řídicí výraz **proveďte** nebo **při** příkazu.

- V **pro** smyčky (pomocí syntaxe `for`(`init-expr`; `cond-expr`; `loop-expr`)), `loop-expr` provedeny klauzule. Pak bude `cond-expr` klauzule je již znovu a v závislosti na výsledku, buď smyčku ukončí nebo dojde k jiné iterace.

Následující příklad ukazuje způsob, jakým **pokračovat** příkaz je možné obejít části kódu a zahájí na další iteraci smyčky.

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

## <a name="see-also"></a>Viz také:

[Jump – příkazy](../cpp/jump-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)