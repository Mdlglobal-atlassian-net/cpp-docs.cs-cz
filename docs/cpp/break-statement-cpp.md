---
title: BREAK – příkaz (C++) | Microsoft Docs
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
ms.openlocfilehash: c3679ad27683e5f7ff9a13f5b5021710f7894c04
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="break-statement-c"></a>break – příkaz (C++)
`break` Příkaz ukončí provádění nejbližší obklopuje smyčky nebo podmíněného příkaz, ve kterém se zobrazí. Řízení se předá příkazu, který následuje po konci příkazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
break;  
```  
  
## <a name="remarks"></a>Poznámky  
 `break` Pomocí zásad správy se použije příkaz [přepínač](../cpp/switch-statement-cpp.md) příkaz a [provést](../cpp/do-while-statement-cpp.md), [pro](../cpp/for-statement-cpp.md), a [při](../cpp/while-statement-cpp.md) smyčky příkazy.  
  
 V `switch` příkaz, `break` příkaz způsobí, že program, který chcete spustit další příkaz mimo `switch` příkaz. Bez `break` příkaz, každý příkaz z odpovídající `case` popisek na konec `switch` prohlášení, včetně `default` klauzule, se spustí.  
  
 V smyčky `break` příkaz ukončí provádění nejbližší obklopuje `do`, `for`, nebo `while` příkaz. Řízení se předá příkazu, který následuje ukončený příkaz.  
  
 V rámci vnořené příkazy `break` příkaz končí pouze `do`, `for`, `switch`, nebo `while` příkaz, který okamžitě uzavře ho. Můžete použít `return` nebo `goto` příkaz k přenosu řízení z více hluboko vnořené struktury.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje způsob použití `break` příkaz v `for` smyčky.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    // An example of a standard for loop  
    for (int i = 1; i < 10; i++)  
    {  
        cout << i << '\n';  
        if (i == 4)  
            break;  
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
  
 Následující kód ukazuje, jak používat `break` v `while` smyčky a `do` smyčky.  
  
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
  
 Následující kód ukazuje, jak používat `break` v příkazu switch. Je nutné použít `break` ve všech případech, pokud chcete pro každý případ zpracování samostatně; pokud nepoužijete `break`, provádění kódu se k další případ.  
  
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
 [Jump – příkazy](../cpp/jump-statements-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [continue – příkaz](../cpp/continue-statement-cpp.md)