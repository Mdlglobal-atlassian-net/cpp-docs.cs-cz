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
ms.openlocfilehash: b5e0d602332c87510b1fe5f59db3e497b88f0acb
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299114"
---
# <a name="goto-and-labeled-statements-c"></a>Příkaz goto a příkazy s popiskem (C)

`goto` Příkaz přenáší řízení na popisek. Daný popisek se musí nacházet ve stejné funkci a může se objevit před pouze jedním příkazem ve stejné funkci.

## <a name="syntax"></a>Syntaxe

*příkaz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz s popiskem*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příkaz skoku*

*příkaz skoku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**goto**  *identifikátor*  **;**

*příkaz s popiskem*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*  **: –**  *příkaz*

Popisek příkazu má smysl jenom s `goto` příkazem. v jakémkoli jiném kontextu je příkaz s popiskem proveden bez ohledu na popisek.

*Příkaz skoku* se musí nacházet ve stejné funkci a může se objevit před pouze jedním příkazem ve stejné funkci. Sada názvů *identifikátorů* následující po `goto` má svůj vlastní obor názvů, aby názvy nebránily jiným identifikátorům. Popisky nelze deklarovat znovu. Další informace najdete v tématu o [názvových prostorech](../c-language/name-spaces.md) .

Je dobrým programovacím stylem použití **přerušit**, **pokračovat**a `return` příkazu v předvolbách `goto` , kdykoli je to možné. Vzhledem k tomu, že příkaz **Break** se ukončuje jenom z jedné úrovně smyčky, `goto` může být potřeba, aby se ukončila smyčka z hluboce vnořené smyčky.

Tento příklad ukazuje `goto` příkaz:

```c
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

V tomto příkladu `goto` příkaz přenáší řízení na bod označený, `stop` Pokud `i` se rovná 5.

## <a name="see-also"></a>Viz také

[Příkazy](../c-language/statements-c.md)
