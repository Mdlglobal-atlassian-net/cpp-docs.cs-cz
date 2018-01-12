---
title: "Kompilátoru (úroveň 4) upozornění C4706 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4706
dev_langs: C++
helpviewer_keywords: C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 824028fb7fd6d563a7f49017eb6b35d1443490bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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