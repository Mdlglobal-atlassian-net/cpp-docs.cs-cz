---
title: "Kompilátoru (úroveň 2) upozornění C4146 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4146
dev_langs: C++
helpviewer_keywords: C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f88b4e0dde56bc63619257264d46a7d2770fa58
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-2-c4146"></a>C4146 kompilátoru upozornění (úroveň 2)
Unární mínus – operátor u typu bez znaménka, výsledek stále bez znaménka  
  
 Typy bez znaménka mohou být uloženy pouze kladné hodnoty, takže Unární minus (negace) nemá smysl obvykle při použití typu bez znaménka. Operand a výsledek je záporný.  
  
 Prakticky k tomu dochází, když se pokouší programátorů express minimální celočíselná hodnota, která je -2147483648. Tuto hodnotu nelze zapsat jako -2147483648, protože výraz je zpracován ve dvou fázích:  
  
1.  Číslo 2147483648 vyhodnotí. Protože je větší než maximální celočíselnou hodnotu 2147483647, typ 2147483648 není [int](../../c-language/integer-types.md), ale `unsigned int`.  
  
2.  Unární minus se použije na hodnotu s nepodepsané výsledek, který se stane také být 2147483648.  
  
 Úroveň typu bez znaménka výsledku může způsobit neočekávané chování. Pokud v porovnání se používá výsledek a pak nepodepsané porovnání může použít, například při dalších operand `int`. Tato část popisuje, proč uvedený příklad program vytiskne pouze jeden řádek.  
  
 Očekávaný druhý řádek `1 is greater than the most negative int`, není vytisknout, protože `((unsigned int)1) > 2147483648` je false.  
  
 C4146 můžete vyhnout použitím int_min – z Limits.h –, která má typ **podepsané int**.  
  
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