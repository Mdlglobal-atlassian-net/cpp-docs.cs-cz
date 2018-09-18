---
title: Neošetřené výjimky jazyka C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 57d014762ebc5427ccc4b9d26fff75addc883759
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097767"
---
# <a name="unhandled-c-exceptions"></a>Nezpracované výjimky jazyka C++

Pokud odpovídající obslužná rutina (nebo tlačítko se třemi tečkami **catch** obslužná rutina) nebyl nalezen aktuální výjimku, předdefinované `terminate` volá funkci run-time. (V libovolné obslužné rutině lze funkci `terminate` volat také explicitně.) Výchozí akcí funkce `terminate` je volání funkce `abort`. Chcete-li, aby funkce `terminate` vyvolala před ukončením aplikace jinou funkci v programu, vyvolejte funkci `set_terminate`, v jejímž jediném argumentu bude název funkce, která má být vyvolána. Funkci `set_terminate` lze vyvolat kdekoli v programu. `terminate` Rutina vždy volá poslední funkci předána jako argument pro `set_terminate`.

## <a name="example"></a>Příklad

Následující příklad vyvolá výjimku typu `char *`, ale neobsahuje obslužnou rutinu určenou k zachytávání výjimek typu `char *`. Volání funkce `set_terminate` dává pokyn, aby funkce `terminate` vyvolala funkci `term_func`.

```cpp
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

```Output
term_func was called by terminate.
```

Funkce `term_func` by měla ukončit program nebo aktuální vlákno, ideálně vyvoláním funkce `exit`. Pokud k tomu nedojde a místo toho přejde funkce zpět na volající funkci, je vyvolána funkce `abort`.

## <a name="see-also"></a>Viz také:

[Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)