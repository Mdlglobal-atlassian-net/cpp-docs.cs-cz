---
title: "Rozdíly ve zpracování výjimek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cfa736c83dd76ff8b8f677daad54104ff507df03
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="exception-handling-differences"></a>Rozdíly ve zpracování výjimek
Hlavní rozdíl mezi strukturovaným zpracováním výjimek a zpracováním výjimek v jazyce C++ je, že v modelu zpracování výjimek v jazyce C++ se model zabývá typy, zatímco model zpracování strukturovaných výjimek jazyka C se zabývá výjimkami jednoho typu – konkrétně `unsigned int`. Výjimky jazyka C jsou označeny hodnotou unsigned integer, na rozdíl od výjimek jazyka C++, které jsou určeny typem dat. Jakmile je v jazyce C vyvolána výjimka, vykoná každý popisovač filtr, který prověří kontext výjimek jazyka C a určí, zda výjimku přijmout, předat ji jiné obslužné rutině, nebo ji ignorovat. Jakmile je vyvolána výjimka v jazyce C++, může být libovolného typu.  
  
 Druhý rozdíl je v tom, že model zpracování strukturovaných výjimek jazyka C je označován jako „asynchronní“, ve kterém dochází k druhotnému výskytu výjimek vzhledem k normálnímu toku řízení. Mechanismus zpracování výjimek jazyka C++ je plně „synchronní“, což znamená, že výjimky se objevují pouze při jejich vyvolání.  
  
 Pokud C výjimka vyvolána v programu C++, to mohlo být zpracováno strukturovaného výjimek obslužná rutina s jeho přidružené filtru nebo jazyka C++ **catch** obslužnou rutinu, podle toho, co je dynamicky blíže kontext výjimky. Například následující programu C++ vyvolá výjimku C uvnitř jazyka C++ **zkuste** kontextu:  
  
## <a name="example"></a>Příklad  
  
```  
// exceptions_Exception_Handling_Differences.cpp  
// compile with: /EHa  
#include <iostream>  
  
using namespace std;  
void SEHFunc( void );  
  
int main() {  
   try {  
      SEHFunc();  
   }  
   catch( ... ) {  
      cout << "Caught a C exception."<< endl;  
   }  
}  
  
void SEHFunc() {  
   __try {  
      int x, y = 0;  
      x = 5 / y;  
   }  
   __finally {  
      cout << "In finally." << endl;  
   }  
}  
```  
  
```Output  
In finally.  
Caught a C exception.  
```  
  
##  <a name="_core_c_exception_wrapper_class"></a>Obálková třída výjimky jazyka C  
 V jednoduchém příkladu jako výše, může být C výjimka zachycena pouze pomocí třemi tečkami (**...** ) **catch** obslužné rutiny. Obslužné rutině není dodána žádná informace o typu nebo povaze výjimky. Zatímco tato metoda funguje, v některých případech je zapotřebí definovat transformaci mezi dvěma modely zpracování výjimek tak, aby byly jednotlivé výjimky jazyka C spojeny s konkrétní třídou. To lze provést definováním třídy „zabalení“ výjimky jazyka C, kterou lze použít nebo odvodit pro vytvoření atributu pro určitý typ třídy na výjimku jazyka C. Tímto způsobem může ošetřit jednotlivých výjimkách C jazyka C++ **catch** obslužná rutina samostatně než v předchozím příkladu.  
  
 Třída zabalení může obsahovat rozhraní skládající se z některých členských funkcí, které určují hodnotu výjimky a které přistupují k rozšířeným kontextovým informacím poskytnutým modelem zpracování výjimek jazyka C. Je také možné definovat výchozí konstruktor a konstruktor, který přijímá argument `unsigned int` (pro poskytnutí zastoupení základní výjimky jazyka C) a konstruktor bitové kopie. Následuje možná implementace třídy zabalení výjimky jazyka C:  
  
```  
// exceptions_Exception_Handling_Differences2.cpp  
// compile with: /c  
class SE_Exception {  
private:  
   SE_Exception() {}  
   SE_Exception( SE_Exception& ) {}  
   unsigned int nSE;  
public:  
   SE_Exception( unsigned int n ) : nSE( n ) {}  
   ~SE_Exception() {}  
   unsigned int getSeNumber() {  
      return nSE;  
   }  
};  
  
```  
  
 Aby bylo možné tuto třídu použít, je nutné nainstalovat vlastní funkci překladu výjimek jazyka C, která je volána mechanismem zpracování interních výjimek, při každém vyvolání výjimky jazyka C. V rámci vaší funkce překladu žádné typové výjimku můžete vyvolat (možná `SE_Exception` typu nebo typu třídy odvozené od `SE_Exception`), může být zachycena příslušné odpovídající C++ **catch** obslužné rutiny. Funkce překladu může jednoduše provést vrácení, což znamená, že nedošlo ke zpracování výjimky. Pokud C výjimky, vyvolá funkce překladu samotné [ukončit](../c-runtime-library/reference/terminate-crt.md) je volána.  
  
 Chcete-li zadat vlastní překlad funkce, zavolejte [_set_se_translator –](../c-runtime-library/reference/set-se-translator.md) funkce s názvem funkce překladu jako jeden argument. Překlad funkce, která můžete psát nazývá jednou pro každé vyvolání funkce v zásobníku, která má **zkuste** bloky. Neexistuje žádný výchozí funkce překladu; Pokud nezadáte jeden voláním `_set_se_translator`, C výjimka může být pouze zachycena třemi tečkami **catch** obslužné rutiny.  
  
## <a name="example"></a>Příklad  
 Následující kód například nainstaluje vlastní funkci překladu a poté vyvolá výjimku jazyka C, která je zabalena do třídy `SE_Exception`:  
  
```  
// exceptions_Exception_Handling_Differences3.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <eh.h>  
#include <windows.h>  
  
class SE_Exception {  
private:  
   SE_Exception() {}  
   unsigned int nSE;  
  
public:  
   SE_Exception( SE_Exception& e) : nSE(e.nSE) {}  
   SE_Exception(unsigned int n) : nSE(n) {}  
   ~SE_Exception() {}  
   unsigned int getSeNumber() { return nSE; }  
};  
  
void SEFunc() {  
   __try {  
      int x, y = 0;  
      x = 5 / y;  
    }  
    __finally {  
      printf_s( "In finally\n" );  
   }  
}  
  
void trans_func( unsigned int u, _EXCEPTION_POINTERS* pExp ) {  
   printf_s( "In trans_func.\n" );  
   throw SE_Exception( u );  
}  
  
int main() {  
   _set_se_translator( trans_func );  
    try {  
      SEFunc();  
    }  
    catch( SE_Exception e ) {  
      printf_s( "Caught a __try exception with SE_Exception.\n" );  
      printf_s( "nSE = 0x%x\n", e.getSeNumber() );  
    }  
}  
```  
  
```Output  
In trans_func.  
In finally  
Caught a __try exception with SE_Exception.  
nSE = 0xc0000094  
```  
  
## <a name="see-also"></a>Viz také  
 [Kombinování C (strukturované) a výjimky jazyka C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)