---
title: "Výrazy lambda v jazyce C++ | Microsoft Docs"
ms.custom: 
ms.date: 07/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
caps.latest.revision: "36"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 035fe5c222f6de5b3f0d71c0ce9133c1101f2993
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="lambda-expressions-in-c"></a>Výrazy lambda v jazyce C++
C ++ 11 a novější výrazu lambda – často říká *lambda*– je pohodlný způsob definice objekt anonymní funkce ( *uzavření*) přímo v umístění, kde je volána nebo předat jako argument funkce. Lambdas se obvykle používá k zapouzdření pár řádků kódu, které se budou předávat algoritmy nebo asynchronní metody. Tento článek definuje výrazy lambda, porovnává je s jinými programovacími technikami, popisuje jejich výhody a představuje základní příklad.  

## <a name="related-topics"></a>Související témata
- [Lambda – výrazy oproti objektům funkcí](lambda-expression-syntax.md)
- [Práce s výrazy lambda](examples-of-lambda-expressions.md)
- [výrazy lambda constexpr](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Části výrazu Lambda  
 Standardní C++ ISO ukazuje jednoduchý lambda, který je předán jako třetí argument `std::sort()` funkce:  
  
```cpp  
#include <algorithm>  
#include <cmath>  
  
void abssort(float* x, unsigned n) {  
    std::sort(x, x + n,  
        // Lambda expression begins  
        [](float a, float b) {  
            return (std::abs(a) < std::abs(b));  
        } // end of lambda expression  
    );  
}  
  
```  
  
 Tento obrázek ukazuje části lambda:  
  
 ![Strukturální prvky výrazu lambda](../cpp/media/lambdaexpsyntax.png "LambdaExpSyntax")  
  
1.  *zaznamenat klauzule* (také označované jako *lambda představení* ve specifikaci C++.)  
  
2.  *Seznam parametrů* volitelné. (Také označované jako *lambda deklarátor*)  
  
3.  *měnitelný specifikace* volitelné.  
  
4.  *specifikace výjimek* volitelné.  
  
5.  *Koncové typ návratové* volitelné.  
  
6.  *Lambda textu*)  
  
### <a name="capture-clause"></a>Klauzule zachycení  
 Lambda můžete zavádět nové proměnné v jeho textu (v **C ++ 14**) a může taky přístup, nebo *zaznamenat*, proměnné z okolního oboru. Lambda začíná v klauzuli zachycení (*lambda představení* v standardní syntaxi), která určuje, které proměnné zaznamenání, a jestli je zachytávání hodnotou nebo odkazem. Proměnné, které mají ampersand (`&`) předpona jsou dostupné přes odkaz a proměnné, které nemají ho přistupují hodnotu.  
  
 Klauzuli prázdný zachycení `[ ]`, označuje, že tělo výrazu lambda přistupuje k žádné proměnné ve vymezeném oboru.  
  
 Můžete použít výchozí režim zachycení (*zachycení výchozí* v standardní syntaxi) k označení jak zachytit všechny vnější proměnné, které jsou odkazované ve argument lambda: `[&]` znamená jsou zachyceny všechny proměnné, které odkazují na odkaz, a `[=]` znamená jsou zachyceny hodnotu. Můžete použít jiný režim zachytávání výchozí a pak zadejte opačné režim explicitně pro konkrétní proměnné. Například, pokud text lambda přistupuje k externí proměnná `total` odkazem a proměnnou externí `factor` podle hodnoty, pak následující klauzule zachycení odpovídají:  
  
```cpp  
[&total, factor]  
[factor, &total]  
[&, factor]  
[factor, &]  
[=, &total]  
[&total, =]  
```  
  
 Při použití výchozí zachycení zaznamenání pouze proměnné, které jsou uvedeny v argument lambda.  
  
 Pokud klauzuli zachycení zahrnuje zachycení výchozí `&`, pak žádný `identifier` v `capture` tohoto zachycení klauzule může mít formuláře `& identifier`. Podobně pokud klauzuli zachycení zahrnuje zachycení výchozí `=`, pak žádný `capture` tohoto zachycení klauzule může mít formuláře `= identifier`. Identifikátor nebo `this` nelze vložit více než jednou v klauzuli zachycení. Následující fragment kódu dokládá několik příkladů.  
  
```cpp  
struct S { void f(int i); };  
  
void S::f(int i) {  
    [&, i]{};      // OK  
    [&, &i]{};     // ERROR: i preceded by & when & is the default  
    [=, this]{};   // ERROR: this when = is the default  
    [=, *this]{ }; // OK: captures this by value. See below.
    [i, i]{};      // ERROR: i repeated  
}  
```  
  
 Zachycení, za nímž následuje třemi tečkami je rozšíření aktualizací Service pack, jak je uvedeno v tomto [variadické šablony](../cpp/ellipses-and-variadic-templates.md) příklad:  
  
