---
title: Argumenty funkce typu odkazu
ms.date: 08/27/2018
helpviewer_keywords:
- arguments [C++], function
- functions [C++], paramters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
ms.openlocfilehash: cc5a65e9a6bd74e79856057cf7e7fea220c62d4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536199"
---
# <a name="reference-type-function-arguments"></a>Argumenty funkce typu odkazu

Často je efektivnější funkcím předávat reference namísto velkých objektů. To umožňuje kompilátoru předat adresu objektu při zachování syntaxe, která by byla použita k přístupu k objektu. Prohlédněte si následující příklad používající strukturu `Date`:

```cpp
// reference_type_function_arguments.cpp
#include <iostream>

struct Date
{
    short Month;
    short Day;
    short Year;
};

// Create a date of the form DDDYYYY (day of year, year)
// from a Date.
long DateOfYear( Date& date )
{
    static int cDaysInMonth[] = {
        31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31
    };
    long dateOfYear = 0;

    // Add in days for months already elapsed.
    for ( int i = 0; i < date.Month - 1; ++i )
        dateOfYear += cDaysInMonth[i];

    // Add in days for this month.
    dateOfYear += date.Day;

    // Check for leap year.
    if ( date.Month > 2 &&
        (( date.Year % 100 != 0 || date.Year % 400 == 0 ) &&
        date.Year % 4 == 0 ))
        dateOfYear++;

    // Add in year.
    dateOfYear *= 10000;
    dateOfYear += date.Year;

    return dateOfYear;
}

int main()
{
    Date date{ 8, 27, 2018 };
    long dateOfYear = DateOfYear(date);
    std::cout << dateOfYear << std::endl;
}
```

Předchozí kód ukazuje, že členy struktury předané referencí jsou zpřístupněny pomocí operátoru výběru členů (**.**) namísto operátoru volby členu ukazatel (**->**).

Ačkoli argumenty předané jako typy referencí používají syntaxi typů typech bez ukazatele, zachovávají důležitou vlastnost typů ukazatelů: lze, pokud nejsou deklarovány jako je **const**. Jelikož účelem předcházejícího kódu není upravit objekt `date`, je vhodnějším prototypem funkce tento prototyp:

```cpp
long DateOfYear( const Date& date );
```

Tento prototyp zaručuje, že funkce `DateOfYear` nezmění svůj argument.

Všechny funkce prototyp přijímá typ odkazu může přijmout objekt stejného typu na jeho místo, protože existuje standardní převod z *typename* k *typename* <strong>&</strong>.

## <a name="see-also"></a>Viz také:

[Odkazy](../cpp/references-cpp.md)<br/>
