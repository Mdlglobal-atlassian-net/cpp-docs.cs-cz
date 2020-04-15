---
title: Příklady výrazů lambda
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++], examples
ms.assetid: 52506b15-0771-4190-a966-2f302049ca86
ms.openlocfilehash: 106417519d00da1363f214492af9657712487088
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320343"
---
# <a name="examples-of-lambda-expressions"></a>Příklady výrazů lambda

Tento článek ukazuje, jak můžete použít výrazy lambda v programech. Přehled lambda výrazů, viz [Lambda výrazy](../cpp/lambda-expressions-in-cpp.md). Další informace o struktuře výrazu lambda naleznete v tématu [Syntaxe výrazu Lambda](../cpp/lambda-expression-syntax.md).

## <a name="declaring-lambda-expressions"></a><a name="declaringLambdaExpressions"></a>Deklarování výrazů Lambda

### <a name="example-1"></a>Příklad 1

Vzhledem k tomu, že je zadán výraz lambda, můžete jej přiřadit **k automatické** proměnné nebo objektu [funkce,](../standard-library/function-class.md) jak je znázorněno zde:

### <a name="code"></a>kód

```cpp
// declaring_lambda_expressions1.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{

    using namespace std;

    // Assign the lambda expression that adds two numbers to an auto variable.
    auto f1 = [](int x, int y) { return x + y; };

    cout << f1(2, 3) << endl;

    // Assign the same lambda expression to a function object.
    function<int(int, int)> f2 = [](int x, int y) { return x + y; };

    cout << f2(3, 4) << endl;
}
```

### <a name="output"></a>Výstup

```Output
5
7
```

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu auto](../cpp/auto-cpp.md), function [Class](../standard-library/function-class.md)a Function [Call](../cpp/function-call-cpp.md).

Přestože lambda výrazy jsou nejčastěji deklarovány v těle funkce, můžete deklarovat kdekoli, že můžete inicializovat proměnnou.

### <a name="example-2"></a>Příklad 2

Kompilátor Microsoft C++ váže výraz lambda na zachycené proměnné, když je výraz deklarován namísto při volání výrazu. Následující příklad ukazuje lambda výraz, který `i` zachycuje místní proměnnou `j` podle hodnoty a místní proměnnou odkazem. Vzhledem k tomu, `i` že výraz lambda `i` zachycuje podle hodnoty, opětovné přiřazení později v programu nemá vliv na výsledek výrazu. Protože však výraz lambda `j` zachytí odkazem, `j` přeřazení výrazu ovlivní výsledek výrazu.

### <a name="code"></a>kód

```cpp
// declaring_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   int i = 3;
   int j = 5;

   // The following lambda expression captures i by value and
   // j by reference.
   function<int (void)> f = [i, &j] { return i + j; };

   // Change the values of i and j.
   i = 22;
   j = 44;

   // Call f and print its result.
   cout << f() << endl;
}
```

### <a name="output"></a>Výstup

```Output
47
```

