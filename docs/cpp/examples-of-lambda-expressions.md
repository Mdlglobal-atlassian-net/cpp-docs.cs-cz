---
title: Příklady výrazů Lambda | Dokumentace Microsoftu
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
ms.openlocfilehash: d294eef323d96ddbfecad8f740826a5a038d7b4c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947533"
---
# <a name="examples-of-lambda-expressions"></a>Příklady výrazů lambda
Tento článek ukazuje, jak můžete použít výrazy lambda v programech. Přehled výrazů lambda naleznete v tématu [výrazy Lambda](../cpp/lambda-expressions-in-cpp.md). Další informace o struktuře výrazu lambda naleznete v tématu [Lambda Expression Syntax](../cpp/lambda-expression-syntax.md).  
  
##  <a name="declaringLambdaExpressions"></a> Deklarování výrazů Lambda  
  
### <a name="example-1"></a>Příklad 1  
 Protože je lambda výraz zadaný, můžete je přiřadit k **automaticky** proměnné nebo [funkce](../standard-library/function-class.md) objektu, jak je znázorněno zde:  
  
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
 Další informace najdete v tématu [automaticky](../cpp/auto-cpp.md), [funkce třídy](../standard-library/function-class.md), a [volání funkce](../cpp/function-call-cpp.md).  
  
 Přestože výrazy lambda jsou často deklarovány v těle funkce, můžete je deklarovat kdekoli, lze inicializovat proměnnou.  
  
### <a name="example-2"></a>Příklad 2  
 Kompilátor Visual C++ sváže lambda výraz s jeho zachycenými proměnnými při deklaraci výrazu místo při jeho volání. Následující příklad ukazuje výraz lambda, který explicitně zaznamenává místní proměnnou `i` podle hodnoty a místní proměnnou `j` podle odkazu. Vzhledem k tomu, že lambda výraz zachytí `i` podle hodnoty, přeřazení `i` dále v programu neovlivní výsledek výrazu. Ale vzhledem k tomu, že lambda výraz zachytí `j` podle odkazu, přeřazení `j` ovlivní výsledek výrazu.  
  
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
  
##  <a name="callingLambdaExpressions"></a> Volání výrazů Lambda  
 Výraz lambda můžete volat ihned, jak je znázorněno v následujícím fragmentu kódu. Druhý fragment kódu ukazuje, jak předat výraz lambda jako argument do algoritmů standardní knihovny C++, jako `find_if`.  
  
