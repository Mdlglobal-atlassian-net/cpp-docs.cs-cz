---
title: Výrazy lambda v jazyce C++
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
ms.openlocfilehash: e206ea8d67bb333065bf43f7f9c2dc373a5a5258
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857486"
---
# <a name="lambda-expressions-in-c"></a>Výrazy lambda v jazyce C++

V jazyce C++ 11 a novějším je výraz lambda, často označovaný jako *lambda*, pohodlný způsob definování anonymního objektu funkce ( *uzavření*) přímo v umístění, kde je vyvoláno nebo předáno jako argument funkci. Výrazy lambda se typicky používají k zapouzdření několika řádků kódu, které jsou předány algoritmům nebo asynchronním metodám. Tento článek definuje výrazy lambda, porovnává je s jinými programovacími technikami, popisuje jejich výhody a představuje základní příklad.

## <a name="related-topics"></a>Související témata

- [Lambda výrazy vs. objekty funkcí](lambda-expression-syntax.md)
- [Práce s výrazy lambda](examples-of-lambda-expressions.md)
- [výrazy lambda constexpr](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>Části výrazu lambda

Standard ISO C++ ukazuje jednoduchý lambda, který se předává jako třetí argument funkce `std::sort()`:

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

Tento obrázek ukazuje části výrazu lambda:

![Strukturální prvky výrazu lambda](../cpp/media/lambdaexpsyntax.png "Strukturální prvky výrazu lambda")

1. *klauzule zachycení* (označuje se také jako *představení výrazu lambda* ve C++ specifikaci)

1. *seznam parametrů* Volitelné. (Označuje se také jako *lambda deklarátor*)

1. *proměnlivá specifikace* Volitelné.

1. *Specifikace výjimek* Volitelné.

1. *koncová – návratový typ* Volitelné.

1. *tělo výrazu lambda*

### <a name="capture-clause"></a>Klauzule zachycení

Lambda může do svého těla začlenit nové proměnné (v **C++ 14**) a může také přistupovat k proměnným z okolního rozsahu nebo je z něj *zachytit*. Lambda začíná klauzulí zachycení (*výraz lambda – zavádí* ve standardní syntaxi), který určuje proměnné, které jsou zachyceny a zda je zachycení hodnotou nebo odkazem. Proměnné, které mají předponu ampersand (`&`), jsou k dispozici na základě odkazu a proměnných, které k nim nemají přístup pomocí hodnoty.

Prázdná klauzule zachycení, `[ ]`, označuje, že tělo výrazu lambda přistupuje k žádným proměnným v ohraničujícím oboru.

Můžete použít výchozí režim sběru (*zachytit – výchozí* ve standardní syntaxi) a určit, jak se mají zachytit vnější proměnné, na které se odkazuje ve výrazu lambda: `[&]` znamená, že všechny proměnné, na které odkazujete, jsou zachyceny odkazem a `[=]` znamená, že jsou zachyceny hodnotou. Můžete použít výchozí režim sběru dat a pak pro konkrétní proměnné zadat opačný režim. Například pokud tělo lambda přistupuje k externí proměnné `total` odkazem a externí proměnnou `factor` podle hodnoty, jsou následující klauzule zachycení ekvivalentní:

```cpp
[&total, factor]
[factor, &total]
[&, factor]
[factor, &]
[=, &total]
[&total, =]
```

Pouze proměnné, které jsou zmíněny v lambda, jsou zachyceny při použití zachycení – výchozí.

Pokud klauzule zachycení zahrnuje Capture-default `&`, nemůže mít `identifier` v `capture` této klauzule zachycení formu `& identifier`. Podobně platí, že pokud klauzule Capture zahrnuje Capture-default `=`, nemůže mít `= identifier`formuláře žádný `capture` této klauzule zachycení. Identifikátor nebo **to** nemůže být v klauzuli Capture uveden více než jednou. Následující fragment kódu dokládá několik příkladů.

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

Záznam následovaný třemi tečkami je rozšíření balíčku, jak je znázorněno v tomto příkladu [šablony variadické](../cpp/ellipses-and-variadic-templates.md) :

```cpp
template<class... Args>
void f(Args... args) {
    auto x = [args...] { return g(args...); };
    x();
}
```

Chcete-li použít výrazy lambda v těle metody třídy, předejte **Tento** ukazatel na klauzuli Capture pro poskytnutí přístupu k metodám a datovým členům ohraničující třídy.

**Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): **Tento** ukazatel může být zachycen podle hodnoty zadáním `*this` v klauzuli Capture. Capture podle hodnoty znamená, že celé *uzavření*, což je objekt anonymní funkce, který encapulates lambda výraz, je zkopírováno do všech volání webu, kde je lambda vyvolána. Zachycení podle hodnoty je užitečné, pokud lambda spustí paralelní nebo asynchronní operace, zejména u některých hardwarových architektur, jako je například NUMA.

