---
title: "C2065 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 09/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2065
dev_langs:
- C++
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a20fee308a8ed9d237f8fc76df60964704c9c69d
ms.sourcegitcommit: 1e367a5f5c5a6fd0b6018f4fb5edcdf2f1a8085c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="compiler-error-c2065"></a>Compiler Error C2065

> '*identifikátor*': nedeklarovaný identifikátor

Kompilátor nelze najít deklaraci pro identifikátor. Existuje mnoho možných příčin této chyby. Nejběžnější příčiny C2065 jsou, identifikátor nebyla deklarována, identifikátor je zadáno chybně, záhlaví, kde je deklarovaná identifikátor není součástí souboru nebo chybí identifikátor kvalifikátor oboru, například `cout` místo `std::cout`. Další informace o deklarace v C++ najdete v tématu [deklarace a definice (C++)](../../cpp/declarations-and-definitions-cpp.md).

Tady jsou některé běžné problémy a řešení podrobněji.

## <a name="the-identifier-is-undeclared"></a>Identifikátor, který je nebyla deklarována

Pokud je identifikátor proměnné nebo název funkce, musí deklarovat před použitím. Deklaraci funkce musí také obsahovat typy jeho parametry před použitím funkce. Pokud je proměnná deklarováno s použitím `auto`, kompilátor musí být schopen odvození typu z jeho inicializátor.

Pokud identifikátor je členem třídě nebo struktuře nebo deklarované v oboru názvů, musí být kvalifikovaný názvem třídě nebo struktuře, nebo název oboru názvů, při použití mimo obor struktura, třída nebo obor názvů. Alternativně obor názvů musí být uvedena do obor dle `using` direktivy, jako `using namespace std;`, nebo název člena musí být uvedena do oboru ve `using` deklarace, například `using std::string;`. Neúplný název, jinak se považuje za nedeklarovaný identifikátor v aktuálním oboru.

Pokud je identifikátor značky pro uživatelem definovaný typ, například `class` nebo `struct`, typ značky musí být deklarován před použitím. Například deklaraci `struct SomeStruct { /*...*/ };` musí existovat lze deklarovat proměnnou `SomeStruct myStruct;` v kódu.

Pokud je identifikátor typ alias, typ musí být deklarován pomocí `using` deklarace nebo `typedef` před použitím. Například musíte deklarovat `using my_flags = std::ios_base::fmtflags;` před použitím `my_flags` jako typ aliasu pro `std::ios_base::fmtflags`.

## <a name="example-misspelled-identifier"></a>Příklad: Chybný identifikátor

K této chybě dochází běžně, když je nesprávně uveden název identifikátor nebo identifikátor se používá nesprávný malá a velká písmena. Název v deklaraci musí přesně odpovídat názvu, který používáte.

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

Této chybě může dojít, pokud vaše identifikátor není správně obor. Pokud se zobrazí C2065 při použití `cout`, to je důvod. Když funkce standardní knihovny C++ a operátory nejsou plně kvalifikovaná pomocí oboru názvů, nebo nebyly začlenění `std` oboru názvů do aktuální obor pomocí `using` direktivy, kompilátor nelze najít je. Pokud chcete tento problém vyřešit, musíte buď plně kvalifikovat identifikátor názvy, nebo zadejte obor názvů s `using` – direktiva.

V tomto příkladu se nepovede zkompilovat, protože `cout` a `endl` jsou definovány v `std` obor názvů:

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

Identifikátory, které jsou deklarované uvnitř `class`, `struct`, nebo `enum class` typy musí být kvalifikovaný názvem jejich vymezeném oboru také, při použití mimo tento rozsah.

## <a name="example-precompiled-header-isnt-first"></a>Příklad: není první předkompilovaných hlaviček

