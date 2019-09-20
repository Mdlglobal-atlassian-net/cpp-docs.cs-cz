---
title: Ošetření strukturovaných výjimek v C++
description: Postup zpracování strukturovaných výjimek pomocí modelu C++ zpracování výjimek.
ms.date: 09/19/2019
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
ms.openlocfilehash: 0c0e458f576325034d77676d247020adedfa33e5
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158732"
---
# <a name="handle-structured-exceptions-in-c"></a>Ošetření strukturovaných výjimek v C++

Hlavním rozdílem mezi zpracováním strukturované výjimky jazyka C (SEH C++ ) a zpracováním výjimek C++ je, že model zpracování výjimek se zabývá typy, zatímco model zpracování strukturované výjimky jazyka c pracuje s výjimkami jednoho typu. konkrétně **unsigned int**. Výjimky jazyka C jsou označeny hodnotou unsigned integer, na rozdíl od výjimek jazyka C++, které jsou určeny typem dat. Pokud je v jazyce C vyvolána strukturovaná výjimka, každá z možných obslužných rutin spustí filtr, který prověřuje kontext výjimky jazyka C a určí, zda má být výjimka akceptovat, předejte ji do nějaké jiné obslužné rutiny nebo ji ignorujte. Jakmile je vyvolána výjimka v jazyce C++, může být libovolného typu.

Druhým rozdílem je, že model zpracování strukturované výjimky jazyka C je označován jako *asynchronní*, protože výjimky se vyskytují jako sekundární v normálním toku řízení. Mechanismus C++ zpracování výjimek je plně *synchronní*, což znamená, že výjimky nastávají pouze v případě, že jsou vyvolány.

Při použití možnosti kompilátoru [/EHS nebo/EHsc](../build/reference/eh-exception-handling-model.md) žádné C++ obslužné rutiny výjimek zpracovávají strukturované výjimky. Tyto výjimky jsou zpracovávány pouze obslužnými rutinami strukturované výjimky **__except** nebo obslužnými rutinami **__finally** strukturovaného ukončení. Informace naleznete v tématu [strukturované zpracování výjimek (C/C++)](structured-exception-handling-c-cpp.md).

V rámci možnosti kompilátoru [/EHa](../build/reference/eh-exception-handling-model.md) , pokud je v C++ programu vyvolána výjimka jazyka C, může být zpracována strukturovaným obslužnou rutinou výjimky s přidruženým filtrem nebo obslužnou C++ rutinou **catch** , která je dynamicky blízko k výjimce. souvislost. Například tento ukázkový C++ program vyvolá výjimku jazyka C v C++ rámci kontextu **Try** :

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>Příklad – zachycení výjimky jazyka C v bloku C++ catch

```cpp
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

## <a name="c-exception-wrapper-classes"></a>Obálkové třídy výjimky jazyka C

V jednoduchém příkladu, jak je uvedeno výše, může být výjimka jazyka C zachycena pouze třemi tečkami ( **...** ) Obslužná rutina **catch** Obslužné rutině není dodána žádná informace o typu nebo povaze výjimky. I když tato metoda funguje, v některých případech můžete chtít definovat transformaci mezi dvěma modely zpracování výjimek, aby každá výjimka jazyka C byla přidružena k určité třídě. Chcete-li ji transformovat, můžete definovat třídu "Obálka" jazyka C, která může být použita nebo odvozena z, aby bylo možné vytvořit atribut konkrétní třídy typu výjimka jazyka C. Díky tomu je možné každou výjimku jazyka C zpracovat samostatně pomocí konkrétní C++ obslužné rutiny **catch** namísto všech z nich v rámci jedné obslužné rutiny.

Třída zabalení může obsahovat rozhraní skládající se z některých členských funkcí, které určují hodnotu výjimky a které přistupují k rozšířeným kontextovým informacím poskytnutým modelem zpracování výjimek jazyka C. Můžete také definovat výchozí konstruktor a konstruktor, který přijímá celočíselný argument **bez znaménka** (k poskytnutí podkladové reprezentace výjimky jazyka C) a konstruktor bitové kopie. Tady je možná implementace třídy obálky výjimky jazyka C:

```cpp
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

Chcete-li použít tuto třídu, nainstalujte vlastní funkci překladu výjimek jazyka C, která je volána mechanismem pro zpracování vnitřních výjimek pokaždé, když je vyvolána výjimka jazyka C. V rámci funkce překladu můžete vyvolat jakoukoli `SE_Exception` typovou výjimku (možná typ nebo typ třídy odvozený z `SE_Exception`), která může být zachycena příslušnou odpovídající C++ obslužnou rutinou **catch** . Funkce překladu může místo toho vracet, což znamená, že výjimka nebyla zpracována. Pokud funkce překladu sám vyvolá výjimku jazyka C, je volána funkce [ukončit](../c-runtime-library/reference/terminate-crt.md) .

Chcete-li zadat vlastní funkci překladu, zavolejte funkci [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) s názvem vaší funkce překladu jako jeho jediný argument. Funkce překladu, kterou napíšete, je volána jednou pro každé vyvolání funkce v zásobníku, který obsahuje bloky **Try** . Neexistuje žádná výchozí funkce překladu; Pokud nezadáte žádné voláním **_set_se_translator**, výjimka jazyka C může být zachycena pouze obslužnou rutinou **catch** pro tři tečky.

## <a name="example---use-a-custom-translation-function"></a>Příklad: použití vlastní funkce překladu

Následující kód například nainstaluje vlastní funkci překladu a poté vyvolá výjimku jazyka C, která je zabalena do třídy `SE_Exception`:

```cpp
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

## <a name="see-also"></a>Viz také:

[Kombinování (strukturovaných) C++ a výjimek](../cpp/mixing-c-structured-and-cpp-exceptions.md)
