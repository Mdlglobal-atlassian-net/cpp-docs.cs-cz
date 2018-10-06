---
title: Výrazy lambda v jazyce C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7a9915c7ca6b9d2c3f01cea12e2979ef256f904
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821176"
---
# <a name="lambda-expressions-in-c"></a>Výrazy lambda v jazyce C++

V C ++ 11 a novějším výraz lambda – často označované jako *lambda*– nabízí pohodlný způsob definice objektu anonymní funkce ( *uzavření*) přímo na místě, kde je vyvolána nebo předat jako argument na funkci. Výrazy lambda se obvykle používají k zapouzdření pár řádků kódu, které se předá algoritmy nebo asynchronní metody. Tento článek definuje výrazy lambda, porovnává je s jinými programovacími technikami, popisuje jejich výhody a představuje základní příklad.

## <a name="related-topics"></a>Související témata

- [Výrazy lambda oproti objektům funkcí](lambda-expression-syntax.md)
- [Práce s výrazy lambda](examples-of-lambda-expressions.md)
- [výrazy lambda constexpr.](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Části výrazu Lambda

Norma ISO C++ ukazuje jednoduchý výraz lambda, který je předán jako třetí argument `std::sort()` funkce:

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

Tento obrázek ukazuje část výrazu lambda:

![Konstrukční prvky výrazu lambda](../cpp/media/lambdaexpsyntax.png "LambdaExpSyntax")

1. *klauzule sběru* (označované také jako *lambda-introducer* ve specifikaci jazyka C++.)

1. *Seznam parametrů* volitelné. (Označované také jako *lambda declarator*)

1. *proměnlivé specifikace* volitelné.

1. *Specifikace výjimky* volitelné.

1. *trailing-return-type* volitelné.

1. *hlavní část výrazu lambda*)

### <a name="capture-clause"></a>Klauzule zachycení

Výraz lambda můžete zavést nové proměnné v jeho textu (v **C ++ 14**) a může taky přístup, nebo *zachycení*, proměnné z rozsah obklopujícím rozsahem. Výraz lambda začíná klauzule zachycení (*lambda-introducer* ve standardní syntaxe), která určuje, které proměnné jsou zachyceny a určuje, zda zachytávání je hodnotou nebo odkazem. Proměnné, které mají ampersand (`&`) je přistupováno podle odkazu a proměnné, které ji nemají k nim přístup podle hodnoty.

Klauzule prázdného záznamu `[ ]`, označuje, že hlavní část výrazu lambda nemá přístup k žádné proměnné v ohraničujícím oboru.

Můžete použít výchozí režim zachycení (*capture-default* ve standardní syntaxe) k označení jak zachytit všechny vnější proměnné, které jsou uvedeny v lambdě: `[&]` znamená, že všechny proměnné, které odkazují na jsou zachyceny na základě odkaz, a `[=]` znamená, že jsou zachyceny hodnotou. Můžete použít výchozí režim sběru dat a pak zadejte opačné režimu explicitně pro určité proměnné. Například, pokud hlavní část výrazu lambda přistupuje k externí proměnné `total` podle odkazu a k externí proměnné `factor` podle hodnoty, pak jsou následující odchytávací klauzule rovnocenné:

```cpp
[&total, factor]
[factor, &total]
[&, factor]
[factor, &]
[=, &total]
[&total, =]
```

Pouze proměnné, které jsou uvedeny v lambdě, jsou zachyceny při použití výchozí zachycení.

Pokud klauzule zachycení obsahuje výchozí zachycení `&`, neuvidí žádný `identifier` v `capture` klauzule zachycení může mít formuláře `& identifier`. Podobně pokud klauzule zachycení obsahuje výchozí zachycení `=`, neuvidí žádný `capture` klauzule zachycení může mít formuláře `= identifier`. Identifikátor nebo **to** nelze v klauzuli zachycení objevit více než jednou. Následující fragment kódu dokládá několik příkladů.

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

Zachycení následované třemi tečkami je rozšiřující sada, jak je znázorněno v tomto [šablony variadických funkcí](../cpp/ellipses-and-variadic-templates.md) příkladu:

```cpp
template<class... Args>
void f(Args... args) {
    auto x = [args...] { return g(args...); };
    x();
}
```

Chcete-li použít výrazy lambda v těle metody třídy, předejte **to** ukazatele klauzuli zachycení zajistíte přístup k metodám a datovým členům ohraničující třídy.

