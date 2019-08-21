---
title: Chyba kompilátoru C2065
ms.date: 08/19/2019
f1_keywords:
- C2065
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
ms.openlocfilehash: 40d1d0744588c4b7911e84f5e57a6b40372b48cf
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630138"
---
# <a name="compiler-error-c2065"></a>Chyba kompilátoru C2065

> '*Identifier*': nedeklarovaný identifikátor

Kompilátor nemůže najít deklaraci pro identifikátor. Tato chyba má mnoho možných příčin. Nejběžnějšími příčinami C2065 jsou, že identifikátor nebyl deklarován, identifikátor je nesprávně napsaný, hlavička, kde je identifikátor deklarován, není součástí souboru nebo identifikátor postrádá kvalifikátor oboru, `cout` například místo `std::cout`. Další informace o deklaracích v C++naleznete v tématu [deklarace a definiceC++()](../../cpp/declarations-and-definitions-cpp.md).

Tady jsou některé běžné problémy a řešení podrobněji.

## <a name="the-identifier-is-undeclared"></a>Identifikátor je nedeklarovaný.

Pokud je identifikátor proměnnou nebo názvem funkce, je nutné ji deklarovat předtím, než bude možné ji použít. Deklarace funkce musí také obsahovat typy parametrů, aby bylo možné funkci použít. Pokud je proměnná deklarována pomocí `auto`, kompilátor musí být schopný odvodit typ z jeho inicializátoru.

Pokud je identifikátor členem třídy nebo struktury nebo deklarován v oboru názvů, musí být kvalifikován názvem třídy nebo struktury nebo názvem oboru názvů, pokud je použit mimo strukturu, třídu nebo obor názvů. Případně je nutné obor názvů převést do oboru `using` podle direktivy `using namespace std;`, jako je, nebo musí být název člena `using` přenesen do rozsahu podle deklarace, jako `using std::string;`je například. V opačném případě je Nekvalifikovaný název považován za nedeklarovaný identifikátor v aktuálním oboru.

Pokud je identifikátor značka pro uživatelsky definovaný typ, například `class` nebo `struct`, typ značky musí být deklarován předtím, než bude možné ji použít. Například deklarace `struct SomeStruct { /*...*/ };` musí existovat, aby bylo možné deklarovat proměnnou `SomeStruct myStruct;` ve vašem kódu.

Pokud je identifikátor alias typu, musí být typ deklarován pomocí `using` deklarace nebo `typedef` předtím, než může být použit. Například musíte deklarovat `using my_flags = std::ios_base::fmtflags;` předtím, než můžete použít `my_flags` jako alias typu pro `std::ios_base::fmtflags`.

## <a name="example-misspelled-identifier"></a>Příklad: nesprávně napsaný identifikátor

K této chybě obvykle dochází, pokud je název identifikátoru špatně napsaný nebo identifikátor používá nesprávná velká a malá písmena. Název v deklaraci musí přesně odpovídat názvu, který používáte.

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

## <a name="example-use-an-unscoped-identifier"></a>Příklad: použití nevymezeného identifikátoru

K této chybě může dojít, pokud váš identifikátor není správně vymezen. Pokud se při použití `cout`zobrazí C2065, jedná se o příčinu. Když C++ standardní funkce knihovny a operátory nejsou plně kvalifikované oborem názvů nebo `std` jste obor názvů nedostali do aktuálního `using` rozsahu pomocí direktivy, kompilátor je nemůže najít. Chcete-li tento problém vyřešit, je nutné buď plně kvalifikovat názvy identifikátorů, nebo zadat obor názvů `using` s direktivou.

Nepodařilo se zkompilovat tento příklad, `cout` protože `endl` a jsou definovány v `std` oboru názvů:

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

Identifikátory, které jsou deklarovány `class`uvnitř `struct`typu, `enum class` nebo musí být také kvalifikovány názvem jejich ohraničujícího oboru, pokud je použijete mimo daný rozsah.

## <a name="example-precompiled-header-isnt-first"></a>Příklad: Předkompilovaná hlavička není první

K této chybě může dojít, pokud před #include souboru předkompilované hlavičky umístíte jakékoli direktivy preprocesoru, například #include, #define nebo #pragma. Pokud zdrojový soubor používá soubor předkompilované hlavičky (to znamená, pokud je zkompilován pomocí možnosti kompilátoru **/Yu** ), pak všechny direktivy preprocesoru před hlavičkovým souborem hlaviček budou ignorovány.