Příklad, který ukazuje, jak používat lambda výrazy s metodami třídy naleznete v tématu "Příklad: použití výrazu lambda v metodě" v [příkladech výrazů lambda](../cpp/examples-of-lambda-expressions.md).

Při použití klauzule Capture doporučujeme, abyste zachovali tyto body, zejména při použití výrazů lambda s multithreadingem:

- Zachycení odkazů lze použít pro úpravu proměnných mimo, ale zachycení hodnoty nemohou. (**proměnlivé** umožňuje upravovat kopie, ale ne originály.)

- Zachycení odkazů odráží aktualizace proměnných mimo, ale zachycení hodnot ne.

- Zachycení odkazů zavádí závislost životnosti, ale zachycení hodnot nemají žádné závislosti životního cyklu. To je obzvláště důležité při asynchronním spuštění lambda. Pokud zachytíte místní odkaz v asynchronním výrazu lambda, může být tato lokální chyba způsobena časem spuštění lambda a výsledkem je narušení přístupu v době běhu.

### <a name="generalized-capture-c-14"></a>Generalizovaná zachycení (C++ 14)

V C++ 14 můžete zavést a inicializovat nové proměnné v klauzuli Capture, aniž by tyto proměnné existovaly v ohraničujícím oboru funkce lambda. Inicializace může být vyjádřena libovolným libovolným výrazem; Typ nové proměnné je odvozen z typu vytvořeného výrazem. Jednou z výhod této funkce je, že v C++ 14 můžete zachytit proměnné jenom pro přesun (například std:: unique_ptr) z okolního oboru a použít je ve výrazu lambda.

```cpp
pNums = make_unique<vector<int>>(nums);
//...
      auto a = [ptr = move(pNums)]()
        {
           // use ptr
        };
```

### <a name="parameter-list"></a>Seznam parametrů

Kromě zachycení proměnných může lambda akceptovat vstupní parametry. Seznam parametrů (*lambda deklarátor* ve standardní syntaxi) je volitelný a ve většině aspektů se podobá seznamu parametrů funkce.

```cpp
auto y = [] (int first, int second)
{
    return first + second;
};
```

V  **C++ 14**, pokud je typ parametru obecný, můžete použít klíčové slovo auto jako specifikátor typu. Říká kompilátoru, aby vytvořil operátor volání funkce jako šablonu. Každá instance třídy auto v seznamu parametrů je ekvivalentní parametru samostatného typu.

```cpp
auto y = [] (auto first, auto second)
{
    return first + second;
};
```

Výraz lambda může jako svůj argument přijmout jiný výraz lambda. Další informace naleznete v tématu "výrazy lambda s vyšším pořadím" v tématu [Příklady výrazů lambda](../cpp/examples-of-lambda-expressions.md).

Vzhledem k tomu, že seznam parametrů je nepovinný, můžete vynechat prázdné závorky, pokud nepředáte argumenty výrazu lambda a jeho výraz lambda-deklarátor neobsahuje *specifikaci výjimek*, *koncového-návratového typu*nebo **mutable**.

### <a name="mutable-specification"></a>Proměnlivé specifikace

Obvykle operátor volání funkce lambda je const podle hodnoty, ale použití klíčového slova **mutable** zruší. Nevytváří proměnlivé datové členy. Proměnlivé specifikace umožňují hlavní části výrazu lambda upravit proměnné, které jsou zachyceny hodnotou. Některé příklady dále v tomto článku ukazují, jak používat **mutable**.

### <a name="exception-specification"></a>Specifikace výjimek

Můžete použít specifikaci pro výjimku `noexcept` pro označení, že výraz lambda nevyvolá žádné výjimky. Stejně jako u běžných funkcí kompilátor společnosti C++ Microsoft generuje upozornění [C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md) , pokud výraz lambda deklaruje specifikaci výjimky `noexcept` a tělo lambda vyvolá výjimku, jak je znázorněno zde:

```cpp
// throw_lambda_expression.cpp
// compile with: /W4 /EHsc
int main() // C4297 expected
{
   []() noexcept { throw 5; }();
}
```

Další informace naleznete v tématu [Specifikace výjimek (throw)](../cpp/exception-specifications-throw-cpp.md).

### <a name="return-type"></a>Návratový typ

Návratový typ výrazu lambda je automaticky odvozený. Klíčové slovo [auto](../cpp/auto-cpp.md) nemusíte používat, pokud nezadáte *koncový návratový typ*. *Koncová návratový typ* se podobá částce návratového typu běžné metody nebo funkce. Návratový typ se však musí dodržet seznam parametrů a před návratovým typem musí být zahrnuté klíčové slovo koncového typu `->`.

