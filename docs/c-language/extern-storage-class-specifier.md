---
title: extern – specifikátor třídy úložiště
ms.date: 07/10/2018
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
ms.openlocfilehash: 6bbae7c778f5196ac0dca387265499b27119a367
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233831"
---
# <a name="extern-storage-class-specifier"></a>extern – specifikátor třídy úložiště

Proměnná deklarovaná pomocí specifikátoru třídy úložiště **extern** je odkaz na proměnnou se stejným názvem definovaným v jiném zdrojovém souboru. Slouží k tomu, aby byla definice proměnné na externí úrovni viditelná. Proměnná deklarovaná jako **extern** nemá žádné přidělené úložiště. je pouze název.

## <a name="example"></a>Příklad

Tento příklad ilustruje deklarace na vnitřní a vnější úrovni:

```c

// Source1.c

int i = 1;

// Source2. c

#include <stdio.h>

// Refers to the i that is defined in Source1.c:
extern int i;

void func(void);

int main()
{
    // Prints 1:
    printf_s("%d\n", i);
    func();
    return;
}

void func(void)
{
    // Address of global i assigned to pointer variable:
    static int *external_i = &i;

    // This definition of i hides the global i in Source.c:
    int i = 16;

    // Prints 16, 1:
    printf_s("%d\n%d\n", i, *external_i);
}
```

V tomto příkladu je proměnná `i` definována v source1. c s počáteční hodnotou 1. **Externí** deklarace v SOURCE2. c znamená, že je v tomto souboru vidět "i".

Ve `func` funkci je adresa globální proměnné `i` použita k inicializaci **statické** proměnné `external_i`ukazatele. Tato operace funguje, protože globální proměnná má **statickou** životnost, což znamená, že se její adresa nemění během provádění programu. Dále je proměnná `i` definována v rámci oboru `func` jako místní proměnná s počáteční hodnotou 16. Tato definice nemá vliv na hodnotu hodnoty na externí úrovni `i`, která je skrytá pomocí jejího názvu pro místní proměnnou. Hodnota globální `i` je teď dostupná jenom přes ukazatel `external_i`.

## <a name="see-also"></a>Viz také

[Specifikátory třídy úložiště pro deklarace na interní úrovni](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
