---
title: "Použití polí (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d7cab4f8bcc4deb8353f4cef0828af829da008e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-arrays-c"></a>Použití polí (C++)
Máte přístup k jednotlivé prvky pole pomocí operátor dolního indexu pole (`[ ]`). Pokud jednorozměrné pole se používá v výraz, který nemá žádné dolní index, názvu pole se vyhodnotí jako ukazatel na první prvek v poli.  
  
```  
// using_arrays.cpp  
int main() {  
   char chArray[10];  
   char *pch = chArray;   // Evaluates to a pointer to the first element.  
   char   ch = chArray[0];   // Evaluates to the value of the first element.  
   ch = chArray[3];   // Evaluates to the value of the fourth element.  
}  
```  
  
 Pokud používáte vícerozměrná pole, můžete použít různé kombinace ve výrazech.  
  
```  
// using_arrays_2.cpp  
// compile with: /EHsc /W1  
#include <iostream>  
using namespace std;  
int main() {  
   double multi[4][4][3];   // Declare the array.  
   double (*p2multi)[3];  
   double (*p1multi);  
  
   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.  
   p2multi = multi[3];               // Make p2multi point to  
                                     // fourth "plane" of multi.  
   p1multi = multi[3][2];            // Make p1multi point to  
                                     // fourth plane, third row  
                                     // of multi.  
}  
```  
  
 V předchozí kód `multi` je trojrozměrné typu `double`. `p2multi` Ukazatel ukazuje na pole typu `double` velikosti tři. V tomto příkladu se používá pole s jeden, dva a tři dolní indexy. I když je více společné pro všechny dolní indexy, zadejte jako v `cout` příkaz, je někdy užitečné k výběru určitou podmnožinu elementy pole, jak je znázorněno v příkazech, které následují `cout`.  
  
## <a name="see-also"></a>Viz také  
 [Pole](../cpp/arrays-cpp.md)