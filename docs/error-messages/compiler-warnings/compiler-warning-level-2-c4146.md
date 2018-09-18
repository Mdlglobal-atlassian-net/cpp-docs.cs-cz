---
title: Upozornění (úroveň 2) C4146 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4146
dev_langs:
- C++
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41d21f2be76e67c58599e214df764316dc845e59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044623"
---
# <a name="compiler-warning-level-2-c4146"></a>Kompilátor upozornění (úroveň 2) C4146

Unární operátor minus použitý pro typ bez znaménka, výsledkem bude i bez znaménka

Typy bez znaménka může obsahovat pouze záporné hodnoty, takže Unární minus (negace) nemá smysl obvykle při použití pro typ bez znaménka. Operand a výsledek je záporná.

Prakticky proběhne, když se pokouší programátor express minimální celočíselná hodnota, která je -2147483648. Tuto hodnotu nelze zapsat jako -2147483648, protože výraz zpracovává ve dvou fázích:

1. Číslo 2147483648 vyhodnocena. Protože je větší než maximální celočíselnou hodnotu 2147483647, není typu 2147483648 [int](../../c-language/integer-types.md), ale `unsigned int`.

1. Unární minus je použité pro hodnotu, se výsledek bez znaménka, který se také být 2147483648.

Bez znaménka typu výsledku může způsobit neočekávané chování. Pokud v porovnání se použije výsledky, je porovnávání bez znaménka může použít, například pokud je druhý operand je `int`. To vysvětluje, proč níže uvedený program příklad vytiskne pouze jeden řádek.

Očekávaný druhý řádek `1 is greater than the most negative int`, není vytisknout, protože `((unsigned int)1) > 2147483648` má hodnotu false.

C4146 můžete vyhnout použitím INT_MIN z limits.h, která má typ **znaménkem**.

## <a name="example"></a>Příklad

Následující ukázka generuje C4146:

```
// C4146.cpp
// compile with: /W2
#include <stdio.h>

void check(int i)
{
    if (i > -2147483648)   // C4146
        printf_s("%d is greater than the most negative int\n", i);
}

int main()
{
    check(-100);
    check(1);
}
```