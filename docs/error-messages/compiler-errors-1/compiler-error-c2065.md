---
title: Chyba kompilátoru C2065
ms.date: 09/01/2017
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: ae7f582de5d6c45df34c42164756356a9c794d31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482511"
---
# <a name="compiler-error-c2065"></a>Chyba kompilátoru C2065

> "*identifikátor*': nedeklarovaný identifikátor

Kompilátor nemůže najít deklarace identifikátoru. Existuje mnoho možných příčin této chyby. Nejběžnější příčiny C2065 se, že nebyla deklarována identifikátor, identifikátor je zadáno chybně, záhlaví, ve kterém je deklarována identifikátor není zahrnut do souboru nebo chybí identifikátor obor kvalifikátoru, například `cout` místo `std::cout`. Další informace o deklarace v C++, naleznete v tématu [deklarace a definice (C++)](../../cpp/declarations-and-definitions-cpp.md).

Tady jsou některé běžné problémy a řešení podrobněji.

## <a name="the-identifier-is-undeclared"></a>Nedeklarovaný identifikátor

Pokud se identifikátor proměnnou nebo název funkce, musíte ji deklarovat před jeho použitím. Deklarace funkce musí obsahovat také typy jeho parametrů před použitím funkce. Pokud je proměnná deklarována pomocí `auto`, kompilátor musí mít k odvození typu z jeho vlastním inicializátoru.

Pokud identifikátor je členem třídy nebo struktury nebo deklarované v oboru názvů, musí být určeny podle názvu třídy nebo struktury, nebo název oboru názvů, když se používá mimo obor struktury, třídy nebo oboru názvů. Alternativně obor názvů musí být přeneseny do rozsahu pomocí `using` direktivy, jako `using namespace std;`, nebo název člena musí být přeneseny do rozsahu pomocí `using` deklarace, jako `using std::string;`. V opačném případě neúplný název se považuje za nedeklarovaný identifikátor v aktuálním oboru.

Pokud se identifikátor značky pro uživatelem definovaný typ, například `class` nebo `struct`, typ značky musí být deklarován, před jeho použitím. Například, deklarace `struct SomeStruct { /*...*/ };` musí existovat předtím, než je možné deklarovat proměnnou `SomeStruct myStruct;` ve vašem kódu.

Pokud se identifikátor alias typu, typ musí být deklarovány s použitím `using` prohlášení nebo `typedef` předtím, než je možné. Například musíte deklarovat `using my_flags = std::ios_base::fmtflags;` před použitím `my_flags` jako alias typu pro `std::ios_base::fmtflags`.

## <a name="example-misspelled-identifier"></a>Příklad: chybně identifikátor

K této chybě dochází běžně, když název identifikátoru je zadáno chybně nebo identifikátor používá nesprávný malá a velká písmena. Název v deklaraci musí přesně odpovídat názvu, který používáte.

```cpp
// C2065_spell.cpp
// compile with: cl /EHsc C2065_spell.cpp
#include <iostream>
using namespace std;
int main() {
    int someIdentifier = 42;
    cout << "Some Identifier: " << SomeIdentifier << endl;
    // C2065: 'SomeIdentifier': undeclared identifier
    // To fix, correct the spelling:
    // cout << "Some Identifier: " << someIdentifier << endl;
}
```

## <a name="example-use-an-unscoped-identifier"></a>Příklad: použití bez ohledu na obor identifikátor

K této chybě může dojít, pokud vaše identifikátor není v oboru správně. Pokud se zobrazí při použití C2065 `cout`, je to příčina. Když funkce standardní knihovny C++ a operátory nejsou plně kvalifikován pomocí oboru názvů, nebo nebyly režimu `std` oboru názvů v aktuálním oboru s použitím `using` direktiv, kompilátor nemůže najít je. Chcete-li vyřešit tento problém, musíte buď plně kvalifikovat názvy identifikátorů, nebo zadejte obor názvů se `using` směrnice.

