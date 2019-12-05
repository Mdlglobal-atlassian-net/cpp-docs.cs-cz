---
title: Sémantika výrazů
ms.date: 11/19/2018
helpviewer_keywords:
- grammar, expressions
- expressions [C++], semantics
- expression evaluation
- expression evaluation, about expression evaluation
ms.assetid: 4a792154-533b-48b9-8709-31bfc170f0a7
ms.openlocfilehash: 6770d3fb314222c7c58b6b97fa42d74cbc1e9b33
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857317"
---
# <a name="semantics-of-expressions"></a>Sémantika výrazů

Výrazy jsou vyhodnocovány podle priority a seskupení jejich operátorů. ([Priorita operátorů a asociativita](../cpp/cpp-built-in-operators-precedence-and-associativity.md) v [lexikálních konvencích](../cpp/lexical-conventions.md)zobrazuje vztahy C++ , které operátory ukládají do výrazů.)

## <a name="order-of-evaluation"></a>Pořadí vyhodnocení

Vezměte v úvahu tento příklad:

```cpp
// Order_of_Evaluation.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main()
{
    int a = 2, b = 4, c = 9;

    cout << a + b * c << "\n";
    cout << a + (b * c) << "\n";
    cout << (a + b) * c << "\n";
}
```

```Output
38
38
54
```

![Pořadí vyhodnocení ve výrazu](../cpp/media/vc38zv1.gif "Pořadí vyhodnocení ve výrazu") <br/>
Pořadí vyhodnocení výrazu

Pořadí, ve kterém je výraz podle výše uvedeného obrázku vyhodnocen, se stanoví pomocí přednosti a asociativity operátorů:

1. Násobení (*) má v tomto výrazu nejvyšší prioritu, proto je podvýraz `b * c` vyhodnocen jako první.

1. Sčítání (+) má další nejvyšší prioritu, takže hodnota proměnné `a` je přičtena k výsledku operace s proměnnými `b` a `c`.

1. Levý SHIFT (< <) má ve výrazu nejnižší prioritu, ale existují dva výskyty. Vzhledem k tomu, že operátor levého posunu seskupuje zleva doprava, je levý podvýraz vyhodnocen jako první, a potom je vyhodnocen pravý podvýraz.

Použití závorek k seskupení podvýrazů mění prioritu a také pořadí, ve kterém je výraz vyhodnocen, jak je znázorněno na následujícím obrázku.

![Pořadí vyhodnocování výrazu pomocí závorek](../cpp/media/vc38zv2.gif "Pořadí vyhodnocování výrazu pomocí závorek") <br/>
Pořadí vyhodnocování výrazů pomocí závorek

Výrazy, například na výše uvedeném obrázku, jsou vyhodnoceny výhradně z hlediska jejich vedlejších účinků, v tomto případě pro přenos informací na standardní výstup zařízení.

## <a name="notation-in-expressions"></a>Zápis ve výrazech

C++ Jazyk určuje určité kompatibility při zadávání operandů. V následující tabulce jsou uvedeny typy operandů, které jsou přijatelné pro operátory, které vyžadují operandy *typu Type.*

### <a name="operand-types-acceptable-to-operators"></a>Typy operandů přijatelné pro operátory

|Očekáván typ|Povolené typy|
|-------------------|-------------------|
|*type*|*typ* `const`<br /> *typ* `volatile`<br /> *zadejte*&<br /> *typ* `const`&<br /> *typ* `volatile`&<br /> *typ* `volatile const`<br /> *typ* `volatile const`&|
|*zadejte* \*|*zadejte* \*<br /> *typ* `const` \*<br /> *typ* `volatile` \*<br /> *typ* `volatile const` \*|
|*typ* `const`|*type*<br /> *typ* `const`<br />*typ* `const`&|
|*typ* `volatile`|*type*<br /> *typ* `volatile`<br /> *typ* `volatile`&|

Vzhledem k tomu, že předchozí pravidla mohou být vždy použita v kombinaci, lze zadat ukazatel const na nestálý objekt, kde je očekáván ukazatel.

## <a name="ambiguous-expressions"></a>Nejednoznačné výrazy

Některé výrazy jsou ve svém významu nejednoznačné. Tyto výrazy se nejčastěji vyskytují, je-li hodnota objektu ve stejném výrazu změněna více než jednou. Tyto výrazy se spoléhají na určité pořadí vyhodnocování tam, kde jazyk žádné nedefinuje. Vezměte v úvahu v následujícím příkladu:

```
int i = 7;

func( i, ++i );
```

Jazyk C++ nezaručuje pořadí, ve kterém jsou argumenty pro volání funkce vyhodnocovány. Proto by v předcházejícím příkladu mohla `func` pro své parametry přijímat hodnoty 7 a 8 nebo 8 a 8 podle toho, zda jsou parametry vyhodnoceny zleva doprava nebo zprava doleva.

## <a name="c-sequence-points-microsoft-specific"></a>C++body sekvence (specifické pro Microsoft)

Výraz může změnit hodnotu objektu mezi po sobě jdoucími „body sekvence“ pouze jednou.

Definice jazyka C++ aktuálně nespecifikuje body sekvence. Jazyk C++ společnosti Microsoft používá stejné body sekvence jako standard ANSI C pro všechny výrazy zahrnující operátory jazyka C a nevyžaduje přetížené operátory. Pokud jsou operátory přetíženy, sémantika se změní ze sekvence operátorů na sekvenci volání funkce. Jazyk C++ společnosti Microsoft používá následující body sekvence:

- Levý operand logického operátoru AND (& &). Levý operand logického operátoru AND je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním dokončeny. Není zaručeno, že bude pravý operand logického operátoru AND vyhodnocen.

- Levý operand logického operátoru OR (&#124;&#124;). Levý operand logického operátoru OR je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním dokončeny. Není zaručeno, že bude pravý operand logického operátoru OR vyhodnocen.

- Levý operand operátoru čárky. Levý operand logického operátoru čárky je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním dokončeny. Oba operandy operátoru čárky jsou vždy vyhodnoceny.

- Operátor volání funkce. Výraz volání funkce a všechny argumenty funkce, včetně výchozích argumentů, jsou vyhodnoceny a všechny vedlejší účinky dokončeny před vstupem do této funkce. Neexistuje žádné zadané pořadí vyhodnocování mezi argumenty nebo výrazem volání funkce.

- První operand podmíněného operátoru. První operand podmíněného operátoru je kompletně vyhodnocen a všechny vedlejší účinky jsou před pokračováním dokončeny.

- Konec úplného výrazu inicializace, jako je konec inicializace v příkazu deklarace.

- Výraz v příkazu výrazu. Příkazy výrazů se skládají z volitelného výrazu následovaného středníkem (;). Tento výraz je zcela vyhodnocen pro jeho vedlejší účinky.

- Řídicí výraz v příkazu výběru (if nebo switch). Výraz je vyhodnocen úplně a všechny vedlejší účinky jsou dokončeny před provedením kódu závislého na výběru.

- Řídicí výraz příkazu while nebo do. Výraz je zcela vyhodnocen a všechny vedlejší účinky jsou dokončeny před vykonáním jakýchkoli příkazů v další iteraci smyčky while nebo do.

- Všechny tři výrazy příkazu for. Každý výraz je úplně vyhodnocen a všechny vedlejší účinky dokončeny před přesunem k dalšímu výrazu.

- Výraz v příkazu return. Výraz je vyhodnocován úplně a všechny vedlejší účinky jsou dokončeny před návratem řízení do funkce volání.

## <a name="see-also"></a>Viz také:

[Výrazy](../cpp/expressions-cpp.md)