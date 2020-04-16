---
title: switchpříkaz (C++)
description: Odkaz na standardní příkaz switch C++ v aplikaci Microsoft Visual Studio C++.
ms.date: 04/15/2020
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
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 1f65d4699423d74be9c75a9be47e543a9a1256e2
ms.sourcegitcommit: 9266fc76ac2e872e35a208b4249660dfdfc87cba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81480825"
---
# <a name="opno-locswitch-statement-c"></a>switchpříkaz (C++)

Umožňuje výběr mezi více oddíly kódu, v závislosti na hodnotě integrálního výrazu.

## <a name="syntax"></a>Syntaxe

> **`switch (`**\[ *inicializace* **`;`**] *výraz***`)`**\
> **`{`**\
> &nbsp;&nbsp;&nbsp;&nbsp;**`case`***příkaz* *s konstantním výrazem* **`:`**\
> &nbsp;&nbsp;&nbsp;&nbsp;\[**`default :`***prohlášení*] \
> **`}`**

## <a name="remarks"></a>Poznámky

*Výraz* musí mít integrální typ nebo být typ třídy, který má jednoznačný převod na integrální typ. Integrální propagace probíhá tak, jak je popsáno ve [standardních konverzích](standard-conversions.md).

Tělo **switch** příkazu se skládá **case** z řady **default** popisků a volitelného popisku. Souhrnně příkazy, které následují popisky se nazývají *označené příkazy.* Označené příkazy nejsou syntaktické požadavky, **switch** ale prohlášení je bez nich bezvýznamné. Žádné dva konstantní **case** výrazy v příkazech může vyhodnotit na stejnou hodnotu. Popisek **default** se může zobrazit pouze jednou. Příkaz **default** je často umístěn na konci, ale může se **switch** objevit kdekoli v textu příkazu. **case** Popisek **default** nebo se může **switch** zobrazit pouze uvnitř příkazu.

*Konstantní výraz* v **case** každém popisku je převeden na typ *výrazu*. Pak je porovnán s *výrazem* pro rovnost. Ovládací prvek předá **case** příkazu, jehož *konstantní výraz* odpovídá hodnotě *výrazu*. Výsledné chování je uvedeno v následující tabulce.

### <a name="switch-statement-behavior"></a>Přepnout chování příkazu

| Podmínka | Akce |
|--|--|
| Převedená hodnota odpovídá hodnotě propagovaného řídícího výrazu. | Ovládací prvek je převeden do příkazu následujícího za tímto popiskem. |
| Žádná z konstant neodpovídá konstantám **case** v popiscích; štítek **default** je přítomen. | Ovládací prvek je **default** převeden na popisek. |
| Žádná z konstant neodpovídá konstantám **case** v popiscích; není **default** k dispozici žádný štítek. | Ovládací prvek je převedena **switch** do příkazu po příkazu. |

Pokud je nalezen odpovídající výraz, spuštění **case** **default** může pokračovat později nebo popisky. Příkaz [`break`](../cpp/break-statement-cpp.md) se používá k zastavení provádění a předání **switch** řízení do příkazu po příkazu. Bez **break** příkazu je proveden každý **case** příkaz z odpovídajícího popisku na konec **switch**, včetně **default**, . Příklad:

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

Ve výše uvedeném příkladu se zintáží, `uppercase_A` pokud `c` je velká písmena `'A'`. Příkaz **break** po `uppercase_A++` ukončení provádění **switch** těla příkazu a **while** ovládací prvek předá smyčky. Bez **break** příkazu by exekuce "propadla" do `lowercase_a` dalšího `other` označeného prohlášení, takže by se také zintáčela. Podobnému účelu slouží **break** prohlášení `case 'a'`pro společnost . Pokud `c` je malá `'a'` `lowercase_a` písmena , je **break** přírůstek **switch** a příkaz ukončí tělo příkazu. Pokud `c` není `'a'` nebo `'A'`, **default** příkaz je proveden.

**Visual Studio 2017 a novější:** (k dispozici s [/std:c++17)](../build/reference/std-specify-language-standard-version.md)Atribut `[[fallthrough]]` je určen ve standardu C++17. Můžete jej použít **switch** v příkazu. Je to nápověda k kompilátoru, nebo kdokoli, kdo čte kód, že fall-through chování je úmyslné. Kompilátor Microsoft C++ aktuálně nevaruje na fallthrough chování, takže tento atribut nemá žádný vliv na chování kompilátoru. V příkladu atribut získá použít na prázdný příkaz v rámci neukončený labeled prohlášení. Jinými slovy, středník je nezbytné.

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

**Visual Studio 2017 verze 15.3 a novější** (k dispozici s [/std:c++17](../build/reference/std-specify-language-standard-version.md)). Příkaz switch může mít *klauzuli inicializace.* Zavádí a inicializuje proměnnou, jejíž rozsah je switch omezen na blok příkazu:

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

Vnitřní blok příkazu **switch** může obsahovat definice s inicializacetak dlouho, dokud jsou *dosažitelné*, to znamená, že není obejít všechny možné cesty spuštění. Názvy zavedené pomocí těchto deklarací mají místní obor. Příklad:

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

Příkaz **switch** může být vnořený. Při vnoření **case** **default** se popisky **switch** nebo přidruží k nejbližšímu příkazu, který je obklopuje.

### <a name="microsoft-specific-behavior"></a>Chování specifické pro společnost Microsoft

Microsoft C neomezuje počet **case** hodnot v **switch** příkazu. Počet je omezen pouze dostupnou pamětí. ANSI C vyžaduje, aby **case** v příkazu **switch** bylo povoleno alespoň 257 štítků.

Pro default Microsoft C je, že rozšíření společnosti Microsoft jsou povoleny. Pomocí možnosti kompilátoru [/Za](../build/reference/za-ze-disable-language-extensions.md) zakažte tato rozšíření.

## <a name="see-also"></a>Viz také

[Příkazy výběru](../cpp/selection-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