V tomto příkladu se nepodaří zkompilovat, protože `cout` a `endl` jsou definovány v `std` obor názvů:

```cpp
// C2065_scope.cpp
// compile with: cl /EHsc C2065_scope.cpp
#include <iostream>
// using namespace std;   // Uncomment this line to fix

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead
    std::cout << "Hello" << std::endl;
}
```

Identifikátory, které jsou deklarované uvnitř `class`, `struct`, nebo `enum class` typy musí být kvalifikovaný podle názvu jejich nadřazených rámců také. při použití mimo tento rozsah.

## <a name="example-precompiled-header-isnt-first"></a>Příklad: není první předkompilované hlavičky

K této chybě může dojít, pokud například umístit všechny direktivy preprocesoru, #include, #define, nebo #pragma, než #include souboru předkompilované hlavičky. Pokud zdrojový soubor používá soubor předkompilované hlavičky (tj. Pokud je zkompilován s použitím **/Yu** – možnost kompilátoru) pak budou ignorovány všechny direktivy preprocesoru před předkompilovaného souboru hlaviček.

V tomto příkladu se nepodaří zkompilovat, protože `cout` a `endl` jsou definovány v \<iostream – > hlavičky, která se ignoruje, protože je zahrnutý před předkompilovaného souboru hlaviček. Sestavení tohoto příkladu, vytvořit všechny tři soubory, poté zkompilovat stdafx.cpp a kompilaci C2065_pch.cpp.

```cpp
// stdafx.h
#include <stdio.h>
```

```cpp
// stdafx.cpp
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include <stdafx.h>
```

```cpp
// C2065_pch.cpp
// compile with: cl /EHsc /W4 /Yustdafx.h C2065_pch.cpp
#include <iostream>
#include "stdafx.h"
using namespace std;

int main() {
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier
                               // C2065 'endl': undeclared identifier
}
```

Chcete-li tento problém vyřešit, přidejte #include \<iostream – > do souboru předkompilované hlavičky nebo přesunutí souboru předkompilované hlavičky je zahrnutá ve zdrojovém souboru.

## <a name="example-missing-header-file"></a>Příklad: chybí soubor hlaviček

Hlavičkový soubor, který deklaruje identifikátor nebyly zahrnuty. Ujistěte se, že soubor obsahující deklarace pro identifikátor je součástí každý zdrojový soubor, který ji používá.

```cpp
// C2065_header.cpp
// compile with: cl /EHsc C2065_header.cpp

//#include <stdio.h>
int main() {
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined
}
```

Další možnou příčinou je, pokud použijete seznam inicializátorů bez zahrnutí \<initializer_list > záhlaví.

```cpp
// C2065_initializer.cpp
// compile with: cl /EHsc C2065_initializer.cpp

// #include <initializer_list>
int main() {
    for (auto strList : {"hello", "world"})
        if (strList == "hello") // C2065: 'strList': undeclared identifier
            return 1;
    // To fix, uncomment the #include <initializer_list> line
}
```

Pokud definujete, může se zobrazit tato chyba ve zdrojových souborech aplikace Windows Desktop `VC_EXTRALEAN`, `WIN32_LEAN_AND_MEAN`, nebo `WIN32_EXTRA_LEAN`. Tato makra preprocesoru vyloučit některé soubory s hlavičkami z windows.h a afxv\_zkompiluje w32.h rychlost. Hledejte v windows.h a afxv_w32.h aktuální popis co je vyloučený.

## <a name="example-missing-closing-quote"></a>Příklad: chybí koncová uvozovka

K této chybě může dojít, pokud jsou za konstantu řetězce chybí ukončovací uvozovky. Toto je snadný způsob, jak kompilátor zmást. Všimněte si, že chybí uzavírací uvozovky mohou být Víceřádkový před umístění oznámenou chybu.

```cpp
// C2065_quote.cpp
// compile with: cl /EHsc C2065_quote.cpp
#include <iostream>

int main() {
    // Fix this issue by adding the closing quote to "Aaaa"
    char * first = "Aaaa, * last = "Zeee";
    std::cout << "Name: " << first
        << " " << last << std::endl; // C2065: 'last': undeclared identifier
}
```

