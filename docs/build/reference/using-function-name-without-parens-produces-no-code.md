---
title: "Použití názvu funkce bez () nevygeneruje žádný kód | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 79f360bffa4938098b4b37dd2260596c70669d12
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-function-name-without--produces-no-code"></a>Použití názvu funkce bez závorek () nevygeneruje žádný kód
Pokud se použije v programu deklarovaný název funkce bez závorek, kompilátor nevytváří kódu. Důvodem je to bez ohledu na to, zda funkce využívá parametry, protože kompilátor vypočítá adresu funkce; ale protože operátor volání funkce "(") není dostupná, žádné Přišla žádost. Tento výsledek je podobný následujícímu:  
  
```  
// compile with /Wall to generate a warning  
int a;  
a;      // no code generated here either  
```  
  
 V jazyce Visual C++ i pomocí úroveň upozornění 4 generuje žádný výstup diagnostiky. Žádná upozornění; vytváří žádný kód.  
  
 Následující ukázkový kód zkompiluje (s upozorněním) a propojí správně bez chyb ale nevygeneruje žádný kód reference na `funcn( )`. Tento postup fungovat správně přidejte operátor volání funkce "(").  
  
```  
#include <stdio.h>  
void funcn();  
  
int main() {  
   funcn;      /* missing function call operator;   
                  call will fail.  Use funcn() */  
   }  
  
void funcn() {  
   printf("\nHello World\n");  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace kódu](../../build/reference/optimizing-your-code.md)