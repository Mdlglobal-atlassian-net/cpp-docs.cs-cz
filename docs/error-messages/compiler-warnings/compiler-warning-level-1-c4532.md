---
title: "Kompilátoru (úroveň 1) upozornění C4532 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4532
dev_langs: C++
helpviewer_keywords: C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5cec2f70dfa6781c237cc1c08079904c7b48e171
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4532"></a>C4532 kompilátoru upozornění (úroveň 1)
'continue': přechod z __finally/finally bloku má undefined chování při ukončení zpracování  
  
 Kompilátor zjistil jednu z následujících klíčových slov:  
  
-   [pokračovat](../../cpp/continue-statement-cpp.md)  
  
-   [Konec](../../cpp/break-statement-cpp.md)  
  
-   [goto – příkaz](../../cpp/goto-statement-cpp.md)  
  
 způsobuje přechod z [__finally](../../cpp/try-finally-statement.md) nebo [nakonec](../../dotnet/finally.md) bloku během abnormální ukončení.  
  
 Pokud dojde k výjimce, a když je právě v zásobníku odděleny během provádění obslužné rutiny ukončení ( `__finally` nebo nakonec blokuje), a váš kód přejde z `__finally` před zablokovat `__finally` bloku zakončení, chování není definován. Ovládací prvek nemusí vracet unwinding kódu, takže výjimku nemusí správně ošetřit.  
  
 Pokud je třeba přeskočit mimo **__finally** blokovat, nejprve zkontrolujte abnormální ukončení.  
  
 Následující ukázka generuje C4532; jednoduše komentář příkazy přechod k vyřešení upozornění.  
  
```  
// C4532.cpp  
// compile with: /W1  
// C4532 expected  
int main() {  
   int i;  
   for (i = 0; i < 10; i++) {  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         continue;  
      }  
  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         break;  
      }  
   }  
}  
```