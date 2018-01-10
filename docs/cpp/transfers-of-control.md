---
title: "Přenosy ovládacích prvků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 594ec49242e919f1ea9bd059588b21292af55409
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="transfers-of-control"></a>Přenosy ovládacích prvků
Můžete použít `goto` příkaz nebo **případ** návěští v `switch` příkaz Chcete-li určit program, který větví po inicializátoru. Takový kód je neplatný, dokud není deklarace, která obsahuje inicializátor v bloku, ohraničená blokem, v němž se nachází příkaz jump.  
  
 Následující příklad zobrazuje smyčku, která deklaruje a inicializuje objekty `total`, `ch` a `i`. Je zde také chybný příkaz `goto`, který předává řízení kolem inicializátoru.  
  
```  
// transfers_of_control.cpp  
// compile with: /W1  
// Read input until a nonnumeric character is entered.  
int main()  
{  
   char MyArray[5] = {'2','2','a','c'};  
   int i = 0;  
   while( 1 )  
   {  
      int total = 0;  
  
      char ch = MyArray[i++];  
  
      if ( ch >= '0' && ch <= '9' )  
      {  
         goto Label1;  
  
         int i = ch - '0';  
      Label1:  
         total += i;   // C4700: transfers past initialization of i.  
      } // i would be destroyed here if  goto error were not present  
   else  
      // Break statement transfers control out of loop,  
      //  destroying total and ch.  
      break;  
   }  
}  
```  
  
 V předchozím příkladu se příkaz `goto` pokusí přenést řízení kolem inicializace `i`. Pokud však byly `i` deklarovány, ale nebyly inicializovány, byl by převod platný.  
  
 Objekty `total` a `ch`, deklarované v bloku, která slouží jako *příkaz* z `while` příkaz, budou ztraceny při tomto bloku je byl ukončen pomocí `break` příkaz.  
  
