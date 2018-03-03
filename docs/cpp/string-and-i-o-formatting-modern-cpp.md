---
title: "Řetězec a I-O formátování (moderní verze jazyka C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a13861fe03547e37c4de72c21a528e297a217511
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="string-and-io-formatting-modern-c"></a>Formátování řetězců a I/O (moderní verze jazyka C++)
C++ [iostreams](../standard-library/iostream.md) podporují formátovaný řetězec vstupně-výstupní operace. Například následující kód ukazuje, jak nastavit cout k formátování celé výstup v šestnáctkové soustavě, nejprve ukládání mimo aktuální stav a znovu nastavení později, protože po formátování stavu je předán cout, zůstane tímto způsobem, dokud nezměníte, ne jenom pro jeden řádek kódu.  
  
```cpp  
#include <iostream>  
#include <iomanip>  
  
using namespace std;  
  
int main()   
{  
    ios state(nullptr);  
  
    cout << "The answer in decimal is: " << 42 << endl;  
  
    state.copyfmt(cout); // save current formatting  
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers  
        << hex   
        << uppercase   
        << setw(8)   
        << setfill('0')   
        << 42            // the actual value we wanted to print out  
        << endl;  
    cout.copyfmt(state); // restore previous formatting  
}  
  
```  
  
 To může být zcela příliš komplikované v mnoha případech. Jako alternativu můžete použít Boost.Format z knihoven C++ nárůst, i když je nestandardní. Můžete si stáhnout všechny knihovny nárůst z [nárůst](http://www.boost.org/) webu.  
  
 Některé výhody Boost.Format jsou:  
  
-   Bezpečné: Bezpečných a vyvolá výjimku pro chyby – například specifikace příliš málo nebo příliš mnoho položek.  
  
-   Rozšiřitelné: Funguje pro libovolného typu, který Streamovat.  
  
-   Pohodlná: Standardní Posix a podobné řetězce formátu.  
  
 I když Boost.Format je založený na C++ [iostreams](../standard-library/iostream-programming.md), které jsou bezpečné a rozšiřitelné, nejsou, optimalizovaný výkon. Pokud požadujete optimalizace výkonu, zvažte C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) a [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), které jsou rychlé a snadno se používá. Jsou to ale není rozšiřitelné nebo před ohrožení zabezpečení. (Existuje bezpečné verzí, ale jejich způsobit snížení výkonu mírné. Další informace najdete v tématu [printf_s –, _printf_s_l –, wprintf_s –, _wprintf_s_l –](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) a [sprintf_s –, _sprintf_s_l –, swprintf_s –, _swprintf_s_l –](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).  
  
 Následující kód ukazuje některé nárůst formátování funkce.  
  
```cpp  
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );  
    // s contains "hello hello world"    
  
    for( auto i = 0; i < names.size(); ++i )  
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];  
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789  
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321  
  
```  
  
## <a name="see-also"></a>Viz také  
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)   
 [\<iostream >](../standard-library/iostream.md)   
 [\<omezení >](../standard-library/limits.md)   
 [\<iomanip – >](../standard-library/iomanip.md)
