---
title: Příkaz goto a příkazy s popiskem (C)
ms.date: 11/04/2016
f1_keywords:
- goto
helpviewer_keywords:
- labeled statement
- statements, labeled
- goto keyword [C]
ms.assetid: 3d0473dc-4b18-4fcc-9616-31a38499d7d7
ms.openlocfilehash: b23e7e6310ba4ed968e2eac8e6d07d81ee4e79ba
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151946"
---
# <a name="goto-and-labeled-statements-c"></a>Příkaz goto a příkazy s popiskem (C)

`goto` Příkaz předává řízení k popisku. Dané popisek se musí nacházet ve stejné funkce a může objevit před pouze jeden příkaz ve stejné funkci.

## <a name="syntax"></a>Syntaxe

*příkaz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz s popiskem*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz-skoku*

*příkaz-skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**příkaz goto** *identifikátor* **;**

*příkaz s popiskem*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor* **:** *– příkaz*

Příkaz Popisek má smysl pouze `goto` příkaz v libovolném kontextu, provádí se příkaz s popiskem bez ohledu na popisek.

A *příkaz-skoku* se musí nacházet ve stejné funkce a může objevit před pouze jeden příkaz ve stejné funkci. Sada *identifikátor* následující názvy `goto` má svůj vlastní obor názvů, takže názvy nejsou v konfliktu s další identifikátory. Popisky nelze deklarovat znovu. Zobrazit [obory názvů](../c-language/name-spaces.md) Další informace.

Styl programování je dobrým **přerušení**, **pokračovat**, a `return` příkaz preference a `goto` kdykoli je to možné. Protože **přerušení** příkaz ukončí pouze z jedné úrovně smyčky, `goto` může být nutné pro ukončení smyčky z v rámci smyčky hluboce vnořený.

Tento příklad ukazuje, `goto` – příkaz:

```
// goto.c
#include <stdio.h>

int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 3; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 5 )
                goto stop;
        }
    }

    /* This message does not print: */
    printf_s( "Loop exited. i = %d\n", i );

    stop: printf_s( "Jumped to stop. i = %d\n", i );
}
```

V tomto příkladu `goto` příkaz přenese ovládací prvek na bod s názvem `stop` při `i` rovná 5.

## <a name="see-also"></a>Viz také:

[Příkazy](../c-language/statements-c.md)