```cpp  
template<class... Args>  
void f(Args... args) {  
    auto x = [args...] { return g(args...); };  
    x();  
}  
```  
  
 Chcete-li použití výrazů lambda v těle metody třídy, předat `this` ukazatel na klauzuli zachycení pro poskytnutí přístupu k metody a data členů nadřazených tříd. 
 
**Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): `this` ukazatele mohou být zachyceny hodnotou zadáním `*this` v klauzuli zachycení. Zachycení hodnotou znamená, že celý *uzavření*, který je objekt anonymní funkce této encapulates výrazu lambda, je zkopírována do každé volání lokality, kde je volána argument lambda. Zachycení hodnotou je užitečné, když argument lambda, budou spuštěny v paralelní nebo asynchronní operace, zejména u určité hardwarovou architekturou, jako je například technologie NUMA. 

Příklad, který ukazuje, jak pomocí metody třídy použití výrazů lambda, najdete v části "Příklad: pomocí Lambda výraz metoda" v [příklady výrazů Lambda](../cpp/examples-of-lambda-expressions.md).  
  
 Pokud použijete klauzuli snímek, doporučujeme ponechat tyto body na paměti, zvlášť pokud používáte lambdas s více vláken:  
  
-   Referenční dokumentace zachycení lze použít k úpravám proměnných mimo, ale hodnota zachycení nelze. (`mutable` umožňuje kopie má být změněn, ale není původních.)  
  
-   Zachycení referenční uplatňování aktualizací na proměnné mimo, ale hodnota zachycení nepodporují.  
  
-   Zachycení referenční zavést závislost doba platnosti, ale hodnota zachycení mít žádné závislosti životního cyklu. To je obzvláště důležité, když argument lambda běží asynchronně. Pokud zaznamenáte místním odkazem v asynchronní lambda, tento místní bude velmi pravděpodobně znovu podle času argument lambda běží, což vede k narušení přístupu v době běhu.  
  
### <a name="generalized-capture-c-14"></a>Zobecněný zachycení (C++ 14)  
  
 V C ++ 14 můžou představovat a inicializovat nové proměnné v klauzuli zachycení, aniž by bylo nutné mít tyto proměnné existovat ve vymezeném oboru funkce lambda. Inicializace může být vyjádřený jako jakýkoli libovolný výraz; Typ nové proměnné je odvozen z typu vytvářených výraz. Jednou z výhod tato funkce je, že v C ++ 14 můžete zaznamenat pouze přesunutí proměnné (například std::unique_ptr) z okolního oboru a jejich použití v lambda.  
  
```cpp  
pNums = make_unique<vector<int>>(nums);  
//...  
      auto a = [ptr = move(pNums)]()  
        {  
           // use ptr  
        };  
```  
  
### <a name="parameter-list"></a>Seznam parametrů  
 Kromě zachycením proměnné, může přijmout lambda vstupní parametry. Seznam parametrů (*lambda deklarátor* v standardní syntaxi) je volitelný a v většinu aspektů vypadá takto: seznam parametrů pro funkci.  
  
```cpp  
auto y = [] (int first, int second)  
{  
    return first + second;  
};  
  
```  
  
 V **C++ 14**, pokud je obecný typ parametru, můžete použít auto – klíčové slovo jako specifikátor typu. Tato hodnota informuje kompilátor vytvoří operátor volání funkce jako šablona. Každá instance automaticky v seznamu parametrů je ekvivalentní parametr typu distinct.  
  
```cpp  
auto y = [] (auto first, auto second)  
{  
    return first + second;  
};  
```  
  
 Výraz lambda může jako svůj argument přijmout jiný výraz lambda. Další informace najdete v tématu "Vysokého pořadí Lambda – výrazy" v tématu [příklady výrazů Lambda](../cpp/examples-of-lambda-expressions.md).  
  
 Vzhledem k tomu, že seznam parametr je volitelný, můžete vynechat závorky, pokud není předání argumentů výrazu lambda a jeho lambda deklarátor neobsahuje *specifikace výjimek*,  *Koncové typ návratové*, nebo `mutable`.  
  
