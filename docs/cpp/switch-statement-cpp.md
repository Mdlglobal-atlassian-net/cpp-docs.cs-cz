---
title: switchpříkaz (C++)
description: Odkaz na standardní příkaz jazyka C++ switch v jazyce Microsoft Visual Studio c++.
ms.date: 04/25/2020
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
no-loc:
- switch
- case
- default
- break
- while
- opt
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d43a7a64b5a74f00833093ae8999d73edd7f5753
ms.sourcegitcommit: c4cf8976939dd0e13e25b82930221323ba6f15d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83204165"
---
# <a name="switch-statement-c"></a>`switch`příkaz (C++)

Umožňuje výběr mezi více oddíly kódu v závislosti na hodnotě integrálního výrazu.

## <a name="syntax"></a>Syntaxe

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;__`switch`__&nbsp;__`(`__&nbsp;*`init-statement`*<sub>opt</sub> <sup>C++ 17</sup>&nbsp;*`condition`*&nbsp;__`)`__&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>opt</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>Poznámky

__`switch`__ Příkaz způsobí, že se ovládací prvek převede na jeden *`labeled-statement`* v těle jeho příkazu v závislosti na hodnotě *`condition`* .

*`condition`* Musí mít celočíselný typ nebo být typu třídy, který má dvojznačný převod na celočíselný typ. K integrální povýšení dochází, jak je popsáno v tématu [standardní převody](standard-conversions.md).

__`switch`__ Tělo příkazu se skládá z řady __`case`__ popisků a volitelného __`default`__ popisku. A *`labeled-statement`* je jedním z těchto popisků a příkazů, které následují. Příkazy s popiskem nejsou syntaktické požadavky, ale __`switch`__ příkaz nemá žádný význam. Žádné dvě *`constant-expression`* hodnoty v __`case`__ příkazech nelze vyhodnotit na stejnou hodnotu. __`default`__ Popisek se může objevit jenom jednou. __`default`__ Příkaz je často umístěn na konci, ale může se objevit kdekoli v __`switch`__ těle příkazu. __`case`__ Popisek nebo __`default`__ se může vyskytovat jenom uvnitř __`switch`__ příkazu.

*`constant-expression`* V každém __`case`__ popisku je převedena na konstantní hodnotu, která je stejného typu jako *`condition`* . Pak je porovnán s *`condition`* pro rovnost. Řízení se předá prvnímu příkazu za __`case`__ *`constant-expression`* hodnotou, která odpovídá hodnotě *`condition`* . Výsledné chování je uvedeno v následující tabulce.

### <a name="switch-statement-behavior"></a>`switch`chování příkazu

| Podmínka | Akce |
|--|--|
| Převedená hodnota odpovídá povýšení řídicího výrazu zvýšené úrovně. | Ovládací prvek bude převeden na příkaz následující po tomto popisku. |
| Žádná Konstanta neodpovídá konstantám v popisku __`case`__ ; __`default`__ popisek je k dispozici. | Ovládací prvek se přenese na __`default`__ popisek. |
| Žádná Konstanta neodpovídá konstantám v __`case`__ popisku; __`default`__ není k dispozici žádný popisek. | Ovládací prvek se přenese do příkazu za __`switch`__ příkazem. |

Pokud se najde shodný výraz, může provádění pokračovat prostřednictvím pozdějších __`case`__ nebo __`default`__ popisků. [`break`](../cpp/break-statement-cpp.md)Příkaz slouží k zastavení provádění a přenosu řízení příkazu po __`switch`__ příkazu. Bez __`break`__ příkazu se spustí všechny příkazy z odpovídajícího __`case`__ popisku na konec __`switch`__ , včetně __`default`__ . Příklad:

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int uppercase_A, lowercase_a, other;
   char c;
   uppercase_A = lowercase_a = other = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            uppercase_A++;
            break;
         case 'a':
            lowercase_a++;
            break;
         default:
            other++;
      }
   }
   printf_s( "\nUppercase A: %d\nLowercase a: %d\nTotal: %d\n",
      uppercase_A, lowercase_a, (uppercase_A + lowercase_a + other) );
}
```

Ve výše uvedeném příkladu `uppercase_A` se zvýší, pokud `c` je to velké písmeno `'A'` . __`break`__ Příkaz po `uppercase_A++` ukončení vykonání __`switch`__ těla příkazu a řízení předá do __`while`__ smyčky. Bez __`break`__ příkazu by spuštění vedlo k dalšímu popisku příkazu, takže by `lowercase_a` `other` se také mělo zvýšit. Podobný účel je obsluhován __`break`__ příkazem pro `case 'a'` . Pokud `c` je malá písmena `'a'` , `lowercase_a` je zvýšena a __`break`__ příkaz ukončí __`switch`__ tělo příkazu. Pokud `c` není `'a'` nebo `'A'` , je __`default`__ proveden příkaz.

**Visual Studio 2017 a novější:** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` atribut je zadán v standardu c++ 17. Můžete ho použít v __`switch`__ příkazu. Je to pomocný parametr kompilátoru, nebo kdokoli, kdo čte kód, který je v průběhu tohoto chování záměrné. Kompilátor jazyka Microsoft C++ aktuálně neupozorňuje na chování fallthrough, takže tento atribut nemá žádný vliv na chování kompilátoru. V příkladu je atribut použit pro prázdný příkaz v rámci neukončeného příkazu Label. Jinými slovy je středník nutný.

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

**Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)). __`switch`__ Příkaz může obsahovat *`init-statement`* klauzuli, která končí středníkem. Zavádí a inicializuje proměnnou, jejíž rozsah je omezen na blok __`switch`__ příkazu:

```cpp
    switch (Gadget gadget(args); auto s = gadget.get_status())
    {
    case status::good:
        gadget.zip();
        break;
    case status::bad:
        throw BadGadget();
    };
```

Vnitřní blok __`switch`__ příkazu může obsahovat definice s inicializátory, pokud jsou *dostupné*, to znamená, že neskočí všechny možné cesty provádění. Názvy zavedené pomocí těchto deklarací mají místní rozsah. Příklad:

```cpp
// switch_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    switch( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    case 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        break;

    case 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        break;

    default:
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        break;
    }
}
```

__`switch`__ Příkaz může být vnořený. Při vnoření jsou __`case`__ __`default`__ popisky nebo přidruženy k nejbližšímu __`switch`__ příkazu, který je obklopuje.

### <a name="microsoft-specific-behavior"></a>Chování specifické pro společnost Microsoft

Jazyk Microsoft C++ neomezuje počet __`case`__ hodnot v __`switch`__ příkazu. Počet je omezen pouze dostupnou pamětí.

## <a name="see-also"></a>Viz také

[Příkazy výběru](../cpp/selection-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