Kompilace tohoto příkladu se nezdařila `endl` , protože `cout` a jsou \<definovány v hlavičce > iostream –, která je ignorována, protože je součástí souboru předkompilované hlavičky. Chcete-li vytvořit tento příklad, vytvořte všechny tři soubory, potom zkompilujte stdafx. cpp a potom zkompilujte C2065_pch. cpp.

```cpp
// pch.h (stdafx.h in Visual Studio 2017 and earlier)
#include <stdio.h>
```

```cpp
// pch.cpp (stdafx.cpp in Visual Studio 2017 and earlier)
// Compile by using: cl /EHsc /W4 /c /Ycstdafx.h stdafx.cpp
#include "pch.h"
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

Chcete-li tento problém vyřešit, přidejte #include \<> iostream – do souboru předkompilované hlavičky nebo ho přesuňte po zahrnutí souboru předkompilované hlavičky do zdrojového souboru.

## <a name="example-missing-header-file"></a>Příklad: chybějící hlavičkový soubor

Nezahrnuli jste hlavičkový soubor, který deklaruje identifikátor. Ujistěte se, že soubor, který obsahuje deklaraci pro identifikátor, je zahrnutý do každého zdrojového souboru, který ho používá.

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

Další možnou příčinou je, pokud použijete seznam inicializátorů bez \<zahrnutí hlavičky initializer_list >.

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

Tato chyba se může zobrazit ve zdrojových souborech aplikace klasické pracovní plochy, pokud `VC_EXTRALEAN`definujete, `WIN32_EXTRA_LEAN` `WIN32_LEAN_AND_MEAN`nebo. Tato makra preprocesoru vyloučí některé hlavičkové soubory z Windows. h a\_afxv W32. h k urychlení kompilací. Vyhledejte v systému Windows. h a afxv_w32. h aktuální popis toho, co se vyloučilo.

## <a name="example-missing-closing-quote"></a>Příklad: chybějící koncová uvozovka

K této chybě může dojít, pokud po řetězcové konstantě chybí uzavírací uvozovky. Toto je jednoduchý způsob, jak Zaměňujte kompilátor. Všimněte si, že chybějící uzavírací uvozovky mohou být před nahlášeným umístěním chyby několik řádků.

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

## <a name="example-use-iterator-outside-for-loop-scope"></a>Příklad: použití iterátoru vně pro rozsah smyčky

K této chybě může dojít, pokud deklarujete proměnnou iterátoru `for` ve smyčce a potom se pokusíte použít tuto proměnnou iterátoru mimo rozsah `for` smyčky. Kompilátor ve výchozím nastavení povolí možnost kompilátoru [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) . Další informace najdete v tématu [Podpora ladění iterátoru](../../standard-library/debug-iterator-support.md) .

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

## <a name="example-preprocessor-removed-declaration"></a>Příklad: odebraná deklarace preprocesoru

K této chybě může dojít, pokud odkazujete na funkci nebo proměnnou, která je v podmíněně kompilovaném kódu, který není zkompilován pro vaši aktuální konfiguraci. K tomu může dojít také v případě, že zavoláte funkci v hlavičkovém souboru, který aktuálně není ve vašem prostředí sestavení podporován. Pokud jsou některé proměnné nebo funkce k dispozici pouze v případě, že je definováno konkrétní preprocesorové makro, ujistěte se, že kód, který volá tyto funkce, lze zkompilovat pouze v případě, že je definováno stejné preprocesorové makro. Tento problém se snadno zaznamená v integrovaném vývojovém prostředí (IDE), protože deklarace funkce je šedá, pokud nejsou pro aktuální konfiguraci sestavení definovány požadovaná makra preprocesoru.

Toto je příklad kódu, který funguje při sestavení v ladění, ale ne v maloobchodě:

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

## <a name="example-ccli-type-deduction-failure"></a>Příklad: C++Odvození chyby typu/CLI

K této chybě může dojít při volání obecné funkce, pokud zamýšlený argument typu nelze odvodit z použitých parametrů. Další informace najdete v tématu [Obecné funkce (C++/CLI)](../../extensions/generic-functions-cpp-cli.md).

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

## <a name="example-ccli-attribute-parameters"></a>Příklad: C++/CLI – parametry atributu

Tato chyba se může vygenerovat taky v důsledku práce s shodami s kompilátorem, která se dokončila pro Visual Studio 2005: Kontrola C++ parametrů pro vizuální atributy.

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
