---
title: Upozornění kompilátoru (úroveň 2) C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: d595befc80d954c8fb84f83ad6c4e0cb5f4fcf26
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052172"
---
# <a name="compiler-warning-level-2-c4146"></a>Upozornění kompilátoru (úroveň 2) C4146

Unární operátor minus aplikovaný na typ bez znaménka, výsledek je dál nepodepsaný.

Typy bez znaménka můžou uchovávat jenom nezáporné hodnoty, takže Unární znaménko minus (negace) obvykle nemá smysl při použití na typ bez znaménka. Operand i výsledek jsou nezáporné.

Prakticky k tomu dochází, když programátor pokouší vyjádřit minimální celočíselnou hodnotu, což je-2147483648. Tuto hodnotu nelze zapsat jako-2147483648, protože výraz je zpracován ve dvou fázích:

1. Číslo 2147483648 je vyhodnoceno. Protože je větší než maximální celočíselná hodnota 2147483647, typ 2147483648 není [int](../../c-language/integer-types.md), ale `unsigned int`.

1. Unární znaménko minus se aplikuje na hodnotu s výsledkem bez znaménka, což také nastane 2147483648.

Typ bez znaménka výsledku může způsobit neočekávané chování. Pokud je výsledek použit v porovnání, pak může být použito porovnání bez znaménka, například když je druhý operand `int`. Vysvětluje, proč ukázkový program uvedený níže tiskne pouze jeden řádek.

Očekávaný druhý řádek, `1 is greater than the most negative int`, není vytištěn, protože `((unsigned int)1) > 2147483648` je false.

C4146 můžete zabránit pomocí INT_MIN z Limits. h, který má typ **signed int**.

## <a name="example"></a>Příklad

Následující ukázka generuje C4146:

```cpp
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