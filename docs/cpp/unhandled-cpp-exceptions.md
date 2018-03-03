---
title: "Neošetřené výjimky jazyka C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6b7410d34b7b9f31c96cf7e991133770099735a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="unhandled-c-exceptions"></a>Nezpracované výjimky jazyka C++
Pokud odpovídající obslužná rutina (nebo třemi tečkami **catch** obslužné rutiny) nebyl nalezen pro aktuální výjimky, předdefinovanou `terminate` běhové funkce je volána. (V libovolné obslužné rutině lze funkci `terminate` volat také explicitně.) Výchozí akcí funkce `terminate` je volání funkce `abort`. Chcete-li, aby funkce `terminate` vyvolala před ukončením aplikace jinou funkci v programu, vyvolejte funkci `set_terminate`, v jejímž jediném argumentu bude název funkce, která má být vyvolána. Funkci `set_terminate` lze vyvolat kdekoli v programu. `terminate` Rutina vždy volá funkci naposledy zadaný jako argument pro `set_terminate`.  
  
## <a name="example"></a>Příklad  
 Následující příklad vyvolá výjimku typu `char *`, ale neobsahuje obslužnou rutinu určenou k zachytávání výjimek typu `char *`. Volání funkce `set_terminate` dává pokyn, aby funkce `terminate` vyvolala funkci `term_func`.  
  
```  
// exceptions_Unhandled_Exceptions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
void term_func() {  
   cout << "term_func was called by terminate." << endl;  
   exit( -1 );  
}  
int main() {  
   try  
   {  
      set_terminate( term_func );  
      throw "Out of memory!"; // No catch handler for this exception  
   }  
   catch( int )  
   {  
      cout << "Integer exception raised." << endl;  
   }  
   return 0;  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
term_func was called by terminate.  
```  
  
 Funkce `term_func` by měla ukončit program nebo aktuální vlákno, ideálně vyvoláním funkce `exit`. Pokud k tomu nedojde a místo toho přejde funkce zpět na volající funkci, je vyvolána funkce `abort`.  
  
## <a name="see-also"></a>Viz také  
 [Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)