### <a name="example-1"></a>Příklad 1  
 Tento příklad deklaruje výraz lambda, který vrací součet dvou celých čísel a volá výraz s argumenty okamžitě `5` a `4`:  
  
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
 Tento příklad předává výraz lambda jako argument `find_if` funkce. Výraz lambda vrátí **true** li jeho parametr sudé číslo.  
  
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
 Další informace o `find_if` funkce naleznete v tématu [find_if](../standard-library/algorithm-functions.md#find_if). Další informace o funkce standardní knihovny C++, které provádějí běžné algoritmy, naleznete v tématu [ \<algoritmus >](../standard-library/algorithm.md).  
  
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
 V tomto příkladu `[](int y) { return y * 2; }` je vnořený výraz lambda.  
  
 [[v tomto článku](#top)]  
  
##  <a name="higherOrderLambdaExpressions"></a> Funkce Lambda vyššího řádu  
  
### <a name="example"></a>Příklad  
 Mnoho programovacích jazyků podporuje koncept *funkce vyššího řádu.* Funkce vyššího řádu je výraz lambda, který bere další výraz lambda jako svůj argument nebo který vrací výraz lambda. Můžete použít [funkce](../standard-library/function-class.md) třídy umožňující lambda výrazu C++ chovat, jako je funkce vyššího řádu. Následující příklad ukazuje výraz lambda, který vrátí `function` objektu a výraz lambda, který přijímá `function` objektu jako svůj argument.  
  
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
  
##  <a name="methodLambdaExpressions"></a> Použití výrazu Lambda ve funkci  
  
### <a name="example"></a>Příklad  
 Můžete použít výrazy lambda v těle funkce. Výraz lambda má přístup k funkci nebo datový člen, s přístupem k nadřazené funkce. Můžete explicitně nebo implicitně zachytit **to** ukazatel k poskytnutí přístupu k funkce a datovým členům ohraničující třídy.  
**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): zachycení **to** podle hodnoty (`[*this]`) Pokud výraz lambda se použijí v asynchronní nebo paralelních operací Pokud po může spustit kód na původní objekt dostane mimo rozsah.
  
 Můžete použít **to** ukazatel explicitně ve funkci, jak je znázorněno zde:  
  
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
  
 Můžete také zachytit **to** ukazatel implicitně:  
  
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
 `ApplyScale` Funkce používá výraz lambda k tisku výsledku jednotlivých prvků v a hodnotě měřítka `vector` objektu. Výraz lambda implicitně zachycuje **to** tak, aby měl přístup k `_scale` člena.  
  
 [[v tomto článku](#top)]  
  
##  <a name="templateLambdaExpressions"></a> Použití výrazů Lambda se šablonami  
  
### <a name="example"></a>Příklad  
 Protože výrazy lambda mají typ, můžete je použít s šablonami jazyka C++. Následující příklad ukazuje `negate_all` a `print_all` funkce. `negate_all` Funkce použije unární `operator-` na každý prvek `vector` objektu. `print_all` Funkce vypíše všechny prvky v `vector` objekt do konzoly.  
  
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
 Další informace o šablonách C++ naleznete v tématu [šablony](../cpp/templates-cpp.md).  
  
 [[v tomto článku](#top)]  
  
##  <a name="ehLambdaExpressions"></a> Zpracování výjimek  
  
### <a name="example"></a>Příklad  
 Tělo výrazu lambda je v souladu s pravidly pro strukturované zpracování výjimek (SEH) i zpracování výjimek jazyka C++. V těle výrazu lambda můžete zpracovat vyvolanou výjimku nebo pozdržet zpracování výjimek pro nadřazený obor. V následujícím příkladu **for_each** funkce a výraz lambda pro vyplnění `vector` objektu s hodnotami jiný. Použije **zkuste**/**catch** bloku ke zpracování neplatného přístupu k prvnímu vektoru.  
  
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
 Další informace o zpracování výjimek naleznete v tématu [zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md).  
  
 [[v tomto článku](#top)]  
  
##  <a name="managedLambdaExpressions"></a> Použití výrazů Lambda s spravované typy (C + +/ CLI)  
  
### <a name="example"></a>Příklad  
 Klauzule zachycení výrazu lambda nemůže obsahovat proměnnou se spravovaným typem. Můžete však předat argument se spravovaným typem do seznamu parametrů výrazu lambda. Následující příklad obsahuje výraz lambda, který zachytává místní nespravovanou proměnnou `ch` podle hodnoty a přijímá <xref:System.String?displayProperty=fullName> objektu jako svůj parametr.  
  
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
 Výrazy lambda můžete použít také s knihovnou STL/CLR. Další informace najdete v tématu [referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md).  
  
> [!IMPORTANT]
>  Výrazy lambda nejsou podporovány tyto běžné modulu runtime (CLR) spravované entity jazyka: **třídy ref class**, **ref struct**, **hodnotu třídy**, a **hodnotu struktury**.  
  
 [[v tomto článku](#top)]  
  
## <a name="see-also"></a>Viz také  
 [Výrazy lambda](../cpp/lambda-expressions-in-cpp.md)   
 [Syntaxe výrazů lambda](../cpp/lambda-expression-syntax.md)   
 [Automaticky](../cpp/auto-cpp.md)   
 [Function – třída](../standard-library/function-class.md)   
 [find_if](../standard-library/algorithm-functions.md#find_if)   
 [\<algoritmus >](../standard-library/algorithm.md)   
 [Volání funkce](../cpp/function-call-cpp.md)   
 [Šablony](../cpp/templates-cpp.md)   
 [Zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md)   
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)