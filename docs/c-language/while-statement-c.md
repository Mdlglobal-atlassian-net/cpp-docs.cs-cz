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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344730"
---
# <a name="while-statement-c"></a>while – příkaz (C)

`while` Příkaz umožňuje opakovat příkaz, dokud se zadaný výraz nevrátí na hodnotu NEPRAVDA.

## <a name="syntax"></a>Syntaxe

*příkaz iterace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while**–*příkaz* (*Expression***)**      

*Výraz* musí být aritmetického typu nebo typu ukazatele. Provádění pokračuje následujícím způsobem:

1. *Výraz* je vyhodnocen.

1. Pokud je *výraz* zpočátku nepravdivý, tělo `while` příkazu se nikdy nespustí a ovládací prvek se předává z `while` příkazu do dalšího příkazu v programu.

   Pokud je *výraz* true (nenulový), je proveden text příkazu a proces se opakuje od kroku 1.

Příkaz může také končit při spuštění **přerušení**, `goto`nebo `return` v rámci těla příkazu. `while` Použijte příkaz **Continue** k ukončení iterace bez ukončení `while` smyčky. Příkaz **Continue** předá řízení následující iteraci `while` příkazu.

Zde je příklad příkazu `while`:

```C
while ( i >= 0 )
{
    string1[i] = string2[i];
    i--;
}
```

Tento příklad kopíruje znaky `string2` z `string1`do. Pokud `i` je větší než nebo rovno 0, `string2[i]` je přiřazeno `string1[i]` a `i` sníženo. Když `i` dosáhne nebo klesne pod 0, spuštění `while` příkazu skončí.

## <a name="see-also"></a>Viz také

[while – příkaz (C++)](../cpp/while-statement-cpp.md)
