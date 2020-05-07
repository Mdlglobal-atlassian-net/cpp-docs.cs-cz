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

*Volání funkce* je výraz, který předává řízení a argumenty (pokud existují) do funkce a má formu:

*výraz* (*výraz-seznam*<sub>opt</sub>)

*výraz* WHERE je název funkce nebo se vyhodnotí jako adresa funkce a *výraz – seznam* výrazů (oddělených čárkami). Hodnoty těchto pozdějších výrazů jsou argumenty předané funkci. Pokud funkce nevrací hodnotu, deklarujete ji jako funkci, která vrací `void`.

Pokud existuje deklarace před voláním funkce, ale nejsou k dispozici žádné informace týkající se parametrů, jakékoli nedeklarované argumenty jednoduše podstoupí obvyklým aritmetickým převodům.

> [!NOTE]
> Výrazy v seznamu argumentů funkce lze vyhodnotit v libovolném pořadí, takže argumenty, jejichž hodnoty mohou být změněny vedlejšími účinky z jiného argumentu, mají nedefinované hodnoty. Bod sekvence definovaný operátorem volání funkce garantuje pouze to, že všechny vedlejší účinky v seznamu argumentů jsou vyhodnocovány před předáním řízení volané funkci. (Všimněte si, že pořadí, ve kterém jsou argumenty vloženy do zásobníku, je samostatné.) Další informace naleznete v části [body sekvence](../c-language/c-sequence-points.md) .

Jediným požadavkem v každém volání funkce je, že výraz před závorkami musí být vyhodnocen na adresu funkce. To znamená, že funkci lze volat prostřednictvím libovolného výrazu na ukazatel na funkci.

## <a name="example"></a>Příklad

Tento příklad znázorňuje volání funkcí volaných z `switch` příkazu:

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

V tomto příkladu je volání funkce v `main`,

```
work( count, lift );
```

předá do funkce `count` `lift` `work`celočíselnou proměnnou, a adresu funkce. Všimněte si, že adresa funkce je předána jednoduše předáním identifikátoru funkce, protože identifikátor funkce je vyhodnocen jako výraz ukazatele. Chcete-li použít identifikátor funkce tímto způsobem, musí být funkce deklarována nebo definována před použitím identifikátoru; v opačném případě identifikátor není rozpoznán. V tomto případě je prototyp pro `work` uveden na začátku `main` funkce.

Parametr `function` v `work` je deklarován jako ukazatel na funkci, která přijímá jeden `int` argument a vrací **dlouhou** hodnotu. Jsou vyžadovány závorky kolem názvu parametru. bez nich deklarace by určovala funkci, která vrací ukazatel na **dlouhou** hodnotu.

Funkce `work` volá vybranou funkci zevnitř smyčky **for** pomocí následujícího volání funkce:

```
( *function )( i );
```

Jeden argument, `i`, se předává volané funkci.

## <a name="see-also"></a>Viz také

[Functions](../c-language/functions-c.md)
