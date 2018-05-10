---
title: Příklady výrazů Lambda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], examples
ms.assetid: 52506b15-0771-4190-a966-2f302049ca86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c83802dcc7382040d3b9f40bd0bbc2fe13d076f1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="examples-of-lambda-expressions"></a>Příklady výrazů lambda
Tento článek ukazuje, jak můžete použít výrazy lambda v programech. Přehled výrazů lambda v tématu [výrazy Lambda](../cpp/lambda-expressions-in-cpp.md). Další informace o struktuře výrazu lambda najdete v tématu [syntaxe výrazu Lambda](../cpp/lambda-expression-syntax.md).  
  
##  <a name="declaringLambdaExpressions"></a> Deklarování výrazy Lambda  
  
### <a name="example-1"></a>Příklad 1  
 Protože je zadán výraz lambda, můžete je přiřadit `auto` proměnné nebo [funkce](../standard-library/function-class.md) objektu, jak je vidět tady:  
  
### <a name="code"></a>Kód  
  
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
 Další informace najdete v tématu [automaticky](../cpp/auto-cpp.md), [funkce třída](../standard-library/function-class.md), a [volání funkce](../cpp/function-call-cpp.md).  
  
 I když lambda – výrazy jsou nejčastěji deklarované v těle funkce, je lze deklarovat kdekoli, bude možné inicializovat proměnné.  
  
### <a name="example-2"></a>Příklad 2  
 Kompilátor Visual C++ sváže lambda výraz s jeho zachycenými proměnnými při deklaraci výrazu místo při jeho volání. Následující příklad ukazuje výraz lambda, který zachycuje místní proměnné `i` tak, že hodnota a místní proměnné `j` odkazem. Protože zaznamená výrazu lambda `i` podle hodnoty, opětovné přiřazení `i` novější v programu nemá vliv na výsledek výrazu. Ale protože zaznamená výrazu lambda `j` odkazem opětovné přiřazení `j` ovlivnit výsledek výrazu.  
  
