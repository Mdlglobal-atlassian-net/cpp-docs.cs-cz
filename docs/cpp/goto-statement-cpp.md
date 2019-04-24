---
title: goto – příkaz (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: aac308905a01a52a4ce5ee0fa3be03f2f33ac1cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153694"
---
# <a name="goto-statement-c"></a>goto – příkaz (C++)

**Goto** příkaz bezpodmínečně přenese ovládací prvek na příkaz s popiskem podle zadaného identifikátoru.

## <a name="syntax"></a>Syntaxe

```
goto identifier;
```

## <a name="remarks"></a>Poznámky

Příkaz s popiskem určeným `identifier` musí být v aktuální funkci. Všechny `identifier` názvy jsou členy vnitřní obor názvů a proto nejsou v konfliktu s další identifikátory.

Má smysl jenom na popisek příkazu **goto** příkazu; v opačném případě se ignorují popisků příkazů. Popisky nelze deklarovat znovu.

A **goto** nejsou povoleny pro řízení je převedeno na umístění, ke kterému přeskočí inicializace jakákoli proměnná, která je v oboru v dané oblasti. V následujícím příkladu vyvolává C2362:

```cpp
int goto_fn(bool b)
{
    if (!b)
    {
        goto exit;  // C2362
    }
    else
    { /*...*/ }

    int error_code = 42;

exit:
    return error_code;
}
```

Styl programování je dobrým **přerušení**, **pokračovat**, a **vrátit** příkazy místo **goto** příkaz pokaždé, když je to možné. Ale protože **přerušení** příkaz ukončí pouze jednu úroveň smyčky, možná budete muset použít **goto** příkaz Ukončit hluboce vnořený smyčku.

Další informace o popisky a **goto** příkaz, naleznete v tématu [příkazy s popiskem](../cpp/labeled-statements.md).

## <a name="example"></a>Příklad

V tomto příkladu **goto** příkaz přenese ovládací prvek na bod s názvem `stop` při `i` rovná 3.

```cpp
// goto_statement.cpp
#include <stdio.h>
int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 2; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 3 )
                goto stop;
        }
    }

    // This message does not print:
    printf_s( "Loop exited. i = %d\n", i );

    stop:
    printf_s( "Jumped to stop. i = %d\n", i );
}
```

```Output
Outer loop executing. i = 0
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 1
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 2
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 3
Inner loop executing. j = 0
Jumped to stop. i = 3
```

## <a name="see-also"></a>Viz také:

[Jump – příkazy](../cpp/jump-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
