---
title: Syntaxe výrazu lambda
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
ms.openlocfilehash: 9ac2fdea1a8fc8dcf2b03059455c3141daf86aa8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179650"
---
# <a name="lambda-expression-syntax"></a>Syntaxe výrazu lambda

Tento článek ukazuje syntaxi a strukturální prvky výrazů lambda. Popis výrazů lambda naleznete v tématu [lambda Expressions](../cpp/lambda-expressions-in-cpp.md).

## <a name="function-objects-vs-lambdas"></a>Objekty funkce vs. výrazy lambda

Při psaní kódu pravděpodobně použijete ukazatele na funkce a objekty funkce k řešení problémů a provádění výpočtů, zejména při použití [ C++ algoritmů standardní knihovny](../cpp/algorithms-modern-cpp.md). Ukazatele na funkce a objekty funkce mají tyto výhody a nevýhody – například ukazatele na funkce mají minimální syntaktickou režii, ale neuchovávají stav v rámci rozsahu a objekty funkcí mohou udržovat stav, ale vyžadují syntaktickou režii. definice třídy.

Výraz lambda kombinuje výhody ukazatelů na funkce a objektů funkce a předchází jejich nevýhodám. Podobně jako objekty funkce je výraz lambda flexibilní a může udržovat stav, ale na rozdíl od objektu funkce, jeho syntaxe Compact nevyžaduje explicitní definici třídy. Pomocí výrazů lambda lze napsat kód, který je méně náročný a náchylný k chybám než kód pro ekvivalentní objekt funkce.

Následující příklady porovnávají použití výrazu lambda a objektu funkce. První příklad používá výraz lambda pro tisk do konzoly, zda je každý prvek objektu `vector` sudý nebo lichý. Druhý příklad používá objekt funkce k provedení stejné úlohy.

## <a name="example-1-using-a-lambda"></a>Příklad 1: Použití výrazu lambda

Tento příklad předává lambda funkci **for_each** . Lambda vytiskne výsledek, který uvádí, zda je každý prvek v objektu `vector` sudý nebo lichý.

### <a name="code"></a>Kód

```cpp
// even_lambda.cpp
// compile with: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

int main()
{
   // Create a vector object that contains 9 elements.
   vector<int> v;
   for (int i = 1; i < 10; ++i) {
      v.push_back(i);
   }

   // Count the number of even numbers in the vector by
   // using the for_each function and a lambda.
   int evenCount = 0;
   for_each(v.begin(), v.end(), [&evenCount] (int n) {
      cout << n;
      if (n % 2 == 0) {
         cout << " is even " << endl;
         ++evenCount;
      } else {
         cout << " is odd " << endl;
      }
   });

   // Print the count of even numbers to the console.
   cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

### <a name="comments"></a>Komentáře

V příkladu je třetí argument funkce **for_each** lambda. Část `[&evenCount]` určuje klauzuli zachycení výrazu, `(int n)` určuje seznam parametrů a zbývající část určuje tělo výrazu.

## <a name="example-2-using-a-function-object"></a>Příklad 2: Použití objektu funkce

Výraz lambda je někdy příliš nepraktické rozšířit více než v předchozím příkladu. Následující příklad používá objekt funkce namísto lambda společně s funkcí **for_each** , aby vytvořil stejné výsledky jako příklad 1. Oba příklady ukládají počet sudých čísel v objektu `vector`. Chcete-li zachovat stav operace, třída `FunctorClass` ukládá proměnnou `m_evenCount` odkazem jako členskou proměnnou. K provedení této operace `FunctorClass` implementuje operátor volání funkce, **operátor ()** . Kompilátor společnosti C++ Microsoft generuje kód, který je porovnatelný z rozsahu a výkonu pro kód lambda v příkladu 1. Pro řešení základního problému jako v tomto článku platí, že jednodušší návrh výrazu lambda je pravděpodobně lepší než návrh funkce objektu. Pokud však myslíte, že funkce mohou v budoucnu vyžadovat značné rozšíření, použijte návrh objektu funkce pro snazší údržbu kódu.

Další informace o **operátoru ()** naleznete v tématu [Call Function](../cpp/function-call-cpp.md). Další informace o funkci **for_each** naleznete v tématu [for_each](../standard-library/algorithm-functions.md#for_each).

### <a name="code"></a>Kód

```cpp
// even_functor.cpp
// compile with: /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

class FunctorClass
{
public:
    // The required constructor for this example.
    explicit FunctorClass(int& evenCount)
        : m_evenCount(evenCount) { }

    // The function-call operator prints whether the number is
    // even or odd. If the number is even, this method updates
    // the counter.
    void operator()(int n) const {
        cout << n;

        if (n % 2 == 0) {
            cout << " is even " << endl;
            ++m_evenCount;
        } else {
            cout << " is odd " << endl;
        }
    }

private:
    // Default assignment operator to silence warning C4512.
    FunctorClass& operator=(const FunctorClass&);

    int& m_evenCount; // the number of even variables in the vector.
};

int main()
{
    // Create a vector object that contains 9 elements.
    vector<int> v;
    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }

    // Count the number of even numbers in the vector by
    // using the for_each function and a function object.
    int evenCount = 0;
    for_each(v.begin(), v.end(), FunctorClass(evenCount));

    // Print the count of even numbers to the console.
    cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../cpp/lambda-expressions-in-cpp.md)<br/>
[Příklady výrazů lambda](../cpp/examples-of-lambda-expressions.md)<br/>
[vytváří](../standard-library/algorithm-functions.md#generate)<br/>
[generate_n](../standard-library/algorithm-functions.md#generate_n)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)<br/>
[Specifikace výjimek (throw)](../cpp/exception-specifications-throw-cpp.md)<br/>
[Upozornění kompilátoru (úroveň 1) C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)<br/>
[Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md)
