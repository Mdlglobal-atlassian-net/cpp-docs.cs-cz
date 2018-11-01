---
title: Používání operátorů sčítání
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 78dc559a83626057603027e30742435b1128e31c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557687"
---
# <a name="using-the-additive-operators"></a>Používání operátorů sčítání

Následující příklady ilustrující operátory sčítání a odčítání používají tyto deklarace:

```
int i = 4, j;
float x[10];
float *px;
```

Tyto příkazy jsou stejné:

```
px = &x[4 + i];
px = &x[4] + i;
```

Hodnota `i` je vynásobena délkou **float** a přidán do `&x[4]`. Výsledná hodnota ukazatele je adresa prvku `x[8]`.

```
j = &x[i] - &x[i-2];
```

V tomto příkladu je adresa třetího prvku pole `x` (určená pomocí `x[i-2]`) odečtena od adresy pátého prvku pole `x` (určené pomocí `x[i]`). Rozdíl je vydělen délkou z **float**; výsledkem je celočíselná hodnota 2.

## <a name="see-also"></a>Viz také

[Sčítací operátory jazyka C](../c-language/c-additive-operators.md)