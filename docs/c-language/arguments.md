---
title: Arguments
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- functions [C], parameters
- function parameters, about function parameters
- function arguments
- function calls, arguments
ms.assetid: 14cf0389-2265-41f0-9a96-f2223eb406ca
ms.openlocfilehash: e60a7935cdddc116848b64461b064c5fd5cdd00a
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148722"
---
# <a name="arguments"></a>Arguments

Argumenty ve volání funkce mohou mít následující tvar:

> *výraz* **(** *seznam výrazů*<SUB>optimalizované</SUB> **)** / * volání funkce * /

Ve volání funkce *seznam výrazů* je seznamem výrazů (oddělený čárkami). Hodnoty těchto pozdějších výrazů jsou argumenty předané funkci. Pokud funkce nepřijímá žádné argumenty, *seznam výrazů* by měla obsahovat klíčové slovo `void`.

Argument může být libovolná hodnota základního typu, struktury, sjednocení nebo ukazatele. Všechny argumenty jsou předávány hodnotou. To znamená, že je do odpovídajícího parametru přiřazena kopie argumentu. Funkce nezná skutečné umístění předaného argumentu v paměti. Funkce tuto kopii používá, aniž by ovlivnila proměnnou, ze které byla kopie odvozena.

Ačkoli jako argumenty nelze předávat pole či funkce, lze předat ukazatele na tyto položky. Ukazatele poskytují způsob, jakým může funkce přistupovat k hodnotě pomocí reference. Protože ukazatel na proměnnou udržuje adresu proměnné, může funkce tuto adresu použít k přístupu k hodnotě dané proměnné. Argumenty ukazatelů umožňují funkci přistoupit k polím a funkcím i přesto, že pole a funkce nelze předávat jako argumenty.

Pořadí, ve kterém jsou argumenty vyhodnocovány, se může v různých kompilátorech a s různými úrovněmi optimalizace lišit. Před vstupem do funkce jsou však argumenty a všechny vedlejší účinky plně vyhodnoceny. Zobrazit [vedlejší účinky](../c-language/side-effects.md) o vedlejší účinky.

*Seznam výrazů* ve funkci volání vyhodnocen a obvyklé aritmetické převody jsou prováděny na všech argumentech ve volání funkce. Je-li k dispozici prototyp, je výsledný typ argumentu porovnán s odpovídajícím parametrem prototypu. Pokud se neshodují, je proveden převod nebo zobrazena diagnostická zpráva. Parametry také prochází obvyklými aritmetickými převody.

Počet výrazů v *seznam výrazů* musí odpovídat počtu parametrů, není-li prototyp nebo definice funkce explicitně určuje proměnný počet argumentů. V tomto případě kompilátor kontroluje tolik argumentů, kolik je v seznamu parametrů názvů typů, a v případě potřeby je převede tak, jak je popsáno výše. Zobrazit [volání proměnlivým počtem argumentů](../c-language/calls-with-a-variable-number-of-arguments.md) Další informace.

Obsahuje-li seznam parametrů prototypu pouze klíčové slovo `void`, kompilátor neočekává žádné argumenty ve volání funkce a žádné parametry v definici. Jsou-li nějaké argumenty nalezeny, je zobrazena diagnostická zpráva.

## <a name="example"></a>Příklad

Tento příklad používá jako argumenty ukazatele:

```C
int main()
{
    /* Function prototype */

    void swap( int *num1, int *num2 );
    int x, y;
    .
    .
    .
    swap( &x, &y );  /* Function call */
}

/* Function definition */

void swap( int *num1, int *num2 )
{
    int t;

    t = *num1;
    *num1 = *num2;
    *num2 = t;
}
```

V tomto příkladu je deklarována funkce `swap` ve funkci `main` se dvěma argumenty reprezentovanými identifikátory `num1` a `num2`, z nichž oba jsou ukazatele na hodnoty typu `int`. Parametry `num1` a `num2` v definici ve stylu prototypu jsou také deklarovány jako ukazatele na hodnoty typu `int`.

Ve volání funkce

```C
swap( &x, &y )
```

je adresa proměnné `x` uložena v argumentu `num1` a adresa proměnné `y` je uložena v argumentu `num2`. Nyní pro jedno umístění existují dva názvy („aliasy“). Reference na argumenty `*num1` a `*num2` ve funkci `swap` jsou fakticky reference na proměnné `x` a `y` ve funkci `main`. Přiřazení ve funkci `swap` ve skutečnosti zamění obsah proměnných `x` a `y`. Proto není zapotřebí žádného příkazu `return`.

Kompilátor pro argumenty funkce `swap` provádí kontrolu typů, protože prototyp funkce `swap` obsahuje typy argumentů pro každý parametr. Identifikátory v závorkách prototypu a definice mohou být shodné či odlišné. Důležité je, aby se v prototypu i v definici shodovaly typy argumentů s parametry v seznamu parametrů.

## <a name="see-also"></a>Viz také:

[Volání funkcí](../c-language/function-calls.md)
