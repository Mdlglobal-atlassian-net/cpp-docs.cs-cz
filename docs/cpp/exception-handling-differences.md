---
title: Zpracování strukturovaných výjimek v jazyce C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48acd13aced14bfd8acbeb4c306a5749010636d7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086032"
---
# <a name="handle-structured-exceptions-in-c"></a>Zpracování strukturovaných výjimek v jazyce C++

Hlavní rozdíl mezi C strukturované výjimky (SEH) zpracování a zpracování výjimek jazyka C++ je, že model zabývá typy zpracování výjimek jazyka C++, při C model zpracování strukturovaných výjimek se zabývá výjimkami jednoho typu; Konkrétně **unsigned int**. Výjimky jazyka C jsou označeny hodnotou unsigned integer, na rozdíl od výjimek jazyka C++, které jsou určeny typem dat. Při vyvolání strukturovaných výjimek v jazyce C, vykoná každý popisovač filtr, který prověří kontext výjimek jazyka C a určí, zda výjimku přijmout, předat ji jiné obslužné rutině nebo ji ignorovat. Jakmile je vyvolána výjimka v jazyce C++, může být libovolného typu.

Druhý rozdíl je, že model zpracování strukturovaných výjimek jazyka C se označuje jako *asynchronní*, protože výskytu výjimek vzhledem k normálnímu toku řízení. Mechanismus zpracování výjimek jazyka C++ je plně *synchronní*, což znamená, že výjimkám dochází pouze při jejich vyvolání.

Při použití [/EHS nebo/EHsc](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru, žádné výjimky popisovač strukturované obslužné rutiny výjimky C++. Tyto výjimky jsou zpracovávány pouze **__catch** strukturované obslužné rutiny výjimek nebo **__finally** strukturované obslužné rutiny ukončení. Informace najdete v tématu [strukturovaného zpracování výjimek (C/C++)](structured-exception-handling-c-cpp.md).

V části [/EHa](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru, pokud v programu v jazyce C++ je vyvolána výjimka jazyka C, může být zpracována strukturovanou obslužnou rutinou s přidruženým filtrem nebo pomocí jazyka C++ **catch** obslužnou rutinu, podle toho, co je dynamicky blíže vzhledem ke kontextu výjimky. Například následující program jazyka C++ vyvolá výjimku jazyka C do C++ **zkuste** kontextu:

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>Příklad – Catch blok catch výjimky jazyka C v C++

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

V jednoduchém příkladu je uveden výše, výjimka jazyka C může být zachycena pouze třemi tečkami (**...** ) **catch** obslužné rutiny. Obslužné rutině není dodána žádná informace o typu nebo povaze výjimky. Zatímco tato metoda funguje, v některých případech můžete chtít definovat transformaci mezi dvěma modely zpracování výjimek tak, aby jednotlivé výjimky jazyka C spojeny s konkrétní třídou. To lze provést definováním třídy „zabalení“ výjimky jazyka C, kterou lze použít nebo odvodit pro vytvoření atributu pro určitý typ třídy na výjimku jazyka C. Díky tomu jednotlivé výjimky jazyka C mohou být zpracovány samostatně konkrétní C++ **catch** obslužnou rutinu, ne všechny z nich v jedna obslužná rutina.

Třída zabalení může obsahovat rozhraní skládající se z některých členských funkcí, které určují hodnotu výjimky a které přistupují k rozšířeným kontextovým informacím poskytnutým modelem zpracování výjimek jazyka C. Můžete také definovat výchozí konstruktor a konstruktor, který přijímá **unsigned int** argument (pro poskytnutí základní reprezentace výjimka jazyka C) a konstruktor bitové kopie. Tady je možná implementace třída zabalení výjimky jazyka C:

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

Pokud chcete použít tuto třídu, nainstalujte vlastní funkci překladu výjimek jazyka C, která je volána mechanismem pokaždé, když je vyvolána výjimka jazyka C zpracování interních výjimek. V rámci funkce překladu lze vyvolat jakoukoli typovou výjimku (například `SE_Exception` typ nebo typ třídy odvozený z `SE_Exception`), které lze zachytit příslušné odpovídající C++ **catch** obslužné rutiny. Funkce překladu může jednoduše provést vrácení, což znamená, že nedošlo ke zpracování výjimky. Je-li samotná funkce překladu vyvolává výjimku jazyka C, [ukončit](../c-runtime-library/reference/terminate-crt.md) je volána.

Chcete-li zadat vlastní funkci překladu, zavolejte [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) funkci s názvem funkce překladu jako její jediný argument. Vytvořená funkce překladu při psaní se volá jednou pro každé vyvolání funkce v zásobníku, který má **zkuste** bloky. Neexistuje žádná výchozí funkce překladu; Pokud nezadáte voláním **_set_se_translator**, může být výjimka jazyka C zachycena pouze pomocí tři teček **catch** obslužné rutiny.

## <a name="example---use-a-custom-translation-function"></a>Příklad – použití vlastní funkci překladu

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

[Kombinace jazyka C (strukturované) a výjimky jazyka C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)
