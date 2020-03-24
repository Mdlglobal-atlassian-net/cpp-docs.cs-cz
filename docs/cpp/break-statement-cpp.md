---
title: break – příkaz (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 23d31e1456106d5f82c4a13079c72c231b8477bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190479"
---
# <a name="break-statement-c"></a>break – příkaz (C++)

Příkaz **Break** ukončí provádění nejbližší ohraničující smyčky nebo podmíněného příkazu, ve kterém se zobrazí. Řízení se předá příkazu, který následuje po konci příkazu.

## <a name="syntax"></a>Syntaxe

```
break;
```

## <a name="remarks"></a>Poznámky

Příkaz **Break** se používá spolu s podmíněným příkazem [Switch](../cpp/switch-statement-cpp.md) a s příkazy [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)a [while](../cpp/while-statement-cpp.md) .

V příkazu **Switch** příkaz **Break** způsobí, že program spustí následující příkaz mimo příkaz **Switch** . Bez příkazu **Break** se spustí všechny příkazy z popisku odpovídajícího **případu** až po konec příkazu **Switch** , včetně **výchozí** klauzule.

Ve smyčce ukončí příkaz **Break** provádění nejbližšího ohraničujícího příkazu **do**, **for**nebo **while** . Řízení se předá příkazu, který následuje ukončený příkaz.

V rámci vnořených příkazů **příkaz break** ukončí pouze příkaz **do**, **pro**, **Switch**nebo **while** , který jej bezprostředně obklopuje. Můžete použít příkaz **return** nebo **goto** pro přenos řízení z hlouběji vnořených struktur.

## <a name="example"></a>Příklad

Následující kód ukazuje použití příkazu **Break** ve smyčce **for** .

```cpp
#include <iostream>
using namespace std;

int main()
{
    // An example of a standard for loop
    for (int i = 1; i < 10; i++)
    {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }

    // An example of a range-based for loop
int nums []{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

    for (int i : nums) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }
}
```

```Output
In each case:
1
2
3
```

Následující kód ukazuje, jak použít **přerušení** ve smyčce **while** **a smyčka do.**

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;

    while (i < 10) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    }

    i = 0;
    do {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    } while (i < 10);
}
```

```Output
In each case:
0123
```

Následující kód ukazuje, jak použít **přerušení** v příkazu switch. Je nutné použít **přerušení** v každém případě, pokud chcete zpracovat každý případ zvlášť; Pokud nepoužijete příkaz **Break**, spuštění kódu přejde do dalšího případu.

```cpp
#include <iostream>
using namespace std;

enum Suit{ Diamonds, Hearts, Clubs, Spades };

int main() {

    Suit hand;
    . . .
    // Assume that some enum value is set for hand
    // In this example, each case is handled separately
    switch (hand)
    {
    case Diamonds:
        cout << "got Diamonds \n";
        break;
    case Hearts:
        cout << "got Hearts \n";
        break;
    case Clubs:
        cout << "got Clubs \n";
        break;
    case Spades:
        cout << "got Spades \n";
        break;
    default:
          cout << "didn't get card \n";
    }
    // In this example, Diamonds and Hearts are handled one way, and
    // Clubs, Spades, and the default value are handled another way
    switch (hand)
    {
    case Diamonds:
    case Hearts:
        cout << "got a red card \n";
        break;
    case Clubs:
    case Spades:
    default:
        cout << "didn't get a red card \n";
    }
}
```

## <a name="see-also"></a>Viz také

[Jump – příkazy](../cpp/jump-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[continue – příkaz](../cpp/continue-statement-cpp.md)