## <a name="example-use-iterator-outside-for-loop-scope"></a>Příklad: použití iterátoru mimo pro obor cyklu for

K této chybě může dojít, pokud deklarujete proměnnou iterátor v `for` smyčky a pak zkuste použít tato proměnná iterátoru mimo obor `for` smyčky. Umožňuje kompilátoru [/Zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) – možnost kompilátoru ve výchozím nastavení. Zobrazit [Debug Iterator Support](../../standard-library/debug-iterator-support.md) Další informace.

```cpp
// C2065_iter.cpp
// compile with: cl /EHsc C2065_iter.cpp
#include <iostream>
#include <string>

int main() {
    // char last = '!';
    std::string letters{ "ABCDEFGHIJKLMNOPQRSTUVWXYZ" };
    for (const char& c : letters) {
        if ('Q' == c) {
            std::cout << "Found Q!" << std::endl;
        }
        // last = c;
    }
    std::cout << "Last letter was " << c << std::endl; // C2065
    // Fix by using a variable declared in an outer scope.
    // Uncomment the lines that declare and use 'last' for an example.
    // std::cout << "Last letter was " << last << std::endl; // C2065
}
```

## <a name="example-preprocessor-removed-declaration"></a>Příklad: preprocesoru odebrané deklarace

K této chybě může dojít, pokud odkazujete na funkci nebo proměnnou, která je v podmíněně zkompilovaný kód, který se zkompiluje pro vaši aktuální konfiguraci. To může vzniknout také při volání funkce v hlavičkovém souboru, který není aktuálně podporován ve vašem prostředí sestavení. Pokud určité proměnné nebo funkce jsou k dispozici, pouze když je definována konkrétní preprocesorové makro, ujistěte se, že kód, který volá tyto funkce mohou být zkompilovány pouze pokud je definován stejný preprocesor makro. Tento problém je snadné sledovat v integrovaném vývojovém prostředí, protože deklarace funkce zašedlé Pokud požadované makra preprocesoru nejsou definovány pro aktuální konfiguraci sestavení.

Toto je příklad kódu, který funguje v případě sestavení v ladění, ale ne maloobchod:

```cpp
// C2065_defined.cpp
// Compile with: cl /EHsc /W4 /MT C2065_defined.cpp
#include <iostream>
#include <crtdbg.h>
#ifdef _DEBUG
    _CrtMemState oldstate;
#endif
int main() {
    _CrtMemDumpStatistics(&oldstate);
    std::cout << "Total count " << oldstate.lTotalCount; // C2065
    // Fix by guarding references the same way as the declaration:
    // #ifdef _DEBUG
    //    std::cout << "Total count " << oldstate.lTotalCount;
    // #endif
}
```

## <a name="example-ccli-type-deduction-failure"></a>Příklad: C + +/ CLI chyba odvození typu

Této chybě může dojít při volání obecné funkce, pokud argument určený typ nelze odvodit z parametrů použitých. Další informace najdete v tématu [obecné funkce (C + +/ CLI)](../../windows/generic-functions-cpp-cli.md).

```cpp
// C2065_b.cpp
// compile with: cl /clr C2065_b.cpp
generic <typename ItemType>
void G(int i) {}

int main() {
   // global generic function call
   G<T>(10);     // C2065
   G<int>(10);   // OK - fix with a specific type argument
}
```

## <a name="example-ccli-attribute-parameters"></a>Příklad: C + +/ CLI atribut parametry

Tato chyba může být také generovány jako důsledek kompilátoru prací, které bylo provedeno pro Visual C++ 2005: kontroly parametrů pro atributy Visual C++.

```cpp
// C2065_attributes.cpp
// compile with: cl /c /clr C2065_attributes.cpp
[module(DLL, name=MyLibrary)];   // C2065
// try the following line instead
// [module(dll, name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```
