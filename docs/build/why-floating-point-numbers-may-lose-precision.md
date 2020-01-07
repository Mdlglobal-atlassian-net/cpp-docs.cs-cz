---
title: Proč čísla s plovoucí desetinnou čárkou mohou ztratit přesnost
ms.date: 11/04/2016
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
ms.openlocfilehash: 373ce9fa2c2c96fac349940076873a4a637a9dbe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298711"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Proč čísla s plovoucí desetinnou čárkou mohou ztratit přesnost

Desítkové hodnoty s plovoucí desetinnou čárkou většinou nemají přesnou binární reprezentaci. Jedná se o vedlejší účinky toho, jak CPU představuje data s plovoucí desetinnou čárkou. Z tohoto důvodu se může stát, že dojde ke ztrátě přesnosti a některé operace s plovoucí desetinnou čárkou můžou způsobit neočekávané výsledky.

Toto chování je výsledkem jedné z následujících akcí:

- Binární reprezentace desítkového čísla nemůže být přesně.

- Došlo k neshodě typů mezi použitými čísly (například kombinování plovoucích a dvojitých).

Aby bylo možné chování vyřešit, většina programátorů buď zajistěte, aby byla hodnota větší nebo menší, než je potřeba, nebo získají a používají binární kódované číslo (BCD), které bude uchovávat přesnost.

Binární reprezentace hodnot s plovoucí desetinnou čárkou má vliv na přesnost a přesnost výpočtů s plovoucí desetinnou čárkou. Microsoft vizuálů C++ používá [formát s plovoucí desetinnou čárkou standardu IEEE](ieee-floating-point-representation.md).

## <a name="example"></a>Příklad

```c
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

Pro EPSILON můžete použít konstanty FLT_EPSILON, které jsou definovány pro typ float as 1.192092896 e-07F nebo DBL_EPSILON, který je definován pro Double AS 2.2204460492503131 e-016. Pro tyto konstanty musíte zahrnout float. h. Tyto konstanty jsou definovány jako nejmenší kladné číslo x, což znamená, že x + 1,0 není rovno 1,0. Vzhledem k tomu, že se jedná o velmi malé číslo, měli byste použít uživatelsky definovanou toleranci pro výpočty zahrnující velmi velká čísla.

## <a name="see-also"></a>Viz také:

[Optimalizace kódu](optimizing-your-code.md)
