---
title: while – příkaz (C)
ms.date: 11/04/2016
f1_keywords:
- while
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
ms.openlocfilehash: 4a789f248702f33342a19f95710a8ae313da1d94
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151894"
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

## <a name="see-also"></a>Viz také:

[while – příkaz (C++)](../cpp/while-statement-cpp.md)
