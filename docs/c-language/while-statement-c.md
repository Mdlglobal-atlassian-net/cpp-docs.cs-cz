---
title: while – příkaz (C)
ms.date: 11/04/2016
f1_keywords:
- while
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
ms.openlocfilehash: d774971910fe69ed707bc545e4c0e022282a1d17
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662342"
---
# <a name="while-statement-c"></a>while – příkaz (C)

`while` Příkaz umožňuje opakujte příkaz, dokud nebude NEPRAVDA zadaným výrazem.

## <a name="syntax"></a>Syntaxe

*příkaz iterace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**zatímco (**  *výraz*  **)**  *– příkaz*

*Výraz* musí mít aritmetický typ nebo typ ukazatele. Spuštění probíhá následujícím způsobem:

1. *Výraz* vyhodnocena.

1. Pokud *výraz* je počáteční hodnota false, text `while` příkazu není nikdy proveden a ovládání přejde z `while` příkaz dalšímu příkazu v programu.

   Pokud *výraz* je true (nenulový), provede se tělo příkazu a proces se opakuje, počínaje krokem 1.

`while` Příkaz může také skončit při **přerušení**, `goto`, nebo `return` v rámci příkaz provede se tělo. Použití **pokračovat** příkaz k ukončení iterace bez ukončení `while` smyčky. **Pokračovat** příkaz předá řízení následující iteraci `while` příkazu.

Zde je příklad příkazu `while`:

```C
while ( i >= 0 )
{
    string1[i] = string2[i];
    i--;
}
```

Tento příklad zkopíruje znaky z `string2` k `string1`. Pokud `i` je větší než nebo rovno 0, `string2[i]` přiřazen `string1[i]` a `i` se odečte. Když `i` dosáhne nebo klesne pod 0, provádění `while` příkaz ukončí.

## <a name="see-also"></a>Viz také

[while – příkaz (C++)](../cpp/while-statement-cpp.md)
