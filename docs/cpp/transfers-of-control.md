---
title: Přenosy ovládacích prvků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8bec66d25be2cb56c75f42f60af2ccd5e3f759ad
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947708"
---
# <a name="transfers-of-control"></a>Přenosy ovládacích prvků
Můžete použít **goto** příkazu nebo **případ** popisku v **přepnout** příkaz k určení programu, která je rozvětvena kolem inicializátoru. Takový kód je neplatný, dokud není deklarace, která obsahuje inicializátor v bloku, ohraničená blokem, v němž se nachází příkaz jump.  
  
 Následující příklad zobrazuje smyčku, která deklaruje a inicializuje objekty `total`, `ch` a `i`. Je zde také chybný **goto** příkaz, který předává řízení kolem inicializátoru.  
  
```cpp 
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
  
 V předchozím příkladu **goto** příkaz se pokusí přenést řízení kolem inicializace `i`. Pokud však byly `i` deklarovány, ale nebyly inicializovány, byl by převod platný.  
  
 Objekty `total` a `ch`, které jsou deklarovány v bloku, která slouží jako *příkaz* z **při** prohlášení, jsou zničeny, když tento blok ukončen pomocí  **Konec** příkazu.  
  