### <a name="mutable-specification"></a>Proměnlivé specifikace  
 Operátor volání funkce lambda je obvykle const hodnotu, ale použití `mutable` to – klíčové slovo zruší. Nevytváří proměnlivé datové členy. Proměnlivé specifikace umožňují hlavní části výrazu lambda upravit proměnné, které jsou zachyceny hodnotou. Některé příklady později v tomto článku ukazují, jak používat `mutable`.  
  
### <a name="exception-specification"></a>Specifikace výjimek  
 Můžete použít `noexcept` specifikace výjimek indikující, že výrazu lambda nevyvolá výjimku jakékoli výjimky. Jak se běžné funkce Visual C++ compiler generuje upozornění [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) Pokud deklaruje výrazu lambda `noexcept` specifikace výjimek a text lambda vyvolá výjimku, jak je vidět tady:  
  
```cpp  
// throw_lambda_expression.cpp  
// compile with: /W4 /EHsc   
int main() // C4297 expected  
{  
   []() noexcept { throw 5; }();  
}  
```  
  
 Další informace najdete v tématu [specifikace výjimek (throw)](../cpp/exception-specifications-throw-cpp.md).  
  
### <a name="return-type"></a>Návratový typ  
 Návratový typ výrazu lambda je automaticky odvodit. Nemusíte používat [automaticky](../cpp/auto-cpp.md) – klíčové slovo nezadáte *koncové typ návratové*. *Koncové typ návratové* vypadá takto: část návratový typ běžné metody nebo funkce. Však návratový typ postupujte seznam parametrů, a musí obsahovat koncové návratový typ – klíčové slovo `->` před návratový typ.  
  
 Návratový typ součástí výrazu lambda můžete vynechat, pokud lambda text obsahuje pouze jeden příkaz return nebo výraz nevrací hodnotu. Pokud lambda obsahuje jeden příkaz return, kompilátor deduces návratový typ z typu návratový výraz. Jinak, kompilátor deduces návratový typ, který má být `void`. Zvažte následující příklad fragmentu kódu, který ilustruje tento princip.  
  
```cpp  
auto x1 = [](int i){ return i; }; // OK: return type is int  
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing   
                                  // return type from braced-init-list is not valid  
```  
  
 Výraz lambda může jako vrácenou hodnotu vytvořit jiný výraz lambda. Další informace najdete v tématu "Vysokého pořadí Lambda – výrazy" v [příklady výrazů Lambda](../cpp/examples-of-lambda-expressions.md).  
  
### <a name="lambda-body"></a>Hlavní část výrazu lambda  
 Text lambda (*složené příkaz* v standardní syntaxi) z lambda výraz může obsahovat všechno, co může obsahovat text běžné metody nebo funkce. Tělo běžné funkce a výrazu lambda přístup těchto druhů proměnné:  
  
-   Zaznamená proměnné z nadřazeného oboru, jak je popsáno výše.  
  
-   Parametry  
  
-   Místně deklarované proměnné  
  
-   Datové členy třídy, pokud deklarovaný uvnitř třídy a `this` zachycenou  
  
-   Všechny proměnné, která má úložiště se statickými trvání – například globální proměnné  
  
 Následující příklad obsahuje výraz lambda explicitně shromažďuje proměnnou `n` podle hodnoty a implicitně zaznamená proměnnou `m` odkazem:  
  
```cpp  
// captures_lambda_expression.cpp  
// compile with: /W4 /EHsc   
#include <iostream>  
using namespace std;  
  
int main()  
{  
   int m = 0;  
   int n = 0;  
   [&, n] (int a) mutable { m = ++n + a; }(4);  
   cout << m << endl << n << endl;  
}  
```  
  
```Output  
5  
0  
```  
  
 Protože proměnnou `n` zachycenou hodnotu, jeho hodnota zůstane `0` po zavolání výrazu lambda. `mutable` Umožňuje specifikaci `n` upravovat v rámci argument lambda.  
  
 Přestože výraz lambda může zachytit pouze proměnné, které mají automatickou dobu ukládání, můžete použít proměnné, které mají statickou dobu ukládání v hlavní části výrazu lambda. Následující příklad používá `generate` funkce a výrazu lambda o přiřazení hodnoty pro každý prvek v `vector` objektu. Výraz lambda změní statickou proměnnou a vygeneruje tak hodnotu dalšího prvku.  
  
