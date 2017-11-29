---
title: "Kompilátoru (úroveň 4) upozornění C4714 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4714
dev_langs: C++
helpviewer_keywords: C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c9cf416dd3bff91e8adf8e3f31e9b23b465706c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4714"></a>C4714 kompilátoru upozornění (úroveň 4)
Funkce označen jako __forceinline není vložená funkce  
  
 Danou funkci byla vybrána pro vložené rozšíření, ale kompilátor nebyla provedena vložené.  
  
 I když `__forceinline` se silnější informace pro kompilátor než `__inline`, vložené se stále provádí uvážení kompilátoru, ale žádné heuristiky se používají k určení výhody z vložené tuto funkci.  
  
 V některých případech kompilátor není vložené určitou funkci mechanických důvodů. Například kompilátor bude mimo řádek:  
  
-   Funkce, pokud by to vedlo kombinování SEH a C++ EH.  
  
-   Některé funkce s kopie zkonstruovat předaná hodnota - GX/EHs/EHa je na objekty.  
  
-   Funkce, které vracejí objekt unwindable podle hodnoty, když - GX/EHs/EHa v.  
  
-   Funkcí s vloženým sestavením při kompilování bez - Og/Ox/O1/O2.  
  
-   Funkce se seznamem argumentů proměnných.  
  
-   Funkce s **zkuste** – příkaz (C++ zpracování výjimek).  
  
 Následující ukázka generuje C4714:  
  
```  
// C4714.cpp  
// compile with: /Ob1 /GX /W4  
__forceinline void func1()  
{  
   try  
   {  
   }  
   catch (...)  
   {  
   }  
}  
  
void func2()  
{  
   func1();   // C4714  
}  
  
int main()  
{  
}  
```