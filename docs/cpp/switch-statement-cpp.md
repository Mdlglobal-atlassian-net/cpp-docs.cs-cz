---
title: switch – příkaz (C++)
ms.date: 05/06/2019
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 6b09c0eac939f7ca6a12b68ce5deb3fb83ad27c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160811"
---
# <a name="switch-statement-c"></a>switch – příkaz (C++)

Umožňuje výběr mezi více oddíly kódu v závislosti na hodnotě integrálního výrazu.

## <a name="syntax"></a>Syntaxe

```
   switch ( init; expression )
   case constant-expression : statement
   [default  : statement]
```

## <a name="remarks"></a>Poznámky

*Výraz* musí být integrálního typu nebo typu třídy, pro který existuje jednoznačná konverze na celočíselný typ. Celočíselné povýšení se provádí jak je popsáno v tématu [standardní převody](standard-conversions.md).

Tělo příkazu **Switch** se skládá z řady popisků **case** a volitelného **výchozího** popisku. Žádné dva konstantní výrazy v příkazech **case** nelze vyhodnotit na stejnou hodnotu. **Výchozí** popisek se může objevit jenom jednou. Příkazy s popiskem neobsahují syntaktické požadavky, ale příkaz **Switch** nemá žádný význam.   Výchozí příkaz nemusí být na konci. může se objevit kdekoli v těle příkazu switch. Návěstí Case nebo Default se může vyskytovat jenom uvnitř příkazu switch.

*Konstantní výraz* v každém popisku **případu** je převeden na typ *výrazu* a v porovnání s *výrazem* pro rovnost. Řízení se předá příkazu, jehož *konstantní výraz* **case** odpovídá hodnotě *výrazu*. Výsledné chování je uvedeno v následující tabulce.

### <a name="switch-statement-behavior"></a>Chování příkazu switch

|Podmínka|Akce|
|---------------|------------|
|Převedená hodnota odpovídá povýšení řídicího výrazu zvýšené úrovně.|Ovládací prvek bude převeden na příkaz následující po tomto popisku.|
|Žádná Konstanta neodpovídá konstantám v označeních **case** ; je k dispozici **výchozí** popisek.|Ovládací prvek se přenese na **výchozí** popisek.|
|Žádná Konstanta neodpovídá konstantám v označeních **case** ; **výchozí** popisek není k dispozici.|Ovládací prvek se přenese do příkazu za příkazem **Switch** .|

Pokud je nalezen shodný výraz, ovládací prvek není překážkou pro další **případ** nebo **výchozí** popisky. Příkaz [Break](../cpp/break-statement-cpp.md) se používá k zastavení provádění a přenosu řízení příkazu po příkazu **Switch** . Bez příkazu **Break** se spustí každý příkaz z popisku odpovídajícího **případu** na konec **přepínače**, včetně **výchozího**. Příklad:

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   char *buffer = "Any character stream";
   int capa, lettera, nota;
   char c;
   capa = lettera = nota = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            capa++;
            break;
         case 'a':
            lettera++;
            break;
         default:
            nota++;
      }
   }
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",
      capa, lettera, (capa + lettera + nota) );
}
```

V příkladu výše se `capa` zvýší, pokud `c` je `A`velkých písmen. Příkaz **Break** po `capa++` ukončí provádění těla příkazu **přepínače** a ovládací prvek projde smyčkou **while** . Bez příkazu **Break** by spuštění vedlo k dalšímu popisku příkazu, takže by se také mělo zvýšit `lettera` a `nota`. Podobný účel je obsluhován příkazem **Break** pro `case 'a'`. Pokud `c` je `a`s malým písmenem, `lettera` se zvyšuje a příkaz **Break** ukončí tělo příkazu **Switch** . Pokud `c` není `a` nebo `A`, je proveden **výchozí** příkaz.

**Visual Studio 2017 a novější:** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)) atribut `[[fallthrough]]` je zadán v standardu c++ 17. Dá se použít v příkazu **Switch** jako pomocný parametr kompilátoru (nebo pro kohokoli, kdo čte kód), který je určen pro chování při průchodu. Kompilátor společnosti C++ Microsoft aktuálně neupozorňuje na chování fallthrough, takže tento atribut nemá žádný vliv na chování kompilátoru. Všimněte si, že atribut je použit pro prázdný příkaz v rámci příkazu s popiskem; Jinými slovy je středník nutný.

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

**Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): příkaz switch může zavést a inicializovat proměnnou, jejíž obor je omezen na blok příkazu switch:

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

Vnitřní blok příkazu **Switch** může obsahovat definice s inicializací, pokud jsou dosažitelné – to znamená, že neskočí všechny možné cesty provádění. Názvy zavedené pomocí těchto deklarací mají místní rozsah. Příklad:

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

Příkaz **Switch** může být vnořený. V takových případech jsou popisky **case** nebo **Default** přidruženy k nejbližšímu příkazu **Switch** , který je obklopuje.

**Specifické pro společnost Microsoft**

Jazyk Microsoft C neomezuje počet hodnot Case v příkazu **Switch** . Počet je omezen pouze dostupnou pamětí. ANSI C vyžaduje, aby byly v příkazu **Switch** povoleny aspoň 257 popisky případů.

Výchozí hodnota pro Microsoft C znamená, že jsou rozšíření společnosti Microsoft povolena. Tato rozšíření zakažte pomocí možnosti kompilátoru [/za](../build/reference/za-ze-disable-language-extensions.md) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Příkazy výběru](../cpp/selection-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
