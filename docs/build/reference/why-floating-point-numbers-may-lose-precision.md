---
title: "Proč čísla s plovoucí desetinnou čárkou mohou ztratit přesnost | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 371aad5dc573a13ca834d8d6d9667a43bb40324e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>Proč čísla s plovoucí desetinnou čárkou mohou ztratit přesnost
Desetinná čísla s plovoucí desetinnou čárkou obvykle nemají přesnou binární reprezentace. Toto je vedlejším účinkem jak procesoru reprezentuje data s plovoucí desetinnou. Z tohoto důvodu může dojít k některé ztrátu přesnosti a některé operace s plovoucí desetinnou čárkou mohou vést k neočekávaným výsledkům.  
  
 Toto chování je výsledkem jednu z těchto možností:  
  
-   Binární reprezentace desetinné číslo nemusí být přesné.  
  
-   Došlo k neshodě typu rozsahu mezi zadanými čísly používá (například směšovací float a dvojitou).  
  
 Chování vyřešíte většinu programátory v jazyce, který se buď zajistěte, aby hodnota je větší nebo menší než co je potřeba, nebo získat a použít knihovnu Binary Coded Decimal (BCD), která bude spravovat přesnost.  
  
 Binární reprezentace hodnoty s plovoucí desetinnou čárkou ovlivňuje a přesnost výpočty s plovoucí desetinnou čárkou. Microsoft Visual C++ používá [formátu plovoucí desetinné čárky IEEE](../../build/reference/ieee-floating-point-representation.md).  
  
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
 Epsilon –, můžete použít konstanty flt_epsilon –, která je definována pro float jako 1.192092896e-07F, nebo dbl_epsilon –, která je definována pro dvojitou jako 2.2204460492503131e-016. Je nutné zahrnout float.h – pro tyto konstanty. Tyto konstanty jsou definovány jako nejmenší kladné číslo x, například tento x + 1.0 není rovno hodnotě 1.0. Protože to je velmi malé množství, by měly používat uživatelské tolerance pro výpočty s velmi velká čísla.  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace kódu](../../build/reference/optimizing-your-code.md)