```cpp  
void fillVector(vector<int>& v)  
{  
    // A local static variable.  
    static int nextValue = 1;  
  
    // The lambda expression that appears in the following call to  
    // the generate function modifies and uses the local static   
    // variable nextValue.  
    generate(v.begin(), v.end(), [] { return nextValue++; });   
    //WARNING: this is not thread-safe and is shown for illustration only  
}  
```  
  
 Další informace najdete v tématu [generovat](../standard-library/algorithm-functions.md#generate).  
  
 Následující příklad kódu používá funkci z předchozího příkladu a přidá příklad výrazu lambda, která používá algoritmus standardní knihovna C++ `generate_n`. Tento výraz lambda přiřadí k elementu `vector` objekt, který chcete součet předchozí dva elementy. `mutable` – Klíčové slovo slouží tak, aby text výrazu lambda můžete upravit jeho kopie externí proměnné `x` a `y`, která výrazu lambda zachycuje hodnotou. Protože výrazu lambda zaznamená původní proměnné `x` a `y` podle hodnoty, zůstanou jejich hodnoty `1` po provedení argument lambda.  
  
```cpp  
// compile with: /W4 /EHsc  
#include <algorithm>  
#include <iostream>  
#include <vector>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
void fillVector(vector<int>& v)  
{  
    // A local static variable.  
    static int nextValue = 1;  
  
    // The lambda expression that appears in the following call to  
    // the generate function modifies and uses the local static   
    // variable nextValue.  
    generate(v.begin(), v.end(), [] { return nextValue++; });  
    //WARNING: this is not thread-safe and is shown for illustration only  
}  
  
int main()  
{  
    // The number of elements in the vector.  
    const int elementCount = 9;  
  
    // Create a vector object with each element set to 1.  
    vector<int> v(elementCount, 1);  
  
    // These variables hold the previous two elements of the vector.  
    int x = 1;  
    int y = 1;  
  
    // Sets each element in the vector to the sum of the   
    // previous two elements.  
    generate_n(v.begin() + 2,  
        elementCount - 2,  
        [=]() mutable throw() -> int { // lambda is the 3rd parameter  
        // Generate current value.  
        int n = x + y;  
        // Update previous two values.  
        x = y;  
        y = n;  
        return n;  
    });  
    print("vector v after call to generate_n() with lambda: ", v);  
  
    // Print the local variables x and y.  
    // The values of x and y hold their initial values because   
    // they are captured by value.  
    cout << "x: " << x << " y: " << y << endl;  
  
    // Fill the vector with a sequence of numbers  
    fillVector(v);  
    print("vector v after 1st call to fillVector(): ", v);  
    // Fill the vector with the next sequence of numbers  
    fillVector(v);  
    print("vector v after 2nd call to fillVector(): ", v);  
}  
```  
  
```Output  
vector v after call to generate_n() with lambda: 1 1 2 3 5 8 13 21 34  
x: 1 y: 1  
vector v after 1st call to fillVector(): 1 2 3 4 5 6 7 8 9  
vector v after 2nd call to fillVector(): 10 11 12 13 14 15 16 17 18  
```  
  
 Další informace najdete v tématu [generate_n –](../standard-library/algorithm-functions.md#generate_n).  

## <a name="constexpr-lambda-expressions"></a>výrazy lambda constexpr
**Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): výrazu lambda může být deklarována jako `constexpr` nebo použít v konstantní výraz při inicializaci každý člen data to zaznamená nebo zavádí je povoleno v rámci konstantní výraz.  

```cpp
    int y = 32;
    auto answer = [y]() constexpr 
    {
        int x = 10;
        return y + x; 
    };

    constexpr int Increment(int n) 
    {
        return [n] { return n + 1; }();
    }

``` 
Lambda je implicitně `constexpr` Pokud svůj výsledek splňuje požadavky `constexpr` funkce:
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
Pokud lambda implicitně nebo explicitně `constexpr`, vytváří převod na ukazatel na funkci `constexpr` funkce:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="microsoft-specific"></a>Specifické pro společnost Microsoft  
 Lambdas nepodporuje následující běžné runtime (CLR) spravované entity jazyk: `ref class`, `ref struct`, `value class`, nebo `value struct`.  
  
 Pokud například používáte modifikátor specifické pro společnost Microsoft [__declspec](../cpp/declspec.md), můžete je do výrazu lambda ihned po `parameter-declaration-clause`– například:  
  
```cpp  
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };  
```  
  
 Pokud chcete zjistit, zda modifikátor lambdas podporuje, najdete v článku o něm v [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md) části dokumentace.  
  
 Kromě C ++ 11 standardní lambda funkcí Visual Studio podporuje bezstavové lambdas, které jsou omni převoditelné na ukazatele na funkce, které používají libovolný konvence volání.  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Objekty funkcí ve standardní knihovně C++](../standard-library/function-objects-in-the-stl.md)   
 [Volání funkce](../cpp/function-call-cpp.md)   
 [for_each –](../standard-library/algorithm-functions.md#for_each)
