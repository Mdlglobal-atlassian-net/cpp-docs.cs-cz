---
title: Continue – příkaz (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- continue_cpp
dev_langs:
- C++
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88281d90ce15ced12079b3c66a74bb2f23c11034
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099703"
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