**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): **to** ukazatele může být zachyceno hodnotou zadáním `*this` v klauzuli zachycení. Zaznamenávání hodnota znamená, že celý *uzavření*, které je objekt anonymní funkce tohoto encapulates výraz lambda, je zkopírován do každé volání webu, kde vyvolání lambda. Zachycení podle hodnoty je užitečné, když bude výraz lambda vykonán v paralelní a asynchronní operace, zejména u určité architektury hardwaru, jako je například technologie NUMA.

Příklad, který ukazuje, jak použít výrazy lambda s metodami tříd naleznete v části "Příklad: Lambda výrazu v metodou" v [Examples of Lambda Expressions](../cpp/examples-of-lambda-expressions.md).

Použijete-li klauzuli zachycení, doporučujeme ponechat tyto body na paměti, zejména při použití lambd s multithreading:

- Zachycení odkazu lze použít k úpravám proměnných mimo, ale nikoli zachycení hodnoty. (**proměnlivé** umožňuje kopie má být upraven, ale ne originálů.)

- Zachycení odkazu odrážejí aktualizace proměnných mimo, ale zachycení hodnoty tomu tak není.

- Zachycení odkazu zavádějí závislost životnosti, ale zachycení hodnoty nemají žádné závislosti životnosti. To je obzvláště důležité, pokud výraz lambda běží asynchronně. Pokud zachycení místní odkazem v asynchronní lambdy této místní budou velmi pravděpodobně znovu podle času spuštění výrazu lambda, což vede k porušení přístupu v době běhu.

### <a name="generalized-capture-c-14"></a>Zachycení generalizovaného (C++ 14)

V C ++ 14 můžete zavést a existují nové inicializace proměnné v klauzuli zachycení, aniž byste museli mít tyto proměnné v ohraničujícím oboru funkce lambda. Inicializace může být vyjádřený jako libovolný libovolný výraz; Typ nové proměnné je odvozen z typu vytvářených výraz. Jednou z výhod této funkce je, že v C ++ 14 můžete zachytit jenom pro přesun proměnné (jako je například std::unique_ptr) z rozsah obklopujícím rozsahem a jejich použití ve výrazu lambda.

```cpp
pNums = make_unique<vector<int>>(nums);
//...
      auto a = [ptr = move(pNums)]()
        {
           // use ptr
        };
```

### <a name="parameter-list"></a>Seznam parametrů

Kromě zachytávání proměnné, výraz lambda může přijmout vstupní parametry. Seznam parametrů (*lambda declarator* ve standardní syntaxe) je volitelný a v většinu aspektů podobá seznamu parametrů pro funkci.

```cpp
auto y = [] (int first, int second)
{
    return first + second;
};
```

V **C++ 14**, pokud typ parametru je obecný, můžete použít klíčové slovo auto jako specifikátoru typu. To instruuje kompilátor, aby vytvořit operátor volání funkce jako šablona. Každá instance automaticky v seznamu parametrů je ekvivalentní odlišný typ parametru.

```cpp
auto y = [] (auto first, auto second)
{
    return first + second;
};
```

Výraz lambda může jako svůj argument přijmout jiný výraz lambda. Další informace najdete v tématu "Výrazy Lambda vyššího řádu" v tématu [Examples of Lambda Expressions](../cpp/examples-of-lambda-expressions.md).

Seznam parametrů je nepovinný, můžete vynechat prázdné závorky, pokud nepředáte argumenty výrazu lambda a jeho lambda-declarator neobsahuje *specifikace výjimky*,  *trailing-return-type*, nebo **proměnlivé**.

### <a name="mutable-specification"></a>Proměnlivé specifikace

Obvykle je operátor volání funkce lambda podle hodnoty const, ale využití **proměnlivé** – klíčové slovo toto ruší. Nevytváří proměnlivé datové členy. Proměnlivé specifikace umožňují hlavní části výrazu lambda upravit proměnné, které jsou zachyceny hodnotou. Některé příklady dále v tomto článku ukazují, jak používat **proměnlivé**.

### <a name="exception-specification"></a>Specifikace výjimek

Můžete použít `noexcept` specifikace výjimky označující, že výraz lambda nevyvolá žádné výjimky. Jako u běžných funkcí kompilátor Visual C++ generuje upozornění [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) Pokud výraz lambda deklaruje `noexcept` specifikace výjimek a hlavní část výrazu lambda vyvolá výjimku, jak je znázorněno zde:

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

Návratový typ výrazu lambda je automaticky odvozen. Není nutné použít [automaticky](../cpp/auto-cpp.md) – klíčové slovo-li *trailing-return-type*. *Trailing-return-type* se podobá části návratového typu obyčejné metody nebo funkce. Ale návratový typ musí odpovídat seznamu parametrů a musí obsahovat klíčové slovo trailing-return-type `->` před návratovým typem.

