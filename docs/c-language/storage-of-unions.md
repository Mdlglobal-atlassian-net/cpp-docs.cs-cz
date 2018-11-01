---
title: Ukládání sjednocení
ms.date: 11/04/2016
helpviewer_keywords:
- storage, union
- union keyword [C], storage
- union keyword [C]
ms.assetid: b33d246a-8d20-41c4-89b2-ab05f1428792
ms.openlocfilehash: 06444151a453017055667885304ecb59534f5774
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602225"
---
# <a name="storage-of-unions"></a>Ukládání sjednocení

Úložiště přidružené k proměnné sjednocení je místo na disku požadované pro největšího člena sjednocení. Při uložení menšího člena sjednocení může proměnná sjednocení obsahovat nevyužitý paměťový prostor. Všichni členové jsou uloženi ve stejném paměťovém prostoru a začínají na stejné adrese. Uložená hodnota je přepsána pokaždé, když je hodnota přiřazena k jinému členu. Příklad:

```
union         /* Defines a union named x */
{
    char *a, b;
    float f[20];
} x;
```

Členové `x` sjednocení jsou v pořadí podle své deklarace, ukazatel na `char` hodnotu, `char` hodnotu a pole **float** hodnoty. Úložiště přidělené prvku `x` je požadované místo na disku pro pole o 20 prvcích `f`, jelikož `f` je nejdelším členem sjednocení. Vzhledem k tomu, že ke sjednocení není přidružena žádná značka, jeho typ je nepojmenovaný nebo „anonymní“.

## <a name="see-also"></a>Viz také

[Deklarace sjednocení](../c-language/union-declarations.md)