Této chybě může dojít, když vložíte preprocesor – direktivy, například #include, #define, nebo #pragma, než #include předkompilovaný hlavičkový soubor. Pokud váš zdrojový soubor používá předkompilovaný hlavičkový soubor (tj. Pokud je kompilován s použitím **/Yu** – možnost kompilátoru) a jsou ignorovány všechny direktivy preprocesoru před předkompilovaný hlavičkový soubor.

V tomto příkladu se nepovede zkompilovat, protože `cout` a `endl` jsou definovány v \<iostream > hlavičky, která se ignoruje, protože je zahrnutá před předkompilovaný hlavičkový soubor. K sestavení v tomto příkladu, vytvořte všechny tři soubory, pak zkompilovat stdafx.cpp pak zkompilovat C2065_pch.cpp.

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

Chcete-li tento problém vyřešit, přidejte #include \<iostream > do předkompilovaný hlavičkový soubor nebo přesunutí po předkompilovaný hlavičkový soubor je součástí zdrojového souboru.

## <a name="example-missing-header-file"></a>Příklad: chybí soubor hlaviček

Nebyly zahrnout soubor hlaviček, který deklaruje identifikátor. Ujistěte se, že soubor, který obsahuje deklaraci pro identifikátor je zahrnuta v každé zdrojový soubor, který se používá.

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

Další možnou příčinou je, pokud použijete inicializačním seznam bez včetně \<initializer_list > záhlaví.

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

Pokud definujete, mohou se zobrazit tato chyba ve zdrojových souborech aplikace Windows Desktop `VC_EXTRALEAN`, `WIN32_LEAN_AND_MEAN`, nebo `WIN32_EXTRA_LEAN`. Tyto makra preprocesoru vyloučit některé soubory hlaviček z odkazující na Windows a afxv\_zkompiluje w32.h pro rychlejší. Vyhledejte v odkazující na Windows a afxv_w32.h aktuální popis co je vyloučen.

## <a name="example-missing-closing-quote"></a>Příklad: chybí ukončovací uvozovky

Této chybě může dojít, pokud jsou za konstantu řetězce chybí ukončovací uvozovky. Toto je snadný způsob, jak matou kompilátoru. Všimněte si, že chybí ukončovací uvozovky může být Víceřádkový před umístění oznámenou chybu. 

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

## <a name="example-use-iterator-outside-for-loop-scope"></a>Příklad: použití iterator mimo pro obor cyklu for

Této chybě může dojít, pokud je deklarovat proměnnou iterator v `for` smyčky a potom zkuste tuto proměnnou iterator použít mimo obor `for` smyčky. Kompilátor umožňuje [/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) – možnost kompilátoru ve výchozím nastavení. V tématu [podpora ladění iterátorů](../../standard-library/debug-iterator-support.md) Další informace.

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

Této chybě může dojít, pokud vyhledáváte funkce nebo proměnná, která je v podmíněně zkompilovaný kód, který není sestaven pro aktuální konfiguraci. Tato situace může také nastat při volání funkce v záhlaví souboru, který není aktuálně podporován ve vašem prostředí sestavení. Pokud určité proměnné nebo funkce jsou k dispozici, pouze pokud je definován konkrétní makro preprocesoru, ujistěte se, že kód, který volá tyto funkce mohou být zkompilovány pouze pokud je definován stejný makro preprocesoru. Tento problém je snadné spot v prostředí IDE, protože je šedé deklaraci pro funkci, pokud nejsou požadované makra preprocesoru definovaný pro aktuální konfiguraci sestavení.

Jedná se o příklad kódu, který funguje, když jste sestavení v ladění, ale není maloobchodní:

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

Této chybě může dojít při volání metody obecné funkce, pokud argument určený typu nelze odvodit z použité parametry. Další informace najdete v tématu [obecné funkce (C + +/ CLI)](../../windows/generic-functions-cpp-cli.md).

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

Tato chyba může být také vygenerovaného jako výsledek kompilátoru shoda práci, kterou bylo provedeno pro Visual C++ 2005: Parametr kontrola atributy Visual C++.

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
