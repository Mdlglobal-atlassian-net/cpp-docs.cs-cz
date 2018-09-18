---
title: BREAK – příkaz (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- break_cpp
dev_langs:
- C++
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99b342719593b2072cdba21e3200aa23daa8f9df
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087277"
---
# <a name="break-statement-c"></a>break – příkaz (C++)

**Přerušení** příkaz ukončí vykonávání nejbližšího obklopujícího cyklu nebo podmíněného příkazu, ve kterém se zobrazí. Řízení se předá příkazu, který následuje po konci příkazu.

## <a name="syntax"></a>Syntaxe

```
break;
```

## <a name="remarks"></a>Poznámky

**Přerušení** prohlášení se používá s podmíněným [přepnout](../cpp/switch-statement-cpp.md) příkazu a s [proveďte](../cpp/do-while-statement-cpp.md), [pro](../cpp/for-statement-cpp.md), a [při](../cpp/while-statement-cpp.md) příkazy pro cykly.

V **přepnout** příkazu **přerušení** příkaz způsobí, že se program spustí další příkaz mimo příkaz **přepnout** příkaz. Bez **přerušení** prohlášení, každý příkaz ze spárovaného **případ** popisek na konec objektu **přepnout** prohlášení, včetně **výchozí**klauzule, je proveden.

Ve smyčkách **přerušení** ukončí vykonávání nejbližšího obklopujícího příkazu **proveďte**, **pro**, nebo **při** příkazu. Řízení se předá příkazu, který následuje ukončený příkaz.

V rámci vnořených příkazů **přerušení** ukončí pouze příkaz **proveďte**, **pro**, **přepnout**, nebo **při**příkaz, který jej bezprostředně obklopuje. Můžete použít **vrátit** nebo **goto** příkaz k přenosu řízení z více hluboce vnořené struktury.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak používat **přerušení** výroky **pro** smyčky.

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

Následující kód ukazuje, jak používat **přerušení** v **při** smyčky a **proveďte** smyčky.

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

Následující kód ukazuje, jak používat **přerušení** v příkazu switch. Je nutné použít **přerušení** ve všech případech, pokud chcete jednotlivé případy zpracovat zvlášť; pokud nepoužijete **přerušení**, spouštění kódu přejde na další případ.

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

## <a name="see-also"></a>Viz také:

[Jump – příkazy](../cpp/jump-statements-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[continue – příkaz](../cpp/continue-statement-cpp.md)