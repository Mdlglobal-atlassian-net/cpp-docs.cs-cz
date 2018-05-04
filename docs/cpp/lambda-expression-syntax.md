---
title: Syntaxe výrazu lambda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1faf0458a9cf1a528e9a0c2582e8d2ec3715f149
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="lambda-expression-syntax"></a>Syntaxe výrazu lambda
Tento článek ukazuje syntaxi a strukturální elementy výrazů lambda. Popis výrazů lambda najdete v tématu [výrazy Lambda](../cpp/lambda-expressions-in-cpp.md).  
  
## <a name="function-objects-vs-lambdas"></a>Funkce objekty vs. Výrazy lambda  
 Při psaní kódu, pravděpodobně použijete ukazatelů na funkce a objekty funkcí k řešení problémů a provádět výpočty, zejména v případě, že používáte [standardní knihovna C++ algoritmy](../cpp/algorithms-modern-cpp.md). Ukazatele na funkce a funkce objekty mají výhody a nevýhody – například ukazatelů na funkce mají minimální syntaktické režii, ale není zachovat stav v rámci oboru a objekty funkcí můžete udržovat stav ale vyžadují syntaktické režii definice třídy.  
  
 Výraz lambda kombinuje výhody ukazatelů na funkce a objektů funkce a předchází jejich nevýhodám. Podobně jako objekty funkce lambda je flexibilní a můžete udržovat stav, ale na rozdíl od funkce objektu, jeho compact syntaxe nevyžaduje definici explicitní třídy. Pomocí výrazů lambda lze napsat kód, který je méně náročný a náchylný k chybám než kód pro ekvivalentní objekt funkce.  
  
 Následující příklady porovnávají použití výrazu lambda a objektu funkce. V prvním příkladu používá lambda tisk do konzoly zda každý prvek v `vector` objekt je popisných. Druhý příklad používá objekt funkce k provedení stejné úlohy.  
  
## <a name="example-1-using-a-lambda"></a>Příklad 1: Použití výrazu lambda  
 Tento příklad předá lambda k `for_each` funkce. Argument lambda vytiskne výsledek, který uvádí, zda každý prvek v `vector` objekt je popisných.  
  
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
   // Create a vector object that contains 10 elements.  
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
  
### <a name="output"></a>Výstup  
  
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
 V příkladu třetí argument `for_each` funkce je lambda. `[&evenCount]` Část určuje klauzuli zachycení výrazu, `(int n)` určuje seznam parametrů a zbývající část určuje text výrazu.  
  
## <a name="example-2-using-a-function-object"></a>Příklad 2: Použití objektu funkce  
 Výraz lambda je někdy příliš nepraktické rozšířit více než v předchozím příkladu. Další příklad používá objekt funkce místo lambda, společně s `for_each` funkce k vytvoření stejné výsledky jako příklad 1. Uložení počet sudým číslům v obou příkladech `vector` objektu. Pro uchování stavu operace `FunctorClass` třídy úložiště `m_evenCount` proměnné odkazem jako členské proměnné. K provedení operace, `FunctorClass` implementuje operátor volání funkce `operator()`. Kompilátor jazyka Visual C++ vygeneruje kód, který je srovnatelné velikosti a výkonu jako kód výrazu lambda v příkladu 1. Pro řešení základního problému jako v tomto článku platí, že jednodušší návrh výrazu lambda je pravděpodobně lepší než návrh funkce objektu. Pokud však myslíte, že funkce mohou v budoucnu vyžadovat značné rozšíření, použijte návrh objektu funkce pro snazší údržbu kódu.  
  
 Další informace o `operator()`, najdete v části [volání funkce](../cpp/function-call-cpp.md). Další informace o `for_each` funkce najdete v tématu [for_each –](../standard-library/algorithm-functions.md#for_each).  
  
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
    // Create a vector object that contains 10 elements.  
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
  
## <a name="output"></a>Výstup  
  
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
 [Lambda – výrazy](../cpp/lambda-expressions-in-cpp.md)   
 [Příklady výrazů Lambda](../cpp/examples-of-lambda-expressions.md)   
 [Generovat](../standard-library/algorithm-functions.md#generate)   
 [generate_n –](../standard-library/algorithm-functions.md#generate_n)   
 [for_each –](../standard-library/algorithm-functions.md#for_each)   
 [Specifikace výjimek (throw)](../cpp/exception-specifications-throw-cpp.md)   
 [C4297 kompilátoru upozornění (úroveň 1)](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)   
 [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md)