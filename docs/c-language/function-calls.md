---
title: Volání funkcí
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
ms.openlocfilehash: cce1a888f3e1224822ab4e97c67bf59da4c46fc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334577"
---
# <a name="function-calls"></a>Volání funkcí

*Volání funkce* je výraz, který předává ovládací prvek a argumenty (pokud existuje) funkci a má formulář:

*výraz* (*volba seznamu výrazů*<sub>opt</sub>)

kde *výraz* je název funkce nebo vyhodnocuje adresu funkce a *seznam výrazů* je seznam výrazů (oddělených čárkami). Hodnoty těchto pozdějších výrazů jsou argumenty předané funkci. Pokud funkce nevrátí hodnotu, pak deklarujete, `void`že je funkce, která vrátí .

Pokud deklarace existuje před voláním funkce, ale nejsou uvedeny žádné informace týkající se parametrů, všechny nedeklarované argumenty jednoduše podstoupí obvyklé aritmetické převody.

> [!NOTE]
> Výrazy v seznamu argumentů funkce lze vyhodnotit v libovolném pořadí, takže argumenty, jejichž hodnoty mohou být změněny vedlejšími účinky jiného argumentu, mají nedefinované hodnoty. Sekvenční bod definovaný operátorem volání funkce zaručuje pouze to, že všechny vedlejší účinky v seznamu argumentů jsou vyhodnoceny před tím, než ovládací prvek předá volanou funkci. (Všimněte si, že pořadí, ve kterém jsou argumenty posunuty v zásobníku je samostatná záležitost.) Další informace naleznete [v tématu Body sekvence.](../c-language/c-sequence-points.md)

Jediným požadavkem v každém volání funkce je, že výraz před závorky musí vyhodnotit na adresu funkce. To znamená, že funkce může být volána prostřednictvím libovolného výrazu ukazatel funkce.

## <a name="example"></a>Příklad

Tento příklad ilustruje volání funkcí `switch` volaných z příkazu:

```
int main()
{
    /* Function prototypes */

    long lift( int ), step( int ), drop( int );
    void work( int number, long (*function)(int i) );

    int select, count;
    .
    .
    .
    select = 1;
    switch( select )
    {
        case 1: work( count, lift );
                break;

        case 2: work( count, step );
                break;

        case 3: work( count, drop );
                /* Fall through to next case */
        default:
                break;
    }
}

/* Function definition */

void work( int number, long (*function)(int i) )
{
    int i;
    long j;

    for ( i = j = 0; i < number; i++ )
            j += ( *function )( i );
}
```

V tomto příkladu funkce `main`volání v ,

```
work( count, lift );
```

předává funkci celou `count`proměnnou a adresu `lift` funkce `work`. Všimněte si, že adresa funkce je předána jednoduše tím, že identifikátor funkce, protože identifikátor funkce vyhodnocuje výraz ukazatele. Chcete-li použít identifikátor funkce tímto způsobem, musí být funkce deklarována nebo definována před použitím identifikátoru; v opačném případě identifikátor není rozpoznán. V tomto případě je `work` prototyp pro uveden `main` na začátku funkce.

Parametr `function` in `work` je deklarován jako `int` ukazatel na funkci, která přebírá jeden argument a vrací **dlouhou** hodnotu. Závorky kolem názvu parametru jsou povinné; bez nich by deklarace specifikovala funkci vracející ukazatel na **dlouhou** hodnotu.

Funkce `work` volá vybranou funkci zevnitř smyčky **for** pomocí následujícího volání funkce:

```
( *function )( i );
```

Jeden argument `i`, je předán volané funkci.

## <a name="see-also"></a>Viz také

[Functions](../c-language/functions-c.md)
