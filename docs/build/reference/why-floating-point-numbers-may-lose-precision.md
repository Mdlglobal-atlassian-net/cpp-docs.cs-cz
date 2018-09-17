---
title: Proč čísla s plovoucí desetinnou čárkou mohou ztratit přesnost | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de54610676ade49f7ce41e00ed0049b20e46709c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700010"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Proč čísla s plovoucí desetinnou čárkou mohou ztratit přesnost

Desetinná čísla s plovoucí desetinnou čárkou obvykle nemají přesné binárního formátu. Toto je vedlejším účinkem jak představuje procesoru s plovoucí desetinnou čárkou datového bodu. Z tohoto důvodu se můžete setkat s určitou ztrátou přesnosti a některé operace s plovoucí desetinnou čárkou může vést k neočekávaným výsledkům.

Toto chování je výsledkem jednoho z následujících akcí:

- Binární reprezentace desetinné číslo nemusí být přesné.

- Došlo k neshodě typů mezi čísla použít (například kombinování plovoucí desetinnou čárkou a double).

Chcete-li vyřešit chování, většina programátoři buď zajistit, že hodnota je větší nebo menší než co je potřeba, nebo získání a použití knihovny Binary programového Decimal (BCD), které bude udržovat přesnost.

Binární reprezentace hodnoty s plovoucí desetinnou čárkou ovlivňuje a přesnost výpočtů s plovoucí desetinnou čárkou. Microsoft Visual C++ používá [formátu s plovoucí desetinnou čárkou IEEE](../../build/reference/ieee-floating-point-representation.md).

## <a name="example"></a>Příklad

```
// Floating-point_number_precision.c
// Compile options needed: none. Value of c is printed with a decimal
// point precision of 10 and 6 (printf rounded value by default) to
// show the difference
#include <stdio.h>

#define EPSILON 0.0001   // Define your own tolerance
#define FLOAT_EQ(x,v) (((v - EPSILON) < x) && (x <( v + EPSILON)))

int main() {
   float a, b, c;

   a = 1.345f;
   b = 1.123f;
   c = a + b;
   // if (FLOAT_EQ(c, 2.468)) // Remove comment for correct result
   if (c == 2.468)            // Comment this line for correct result
      printf_s("They are equal.\n");
   else
      printf_s("They are not equal! The value of c is %13.10f "
                "or %f",c,c);
}
```

```Output
They are not equal! The value of c is  2.4679999352 or 2.468000
```

## <a name="comments"></a>Komentáře

EPSILON, můžete použít konstanty FLT_EPSILON, která je definována pro plovoucí desetinnou čárkou jako 1.192092896e-07F, nebo DBL_EPSILON, která je definována pro double jako 2.2204460492503131e-016. Je třeba zahrnout float.h pro tyto konstanty. Tyto konstanty jsou definovány jako nejmenší kladné číslo x, například tento x + 1,0 není roven 1,0. Protože jde o velmi malé číslo, by měly používat uživatelem definované proti chybám pro výpočty s velmi velká čísla.

## <a name="see-also"></a>Viz také

[Optimalizace kódu](../../build/reference/optimizing-your-code.md)