[[V tomto článku](#top)]

## <a name="calling-lambda-expressions"></a><a name="callingLambdaExpressions"></a>Volání lambda výrazů

Výraz lambda můžete volat ihned, jak je znázorněno v následujícím fragmentu kódu. Druhý úryvek ukazuje, jak předat lambda jako argument algoritmům standardní `find_if`knihovny jazyka C++, například .

### <a name="example-1"></a>Příklad 1

Tento příklad deklaruje výraz lambda, který vrací součet dvou celých `5` `4`čísel a okamžitě volá výraz s argumenty a :

### <a name="code"></a>kód

```cpp
// calling_lambda_expressions1.cpp
// compile with: /EHsc
#include <iostream>

int main()
{
   using namespace std;
   int n = [] (int x, int y) { return x + y; }(5, 4);
   cout << n << endl;
}
```

### <a name="output"></a>Výstup

```Output
9
```

### <a name="example-2"></a>Příklad 2

Tento příklad předá výraz lambda `find_if` jako argument funkci. Výraz lambda vrátí **hodnotu true,** pokud je jeho parametrsudem sudé číslo.

### <a name="code"></a>kód

```cpp
// calling_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    // Create a list of integers with a few initial elements.
    list<int> numbers;
    numbers.push_back(13);
    numbers.push_back(17);
    numbers.push_back(42);
    numbers.push_back(46);
    numbers.push_back(99);

    // Use the find_if function and a lambda expression to find the
    // first even number in the list.
    const list<int>::const_iterator result =
        find_if(numbers.begin(), numbers.end(),[](int n) { return (n % 2) == 0; });

    // Print the result.
    if (result != numbers.end()) {
        cout << "The first even number in the list is " << *result << "." << endl;
    } else {
        cout << "The list contains no even numbers." << endl;
    }
}
```

### <a name="output"></a>Výstup

```Output
The first even number in the list is 42.
```

### <a name="remarks"></a>Poznámky

Další informace o `find_if` funkci naleznete v [tématu find_if](../standard-library/algorithm-functions.md#find_if). Další informace o funkcích standardní knihovny jazyka C++, které provádějí běžné algoritmy, naleznete [ \<v tématu algoritmus>](../standard-library/algorithm.md).

[[V tomto článku](#top)]

## <a name="nesting-lambda-expressions"></a><a name="nestingLambdaExpressions"></a>Vnoření lambda výrazů

### <a name="example"></a>Příklad

Výraz lambda můžete vnořit do jiného tak, jak je ukázáno v následujícím příkladu. Vnitřní výraz lambda vynásobí svůj argument 2 a vrátí výsledek. Vnější výraz lambda volá vnitřní výraz lambda s argumentem a k výsledku přičte 3.

### <a name="code"></a>kód

```cpp
// nesting_lambda_expressions.cpp
// compile with: /EHsc /W4
#include <iostream>

int main()
{
    using namespace std;

    // The following lambda expression contains a nested lambda
    // expression.
    int timestwoplusthree = [](int x) { return [](int y) { return y * 2; }(x) + 3; }(5);

    // Print the result.
    cout << timestwoplusthree << endl;
}
```

### <a name="output"></a>Výstup

```Output
13
```

### <a name="remarks"></a>Poznámky

V tomto `[](int y) { return y * 2; }` příkladu je vnořený lambda výraz.

[[V tomto článku](#top)]

## <a name="higher-order-lambda-functions"></a><a name="higherOrderLambdaExpressions"></a>Funkce Lambda vyššího řádu

### <a name="example"></a>Příklad

Mnoho programovacích jazyků podporuje koncept *funkce vyššího řádu.* Funkce vyššího řádu je výraz lambda, který bere další výraz lambda jako svůj argument nebo který vrací výraz lambda. Třídu [funkce](../standard-library/function-class.md) můžete použít k povolení výrazu lambda jazyka C++, který se má chovat jako funkce vyššího řádu. Následující příklad ukazuje lambda výraz, `function` který vrací objekt a lambda výraz, který bere `function` objekt jako jeho argument.

### <a name="code"></a>kód

```cpp
// higher_order_lambda_expression.cpp
// compile with: /EHsc /W4
#include <iostream>
#include <functional>

int main()
{
    using namespace std;

    // The following code declares a lambda expression that returns
    // another lambda expression that adds two numbers.
    // The returned lambda expression captures parameter x by value.
    auto addtwointegers = [](int x) -> function<int(int)> {
        return [=](int y) { return x + y; };
    };

    // The following code declares a lambda expression that takes another
    // lambda expression as its argument.
    // The lambda expression applies the argument z to the function f
    // and multiplies by 2.
    auto higherorder = [](const function<int(int)>& f, int z) {
        return f(z) * 2;
    };

    // Call the lambda expression that is bound to higherorder.
    auto answer = higherorder(addtwointegers(7), 8);

    // Print the result, which is (7+8)*2.
    cout << answer << endl;
}
```

### <a name="output"></a>Výstup

```Output
30
```

[[V tomto článku](#top)]

## <a name="using-a-lambda-expression-in-a-function"></a><a name="methodLambdaExpressions"></a>Použití výrazu Lambda ve funkci

### <a name="example"></a>Příklad

Výrazy lambda můžete použít v těle funkce. Výraz lambda může přistupovat k libovolné funkci nebo datovému členu, ke kterému má přístup ohraničující funkce. Můžete explicitně nebo implicitně zachytit **tento** ukazatel poskytnout přístup k funkcím a datovým členům ohraničující třídy.
**Visual Studio 2017 verze 15.3 a novější** (k dispozici s [/std:c++17):](../build/reference/std-specify-language-standard-version.md)Zachyťte **to** podle hodnoty (`[*this]`), kdy lambda bude použita v asynchronní nebo paralelní operace, kde se může spustit kód po původní objekt přejde mimo rozsah.

Tento **ukazatel** můžete použít explicitně ve funkci, jak je znázorněno zde:

```cpp
// capture "this" by reference
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [this](int n) { cout << n * _scale << endl; });
}

// capture "this" by value (Visual Studio 2017 version 15.3 and later)
void ApplyScale2(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [*this](int n) { cout << n * _scale << endl; });
}
```

Tento **ukazatel** můžete také implicitně zachytit:

```cpp
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [=](int n) { cout << n * _scale << endl; });
}
```

Následující příklad ukazuje `Scale` třídu, která zapouzdřuje hodnotu měřítka.

```cpp
// function_lambda_expression.cpp
// compile with: /EHsc /W4
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

class Scale
{
public:
    // The constructor.
    explicit Scale(int scale) : _scale(scale) {}

    // Prints the product of each element in a vector object
    // and the scale value to the console.
    void ApplyScale(const vector<int>& v) const
    {
        for_each(v.begin(), v.end(), [=](int n) { cout << n * _scale << endl; });
    }

private:
    int _scale;
};

int main()
{
    vector<int> values;
    values.push_back(1);
    values.push_back(2);
    values.push_back(3);
    values.push_back(4);

    // Create a Scale object that scales elements by 3 and apply
    // it to the vector object. Does not modify the vector.
    Scale s(3);
    s.ApplyScale(values);
}
```

### <a name="output"></a>Výstup

```Output
3
6
9
12
```

### <a name="remarks"></a>Poznámky

Funkce `ApplyScale` používá výraz lambda k tisku součin hodnoty měřítka a každého prvku v objektu. `vector` Výraz lambda implicitně zachytí **to** tak, `_scale` aby přístup k členu.

[[V tomto článku](#top)]

## <a name="using-lambda-expressions-with-templates"></a><a name="templateLambdaExpressions"></a>Použití výrazů Lambda se šablonami

### <a name="example"></a>Příklad

Protože výrazy lambda mají typ, můžete je použít s šablonami jazyka C++. Následující příklad ukazuje `negate_all` `print_all` funkce a. Funkce `negate_all` použije unární **operátor-** pro každý `vector` prvek v objektu. Funkce `print_all` vytiskne každý `vector` prvek v objektu do konzoly.

### <a name="code"></a>kód

```cpp
// template_lambda_expression.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

// Negates each element in the vector object. Assumes signed data type.
template <typename T>
void negate_all(vector<T>& v)
{
    for_each(v.begin(), v.end(), [](T& n) { n = -n; });
}

// Prints to the console each element in the vector object.
template <typename T>
void print_all(const vector<T>& v)
{
    for_each(v.begin(), v.end(), [](const T& n) { cout << n << endl; });
}

int main()
{
    // Create a vector of signed integers with a few elements.
    vector<int> v;
    v.push_back(34);
    v.push_back(-43);
    v.push_back(56);

    print_all(v);
    negate_all(v);
    cout << "After negate_all():" << endl;
    print_all(v);
}
```

### <a name="output"></a>Výstup

```Output
34
-43
56
After negate_all():
-34
43
-56
```

### <a name="remarks"></a>Poznámky

Další informace o šablonách jazyka C++ naleznete v [tématu Templates](../cpp/templates-cpp.md).

[[V tomto článku](#top)]

## <a name="handling-exceptions"></a><a name="ehLambdaExpressions"></a>Zpracování výjimek

### <a name="example"></a>Příklad

Tělo výrazu lambda je v souladu s pravidly pro strukturované zpracování výjimek (SEH) i zpracování výjimek jazyka C++. V těle výrazu lambda můžete zpracovat vyvolanou výjimku nebo pozdržet zpracování výjimek pro nadřazený obor. Následující příklad používá **funkci for_each** a výraz lambda k vyplnění objektu `vector` hodnotami jiného. Používá **try**/**catch** bloku pro zpracování neplatný přístup k prvnímu vektoru.

### <a name="code"></a>kód

```cpp
// eh_lambda_expression.cpp
// compile with: /EHsc /W4
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

int main()
{
    // Create a vector that contains 3 elements.
    vector<int> elements(3);

    // Create another vector that contains index values.
    vector<int> indices(3);
    indices[0] = 0;
    indices[1] = -1; // This is not a valid subscript. It will trigger an exception.
    indices[2] = 2;

    // Use the values from the vector of index values to
    // fill the elements vector. This example uses a
    // try/catch block to handle invalid access to the
    // elements vector.
    try
    {
        for_each(indices.begin(), indices.end(), [&](int index) {
            elements.at(index) = index;
        });
    }
    catch (const out_of_range& e)
    {
        cerr << "Caught '" << e.what() << "'." << endl;
    };
}
```

### <a name="output"></a>Výstup

```Output
Caught 'invalid vector<T> subscript'.
```

### <a name="remarks"></a>Poznámky

Další informace o zpracování výjimek naleznete v [tématu Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md).

[[V tomto článku](#top)]

## <a name="using-lambda-expressions-with-managed-types-ccli"></a><a name="managedLambdaExpressions"></a>Použití výrazů Lambda se spravovanými typy (C++/CLI)

### <a name="example"></a>Příklad

Klauzule zachycení výrazu lambda nemůže obsahovat proměnnou se spravovaným typem. Můžete však předat argument se spravovaným typem do seznamu parametrů výrazu lambda. Následující příklad obsahuje výraz lambda, který zachycuje `ch` místní nespravovanou proměnnou podle hodnoty a bere <xref:System.String?displayProperty=fullName> objekt jako svůj parametr.

### <a name="code"></a>kód

```cpp
// managed_lambda_expression.cpp
// compile with: /clr
using namespace System;

int main()
{
    char ch = '!'; // a local unmanaged variable

    // The following lambda expression captures local variables
    // by value and takes a managed String object as its parameter.
    [=](String ^s) {
        Console::WriteLine(s + Convert::ToChar(ch));
    }("Hello");
}
```

### <a name="output"></a>Výstup

```Output
Hello!
```

### <a name="remarks"></a>Poznámky

Výrazy lambda můžete použít také s knihovnou STL/CLR. Další informace naleznete v tématu [STL/CLR Library Reference](../dotnet/stl-clr-library-reference.md).

> [!IMPORTANT]
> Lambdas nejsou podporovány v těchto spravovaných entitách modulu CLR (COMMON Language runtime): **ref class**, **ref struct**, **value class**a **value struct**.

[[V tomto článku](#top)]

## <a name="see-also"></a>Viz také

[Lambda výrazy](../cpp/lambda-expressions-in-cpp.md)<br/>
[Syntaxe výrazu Lambda](../cpp/lambda-expression-syntax.md)<br/>
[auto](../cpp/auto-cpp.md)<br/>
[třída funkce](../standard-library/function-class.md)<br/>
[find_if](../standard-library/algorithm-functions.md#find_if)<br/>
[\<algoritmus>](../standard-library/algorithm.md)<br/>
[Volání funkce](../cpp/function-call-cpp.md)<br/>
[Šablony](../cpp/templates-cpp.md)<br/>
[Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)