Část návratového typu výrazu lambda lze vynechat, pokud hlavní část lambdy obsahuje jenom jeden návratový příkaz nebo výraz nevrací hodnotu. Pokud hlavní část lambdy obsahuje jeden příkaz return, kompilátor odvodí návratový typ od typu vráceného výrazu. V opačném případě kompilátor odvodí návratový typ jako **void**. Zvažte následující příklad fragmentu kódu, který ilustruje tento princip.

```cpp
auto x1 = [](int i){ return i; }; // OK: return type is int
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing
                                  // return type from braced-init-list is not valid
```

Výraz lambda může jako vrácenou hodnotu vytvořit jiný výraz lambda. Další informace najdete v tématu "Výrazy Lambda vyššího řádu" [Examples of Lambda Expressions](../cpp/examples-of-lambda-expressions.md).

### <a name="lambda-body"></a>Hlavní část výrazu lambda

Hlavní část výrazu lambda (*compound-statement* ve standardní syntaxe) výrazu lambda výraz může obsahovat cokoli, co může obsahovat hlavní část běžné metody nebo funkce. Tělo běžné funkce i výraz lambda mají přístup k těmto typům proměnných:

- Zachycené proměnné z nadřazeného oboru, jak je popsáno výše.

- Parametry

- Místně deklarované proměnné

- Datové členy třídy, při deklarované uvnitř třídy a **to** zachycena

- Jakákoli proměnná, která má statickou dobu úložiště – například globální proměnné

Následující příklad obsahuje výraz lambda, který explicitně zaznamenává proměnnou `n` podle hodnoty a implicitně zachycuje proměnnou `m` podle odkazu:

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

Protože proměnné `n` zachycena hodnotou, její hodnotou je nadále `0` po volání výrazu lambda. **Proměnlivé** umožňuje specifikaci `n` má být upraven v rámci výrazu lambda.

Přestože výraz lambda může zachytit pouze proměnné, které mají automatickou dobu ukládání, můžete použít proměnné, které mají statickou dobu ukládání v hlavní části výrazu lambda. V následujícím příkladu `generate` funkce a výraz lambda pro přiřazení hodnoty ke každému prvku v `vector` objektu. Výraz lambda změní statickou proměnnou a vygeneruje tak hodnotu dalšího prvku.

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

Následující příklad kódu používá funkci z předchozího příkladu a přidá příklad výraz lambda, který používá algoritmus standardní knihovny C++ `generate_n`. Tento výraz lambda přiřazuje prvek objektu `vector` objekt součtu předchozích dvou prvků. **Proměnlivé** – klíčové slovo se používá tak, aby hlavní část výrazu lambda můžete upravit své kopie externích proměnných `x` a `y`, kterými zachycuje výraz lambda podle hodnoty. Vzhledem k tomu, že výraz lambda zachytí původní proměnné `x` a `y` podle hodnoty, jejich hodnoty zůstávají `1` po spuštění lambdy.

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

Další informace najdete v tématu [generate_n](../standard-library/algorithm-functions.md#generate_n).

## <a name="constexpr-lambda-expressions"></a>výrazy lambda constexpr.

**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): výraz lambda může být deklarována jako `constexpr` nebo použít v konstantním výrazu při inicializaci každý datový člen se zaznamená nebo zavádí je povolený v konstantním výrazu.

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

Výraz lambda je implicitně `constexpr` Pokud výsledek splňuje požadavky `constexpr` funkce:

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Pokud je výraz lambda implicitně nebo explicitně `constexpr`, vytvoří převod na ukazatel na funkci `constexpr` funkce:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="microsoft-specific"></a>Specifické pro společnost Microsoft

Výrazy lambda nejsou podporovány následující běžné entity modulu runtime (CLR) spravované jazyka: **třídy ref class**, **ref struct**, **hodnotu třídy**, nebo **hodnotu – struktura** .

Pokud použijete modifikátor specifické pro společnost Microsoft, jako [__declspec](../cpp/declspec.md), můžete ho vložit do výrazu lambda ihned po `parameter-declaration-clause`– například:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Pokud chcete zjistit, jestli je modifikátor nepodporuje výrazy lambda, najdete v článku o řezu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md) část dokumentace.

Visual Studio podporuje kromě funkce C ++ 11 Standard lambda, jsou výrazy lambda, které jsou omni převoditelné na ukazatele funkcí, které používají libovolné konvence volání.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Objekty funkcí ve standardní knihovně C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Volání funkcí](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)