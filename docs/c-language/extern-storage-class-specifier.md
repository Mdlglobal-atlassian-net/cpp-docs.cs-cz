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
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151387"
---
# <a name="extern-storage-class-specifier"></a>extern – specifikátor třídy úložiště

Proměnná deklarovaná pomocí **extern** – specifikátor třídy úložiště je odkaz na proměnnou se stejným názvem, které jsou definovány v jiném zdrojovém souboru. Používá se k definice proměnné na vnější úrovni zviditelnit. Proměnná deklarovaná jako **extern** nemá žádné úložiště přidělené sama za sebe, je pouze název.

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

V tomto příkladu je proměnná `i` je definována v Source1.c s počáteční hodnotou 1. **Extern** deklarace v Source2.c je je "i" viditelný v tomto souboru.

V `func` funkce, adresa globální proměnné `i` slouží k inicializaci **statické** proměnné ukazatele `external_i`. Tento postup funguje, protože globální proměnná má **statické** životnost, což znamená její adresa během provádění programu nezmění. Další, proměnná `i` je definována v rámci oboru `func` jako místní proměnná s počáteční hodnotou 16. Tato definice nemá vliv na hodnotu na vnější úrovni `i`, což je skrytý pomocí jejího názvu jako lokální proměnné. Hodnota globální proměnné `i` je teď přístupný pouze prostřednictvím ukazatele `external_i`.

## <a name="see-also"></a>Viz také:

[Specifikátory třídy úložiště pro deklarace na interní úrovni](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
