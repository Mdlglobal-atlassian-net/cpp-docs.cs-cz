---
title: zatímco Statement (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- while
dev_langs:
- C++
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6993f209f5e7c5ab6f56ae886f2d57ba90a19936
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860646"
---
# <a name="while-statement-c"></a>while – příkaz (C)

`while` Příkaz umožňuje opakujte příkaz, dokud nebude NEPRAVDA zadaným výrazem.

## <a name="syntax"></a>Syntaxe

*příkaz iterace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**zatímco (***výraz***)***– příkaz*

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