Část návratového typu výrazu lambda lze vynechat, pokud tělo lambda obsahuje pouze jeden návratový příkaz nebo výraz nevrací hodnotu. Pokud tělo lambda obsahuje jeden návratový příkaz, kompilátor odvodit návratový typ z typu návratového výrazu. V opačném případě kompilátor odvodí návratový typ jako **void**. Zvažte následující příklad fragmentu kódu, který ilustruje tento princip.

```cpp
auto x1 = [](int i){ return i; }; // OK: return type is int
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing
                                  // return type from braced-init-list is not valid
```

Výraz lambda může jako vrácenou hodnotu vytvořit jiný výraz lambda. Další informace naleznete v tématu "výrazy lambda s vyšším pořadím" v [příkladech výrazů lambda](../cpp/examples-of-lambda-expressions.md).

### <a name="lambda-body"></a>Hlavní část výrazu lambda

Tělo lambda (*složený příkaz* ve standardní syntaxi) výrazu lambda může obsahovat cokoli, co může obsahovat tělo běžné metody nebo funkce. Tělo běžné funkce a výrazu lambda má přístup k těmto typům proměnných:

- Zachycené proměnné z ohraničujícího oboru, jak je popsáno výše.

- Parametry

- Místně deklarované proměnné

- Datové členy třídy, pokud jsou deklarovány uvnitř třídy **a jsou** zachyceny

- Jakákoli proměnná, která má statickou dobu úložiště, například globální proměnné

Následující příklad obsahuje výraz lambda, který explicitně zaznamenává proměnnou `n` podle hodnoty a implicitně zaznamenává proměnnou `m` podle odkazu:

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

Vzhledem k tomu, že je proměnná `n` zachycena hodnotou, její hodnotou je nadále `0` i po volání výrazu lambda. **Proměnlivá** specifikace umožňuje změnit `n` v rámci výrazu lambda.

Přestože výraz lambda může zachytit pouze proměnné, které mají automatickou dobu ukládání, můžete použít proměnné, které mají statickou dobu ukládání v hlavní části výrazu lambda. V následujícím příkladu se využívá funkce `generate` a výraz lambda pro přiřazení hodnoty ke každému prvku v objektu `vector`. Výraz lambda změní statickou proměnnou a vygeneruje tak hodnotu dalšího prvku.

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

Další informace naleznete v tématu [Generate](../standard-library/algorithm-functions.md#generate).

Následující příklad kódu používá funkci z předchozího příkladu a přidá příklad výrazu lambda, který používá C++ standardní algoritmus knihovny `generate_n`. Tento výraz lambda přiřadí prvek objektu `vector` k součtu předchozích dvou prvků. Klíčové slovo **mutable** je použito, aby tělo výrazu lambda mohl upravovat své kopie externích proměnných `x` a `y`, který výraz lambda zachycuje podle hodnoty. Vzhledem k tomu, že výraz lambda zachytí původní proměnné `x` a `y` podle hodnoty, jejich hodnoty zůstávají `1` po provedení výrazu lambda.

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

## <a name="constexpr-lambda-expressions"></a>constexpr – výrazy lambda

**Visual Studio 2017 verze 15,3 a novější** (k dispozici v [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): výraz lambda může být deklarován jako `constexpr` nebo použit v konstantním výrazu, pokud je v rámci konstantního výrazu povolena inicializace každého datového člena, který zachycuje nebo zavádí.

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

Výraz lambda je implicitně `constexpr`, pokud výsledek splňuje požadavky `constexpr` funkce:

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Pokud je lambda implicitně nebo explicitně `constexpr`, převod na ukazatel na funkci vytvoří `constexpr` funkci:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="microsoft-specific"></a>specifické pro společnost Microsoft

Výrazy lambda nejsou podporované v následujících spravovaných entitách modulu CLR (Common Language Runtime): **ref class**, **ref struct**, **Value Class**nebo **value struct**.

Pokud používáte modifikátor specifický od společnosti Microsoft, například [__declspec](../cpp/declspec.md), můžete jej vložit do výrazu lambda ihned po `parameter-declaration-clause`– například:

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

Chcete-li určit, zda je modifikátor podporován pomocí výrazů lambda, přečtěte si článek v části věnované [modifikátorům specifickým pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md) v dokumentaci.

Kromě standardních funkcí lambda v jazyce C++ 11 podporuje Visual Studio nestavové výrazy lambda, které jsou převoditelné na ukazatele funkcí, které používají libovolné konvence volání.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Objekty funkcí ve standardní knihovně C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Volání funkcí](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
