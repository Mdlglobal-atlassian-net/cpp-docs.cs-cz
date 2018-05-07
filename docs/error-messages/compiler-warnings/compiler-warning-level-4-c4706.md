---
title: Kompilátoru (úroveň 4) upozornění C4706 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4706
dev_langs:
- C++
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1131147a9600525746cb3e89119189ed9e5026a7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4706"></a>C4706 kompilátoru upozornění (úroveň 4)
přiřazení v rámci podmíněného výrazu  
  
 Hodnota testování podmíněného výrazu se výsledek přiřazení.  
  
 Přiřazení má hodnotu (hodnotu na levé straně přiřazení), které je možné právními předpisy v jiné výrazu, včetně výraz testu.  
  
 Následující ukázka generuje C4706:  
  
```  
// C4706a.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a  = b ) // C4706  
   {  
   }  
}  
```  
  
 Upozornění dojde i v případě, že dvakrát závorkách testovací podmínky:  
  
```  
// C4706b.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a  =  b ) ) // C4706  
   {  
   }  
}  
```  
  
 Pokud chcete otestovat relace a přiřazení, Nedělejte pomocí `==` operátor. Například následující řádek testy jestli a b jsou stejné:  
  
```  
// C4706c.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a == b )  
   {  
   }  
}  
```  
  
 Pokud máte v úmyslu provést test hodnota výsledek přiřazení, otestujte zajistit, že přiřazení je nulová nebo not null. Následující kód například nevygeneruje toto upozornění:  
  
```  
// C4706d.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a = b ) != 0 )  
   {  
   }  
}  
```