### <a name="code"></a>Kód  
  
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
  
 [[v tomto článku](#top)]  
  
##  <a name="callingLambdaExpressions"></a> Výrazy Lambda volání  
 Výraz lambda můžete volat ihned, jak je znázorněno v následujícím fragmentu kódu. Druhý fragment kódu ukazuje, jak mají být předány lambda jako argument standardní knihovna C++ algoritmy, jako `find_if`.  
  
### <a name="example-1"></a>Příklad 1  
 Tento příklad deklaruje výrazu lambda, která vrátí součet dvě celá čísla a volá výraz okamžitě s argumenty `5` a `4`:  
  
### <a name="code"></a>Kód  
  
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
 Tento příklad předá jako argument výraz lambda `find_if` funkce. Vrátí výrazu lambda `true` pokud její parametr je číslo sudé.  
  
### <a name="code"></a>Kód  
  
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
 Další informace o `find_if` funkce najdete v tématu [find_if –](../standard-library/algorithm-functions.md#find_if). Další informace o funkcích standardní knihovna C++, které provádějí běžné algoritmy najdete v tématu [ \<algoritmus >](../standard-library/algorithm.md).  
  
 [[v tomto článku](#top)]  
  
##  <a name="nestingLambdaExpressions"></a> Vnořování výrazů Lambda  
  
### <a name="example"></a>Příklad  
 Výraz lambda můžete vnořit do jiného tak, jak je ukázáno v následujícím příkladu. Vnitřní výraz lambda vynásobí svůj argument 2 a vrátí výsledek. Vnější výraz lambda volá vnitřní výraz lambda s argumentem a k výsledku přičte 3.  
  
### <a name="code"></a>Kód  
  
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
 V tomto příkladu `[](int y) { return y * 2; }` je výrazu vnořené lambda.  
  
 [[v tomto článku](#top)]  
  
##  <a name="higherOrderLambdaExpressions"></a> Funkce vyšší pořadí Lambda  
  
### <a name="example"></a>Příklad  
 Koncept podporují řadu programovacích jazyků *funkce vyšší pořadí.* Funkce vyššího řádu je výraz lambda, který bere další výraz lambda jako svůj argument nebo který vrací výraz lambda. Můžete použít [funkce](../standard-library/function-class.md) třída povolit výrazu lambda C++ se bude chovat, jako jsou funkce vyšší pořadí. Následující příklad ukazuje výraz lambda, který vrací `function` objekt a výraz lambda, která přijímá `function` objektu jako její argument.  
  
### <a name="code"></a>Kód  
  
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
  
 [[v tomto článku](#top)]  
  
##  <a name="methodLambdaExpressions"></a> Ve funkci pomocí výrazu Lambda  
  
### <a name="example"></a>Příklad  
 Výrazy lambda v těle funkce můžete použít. Výraz lambda mají přístup všechny funkce nebo data člena, který nadřazených funkce přistupovat. Můžete explicitně nebo implicitně zaznamenat `this` ukazatele pro poskytnutí přístupu k funkce a data členy nadřazených tříd.  
**Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): zachycení `this` podle hodnoty (`[*this]`) při argument lambda bude použita v asynchronní nebo paralelních operací kde může kód Spusťte po původní objekt ocitne mimo rozsah.
  
 Můžete použít `this` ukazatel explicitně ve funkci, jak je vidět tady:  
  
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
  
 Můžete získat `this` ukazatel implicitně:  
  
```  
void ApplyScale(const vector<int>& v) const  
{  
   for_each(v.begin(), v.end(),   
      [=](int n) { cout << n * _scale << endl; });  
}  
```  
  
 Následující příklad ukazuje `Scale` třídy, který zapouzdřuje hodnotu škálování.  
  
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
 `ApplyScale` Funkce používá k vytištění produktu hodnotou škálování a každý prvek v výrazu lambda `vector` objektu. Výraz lambda implicitně zaznamená `this` tak, aby měl přístup `_scale` člen.  
  
 [[v tomto článku](#top)]  
  
##  <a name="templateLambdaExpressions"></a> Lambda – výrazy pomocí šablony  
  
### <a name="example"></a>Příklad  
 Protože výrazy lambda mají typ, můžete je použít s šablonami jazyka C++. Následující příklad ukazuje `negate_all` a `print_all` funkce. `negate_all` Funkce se vztahuje unární `operator-` pro každý prvek v `vector` objektu. `print_all` Funkce vytiskne každý prvek v `vector` objektu do konzoly.  
  
### <a name="code"></a>Kód  
  
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
 Další informace o šablonách C++ najdete v tématu [šablony](../cpp/templates-cpp.md).  
  
 [[v tomto článku](#top)]  
  
##  <a name="ehLambdaExpressions"></a> Zpracování výjimek  
  
### <a name="example"></a>Příklad  
 Tělo výrazu lambda je v souladu s pravidly pro strukturované zpracování výjimek (SEH) i zpracování výjimek jazyka C++. V těle výrazu lambda můžete zpracovat vyvolanou výjimku nebo pozdržet zpracování výjimek pro nadřazený obor. Následující příklad používá `for_each` funkce a výrazu lambda k vyplnění `vector` hodnotami jiný objekt. Použije `try` / `catch` bloku pro zpracování Neplatný přístup k první vektoru.  
  
### <a name="code"></a>Kód  
  
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
 Další informace o zpracování výjimek najdete v tématu [zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md).  
  
 [[v tomto článku](#top)]  
  
##  <a name="managedLambdaExpressions"></a> Použití výrazů Lambda s spravované typy (C + +/ CLI)  
  
### <a name="example"></a>Příklad  
 Klauzule zachycení výrazu lambda nemůže obsahovat proměnnou se spravovaným typem. Můžete však předat argument se spravovaným typem do seznamu parametrů výrazu lambda. Následující příklad obsahuje výraz lambda, který zachycuje místní proměnné nespravované `ch` tak, že hodnota a trvá <xref:System.String?displayProperty=fullName> objektu jako její parametr.  
  
### <a name="code"></a>Kód  
  
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
 Výrazy lambda můžete použít také s knihovnou STL/CLR. Další informace najdete v tématu [referenční příručka knihovny STL/CLR](../dotnet/stl-clr-library-reference.md).  
  
> [!IMPORTANT]
>  Lambdas nejsou podporovány v těchto běžné runtime (CLR) spravovaných entit jazyk: `ref class`, `ref struct`, `value class`, a `value struct`.  
  
 [[v tomto článku](#top)]  
  
## <a name="see-also"></a>Viz také  
 [Lambda – výrazy](../cpp/lambda-expressions-in-cpp.md)   
 [Syntaxe výrazu lambda](../cpp/lambda-expression-syntax.md)   
 [Automaticky](../cpp/auto-cpp.md)   
 [Function – třída](../standard-library/function-class.md)   
 [find_if –](../standard-library/algorithm-functions.md#find_if)   
 [\<algoritmus >](../standard-library/algorithm.md)   
 [Volání funkce](../cpp/function-call-cpp.md)   
 [Šablony](../cpp/templates-cpp.md)   
 [Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)   
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)