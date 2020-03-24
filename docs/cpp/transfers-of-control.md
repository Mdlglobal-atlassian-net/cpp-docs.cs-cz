---
title: Přenosy ovládacích prvků
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: c9a46ccb1cf519080c5105855e41ecd3ebc23f77
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188048"
---
# <a name="transfers-of-control"></a>Přenosy ovládacích prvků

Pomocí příkazu **goto** nebo popisku **case** v příkazu **Switch** můžete určit program, který se větví za inicializátorem. Takový kód je neplatný, dokud není deklarace, která obsahuje inicializátor v bloku, ohraničená blokem, v němž se nachází příkaz jump.

Následující příklad zobrazuje smyčku, která deklaruje a inicializuje objekty `total`, `ch` a `i`. K dispozici je také chybný příkaz **goto** , který přenáší kontrolu za inicializátorem.

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

V předchozím příkladu se příkaz **goto** pokusí přenést řízení po inicializaci `i`. Pokud však byly `i` deklarovány, ale nebyly inicializovány, byl by převod platný.

Objekty `total` a `ch`deklarované v bloku, který slouží jako *příkaz* příkazu **while** , jsou zničeny, pokud je tento blok ukončen pomocí příkazu **Break** .
