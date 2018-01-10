---
title: __restrict | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __restrict_cpp
dev_langs: C++
helpviewer_keywords: __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2c21872c5d6fe6000038a3a2f4fe39451b566dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="restrict"></a>__restrict
Podobně jako **__declspec ( [omezit](../cpp/restrict.md) )** modifikátor, `__restrict` – klíčové slovo označuje, zda symbol není v aktuálním oboru použít alias. Klíčové slovo `__restrict` se od modifikátoru `__declspec ( restrict )` liší následujícími způsoby:  
  
-   Klíčové slovo `__restrict` je platné pouze pro proměnné, klíčové slovo `__declspec ( restrict )` je platné pouze pro deklarace a definice funkcí.  
  
-   Klíčové slovo `__restrict` se podobá klíčovému slovu `restrict` dle specifikace C99, slovo `__restrict` však lze použít v programech jazyka C++ i C.  
  
-   Je-li použito klíčové slovo `__restrict`, kompilátor nebude šířit vlastnost proměnné, že nemá alias. To znamená Chcete-li přiřadit `__restrict` proměnnou jinou hodnotu než`__restrict` proměnné, kompilátor bude stále povolit jiných __restrict proměnná mít alias. Zde je rozdíl oproti chování klíčového slova `restrict` dle specifikace C99.  
  
 Obecně platí, pokud budete mít vliv na chování celý funkce, je lepší použít `__declspec ( restrict )` než klíčové slovo.  
  
 V sadě Visual Studio 2015 a novější `__restrict` lze použít v C++ odkazy.  
  
> [!NOTE]
>  Pokud se používá v proměnné, která má také [volatile](../cpp/volatile-cpp.md) – klíčové slovo, `volatile` bude mít přednost.  
  
## <a name="example"></a>Příklad  
  
```  
// __restrict_keyword.c  
// compile with: /LD  
// In the following function, declare a and b as disjoint arrays  
// but do not have same assurance for c and d.  
void sum2(int n, int * __restrict a, int * __restrict b,   
          int * c, int * d) {  
   int i;  
   for (i = 0; i < n; i++) {  
      a[i] = b[i] + c[i];  
      c[i] = b[i] + d[i];  
    }  
}  
  
// By marking union members as __restrict, tell compiler that  
// only z.x or z.y will be accessed in any given scope.  
union z {  
   int * __restrict x;  
   double * __restrict y;  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)