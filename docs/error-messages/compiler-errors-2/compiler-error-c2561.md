---
title: "C2561 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2561
dev_langs: C++
helpviewer_keywords: C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ce30ffb454deb7bc847e736458295d037826a0ad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2561"></a>C2561 chyby kompilátoru
"identifikátor": funkce musí vrátit hodnotu  
  
 Funkce byla deklarována jako vrací hodnotu, ale neobsahuje definici funkce `return` příkaz.  
  
 Tato chyba může být způsobeno prototypu nesprávná funkce:  
  
1.  Pokud funkce nevrací hodnotu, deklarovat s návratovým typem funkce [void](../../cpp/void-cpp.md).  
  
2.  Zkontrolujte, jestli všechny možné větve funkce vrátí hodnotu typu deklarován v prototypu.  
  
3.  Funkce C++ obsahující vložené sestavení rutiny, které ukládají návratovou hodnotu v `AX` registrace může být nutné příkaz return. Zkopírujte hodnotu v `AX` dočasné proměnné a vrátí tuto proměnnou z funkce.  
  
 Následující ukázka generuje C2561:  
  
```  
// C2561.cpp  
int Test(int x) {  
   if (x) {  
      return;   // C2561  
      // try the following line instead  
      // return 1;  
   }  
   return 0;  
}  
  
int main() {  
   Test(1);  
}  
```