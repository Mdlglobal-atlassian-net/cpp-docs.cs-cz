---
title: Neošetřené výjimky jazyka C++
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
ms.openlocfilehash: f42a4e2af46ab7690d6f4bc9641c09f3757eb6b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160551"
---
# <a name="unhandled-c-exceptions"></a>Neošetřené výjimky jazyka C++

Pokud se pro aktuální výjimku nenajde vyhovující obslužná rutina (nebo obslužná rutina **catch** se třemi tečkami), je volána předdefinovaná funkce `terminate` běhu. (Můžete také explicitně volat `terminate` v jakékoli z vašich obslužných rutin.) Výchozí akcí `terminate` je volání `abort`. Chcete-li, aby funkce `terminate` vyvolala před ukončením aplikace jinou funkci v programu, vyvolejte funkci `set_terminate`, v jejímž jediném argumentu bude název funkce, která má být vyvolána. Funkci `set_terminate` lze vyvolat kdekoli v programu. Rutina `terminate` vždy volá poslední funkci zadanou jako argument pro `set_terminate`.

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

## <a name="see-also"></a>Viz také

[Moderní C++ osvědčené postupy pro výjimky a zpracování chyb](../cpp/errors-and-exception-handling-modern-cpp.md)
