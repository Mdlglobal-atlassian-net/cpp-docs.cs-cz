---
title: "&lt;funkční&gt; funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- functional/std::bind
- xfunctional/std::bind1st
- xfunctional/std::bind2nd
- xfunctional/std::bit_and
- xfunctional/std::bit_not
- xfunctional/std::bit_or
- xfunctional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- xfunctional/std::mem_fn
- xfunctional/std::mem_fun_ref
- xfunctional/std::not1
- xfunctional/std::not2
- xfunctional/std::ptr_fun
- functional/std::ref
- functional/std::swap
dev_langs:
- C++
helpviewer_keywords:
- std::bind [C++]
- std::bind1st
- std::bind2nd
- std::bit_and [C++]
- std::bit_not [C++]
- std::bit_or [C++]
- std::bit_xor [C++]
- std::cref [C++]
ms.assetid: c34d0b45-50a7-447a-9368-2210d06339a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0401f97cbaa30cd0489227008195568748d24b80
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltfunctionalgt-functions"></a>&lt;funkční&gt; funkce
||||  
|-|-|-|  
|[Vazby](#bind)|[bind1st –](#bind1st)|[bind2nd –](#bind2nd)|  
|[bit_and](#bit_and)|[bit_not](#bit_not)|[bit_or](#bit_or)|  
|[bit_xor](#bit_xor)|[cref](#cref)|[mem_fn](#mem_fn)|  
|[mem_fun](#mem_fun)|[mem_fun_ref](#mem_fun_ref)|[not1 –](#not1)|  
|[not2](#not2)|[ptr_fun](#ptr_fun)|[ref](#ref)|  
|[swap](#swap)|  
  
##  <a name="bind"></a>  Vazby  
 Naváže argumenty na volatelný objekt.  
  
```  
template <class Fty, class T1, class T2, ..., class TN>  
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);

template <class Ret, class Fty, class T1, class T2, ..., class TN>  
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);
```  
  
### <a name="parameters"></a>Parametry  
 `Fty`  
 Typ objektu k volání.  
  
 `TN`  
 Typ n. volání argument.  
  
 `fn`  
 Objekt, který se má volat.  
  
 `tN`  
 N-tou volání argument.  
  
### <a name="remarks"></a>Poznámky  
 Typy `Fty, T1, T2, ..., TN` musí být kopie zkonstruovatelný, a `INVOKE(fn, t1, ..., tN)` musí být platný výraz pro některé hodnoty `w1, w2, ..., wN`.  
  
 Vrátí první funkce šablony volání předávání obálku `g` s typem slabé výsledku. Účinek `g(u1, u2, ..., uM)` je `INVOKE(f, v1, v2, ..., vN, ` [result_of](../standard-library/result-of-class.md)`<Fty cv (V1, V2, ..., VN)>::type)`, kde `cv` je odchylka nákladů kvalifikátory z `g` a hodnot a typy Vázané argumenty `v1, v2, ..., vN` jsou určeny jako níže uvedené. Použít k vytvoření vazby argumenty s objektu s objekt se seznamem argumentů šité na míru.  
  
 Druhá šablona funkce vrátí hodnotu předávání volání obálku `g` s typem vnořené `result_type` tedy synonymum pro `Ret`. Účinek `g(u1, u2, ..., uM)` je `INVOKE(f, v1, v2, ..., vN, Ret)`, kde `cv` je odchylka nákladů kvalifikátory z `g` a hodnot a typy Vázané argumenty `v1, v2, ..., vN` jsou určené uvedeného níže. Použít pro vazbu s objektu s objekt s seznam šité na míru argumentů a zadaný návratový typ argumenty.  
  
 Hodnoty vázané argumentů `v1, v2, ..., vN` a jejich odpovídající typy `V1, V2, ..., VN` závisí na typu odpovídající argumentu `ti` typu `Ti` ve volání `bind` a odchylka nákladů kvalifikátory `cv` z volání obálku `g` následujícím způsobem:  
  
 Pokud `ti` je typu `reference_wrapper<T>` argument `vi` je `ti.get()` a její typ `Vi` je `T&`;  
  
 Pokud hodnota `std::is_bind_expression<Ti>::value` je `true` argument `vi` je `ti(u1, u2, ..., uM)` a její typ `Vi` je `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`;  
  
 Pokud hodnota `j` z `std::is_placeholder<Ti>::value` je argument není nula `vi` je `uj` a její typ `Vi` je `Uj&`;  
  
 v opačném případě argument `vi` je `ti` a její typ `Vi` je `Ti` `cv` `&`.  
  
 Například danou funkci `f(int, int)` výraz `bind(f, _1, 0)` vrátí předávání volání obálku `cw` tak, aby `cw(x)` volání `f(x, 0)`. Výraz `bind(f, 0, _1)` vrátí předávání volání obálku `cw` tak, aby `cw(x)` volání `f(0, x)`.  
  
 Počet argumentů je volání `bind` kromě argument `fn` musí být roven počtu argumenty, které lze předat objekt s `fn`. Proto `bind(cos, 1.0)` je správný a obě `bind(cos)` a `bind(cos, _1, 0.0)` jsou nesprávné.  
  
 Počet argumentů ve funkci volat na obálku volání vrácený `bind` musí být alespoň tak velké, jaká nejvyšší hodnotu číselného `is_placeholder<PH>::value` pro všechny argumenty zástupný symbol ve volání `bind`. Proto `bind(cos, _2)(0.0, 1.0)` správné (a vrátí `cos(1.0)`), a `bind(cos, _2)(0.0)` je nesprávný.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__functional__bind.cpp   
// compile with: /EHsc   
#include <functional>   
#include <algorithm>   
#include <iostream>   
  
using namespace std::placeholders;   
  
void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

void product(double x, double y)
{
    std::cout << x << "*" << y << " == " << x * y << std::endl;
}

int main()
{
    double arg[] = { 1, 2, 3 };

    std::for_each(&arg[0], arg + 3, square);
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(square, _1));

    return (0);
}

```  
  
```Output  
1^2 == 1  
2^2 == 4  
3^2 == 9  
  
1*2 == 2  
2*2 == 4  
3*2 == 6  
  
1^2 == 1  
2^2 == 4  
3^2 == 9  
```  
  
##  <a name="bind1st"></a>  bind1st –  
 Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na objekt jednočlenné funkce pomocí vazby prvního argumentu binární funkce na zadanou hodnotu.  
  
```  
template <class Operation, class Type>  
binder1st <Operation> bind1st (const Operation& func, const Type& left);
```  
  
### <a name="parameters"></a>Parametry  
 `func`  
 Objekt binární funkce, která má být převeden na objekt unární funkce.  
  
 `left`  
 Hodnota, na které má být vázána první argument funkce binární objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt unární funkce, která je výsledkem vazby první argument funkce binární objektu na hodnotu `left`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce vazače jsou druh funkce adaptéru a protože vracejí funkce objekty, můžete ji použít v určitých typů funkce – složení vytvořit složitý a výkonné výrazy.  
  
 Pokud `func` je objekt typu `Operation` a `c` je konstanta, pak `bind1st` ( `func`, `c`) je ekvivalentní [binder1st](../standard-library/binder1st-class.md) konstruktoru třídy `binder1st` <  `Operation`> ( `func`, `c`) a pohodlnější.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// functional_bind1st.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
// Creation of a user-defined function object  
// that inherits from the unary_function base class  
class greaterthan5: unary_function<int, bool>  
{  
public:  
    result_type operator()(argument_type i)  
    {  
        return (result_type)(i > 5);  
    }  
};  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( " ;  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    // Count the number of integers > 10 in the vector  
    vector<int>::iterator::difference_type result1a;  
    result1a = count_if(v1.begin(), v1.end(), bind1st(less<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1a << "." << endl;  
  
    // Compare: counting the number of integers > 5 in the vector  
    // with a user defined function object  
    vector<int>::iterator::difference_type result1b;  
    result1b = count_if(v1.begin(), v1.end(), greaterthan5());  
    cout << "The number of elements in v1 greater than 5 is: "  
         << result1b << "." << endl;  
  
    // Count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(), bind2nd(less<int>(), 10));  
    cout << "The number of elements in v1 less than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
```Output  
The vector v1 = ( 0 5 10 15 20 25 )  
The number of elements in v1 greater than 10 is: 3.  
The number of elements in v1 greater than 5 is: 4.  
The number of elements in v1 less than 10 is: 2.  
```  
  
##  <a name="bind2nd"></a>  bind2nd –  
 Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na objekt jednočlenné funkce pomocí vazby druhého argumentu binární funkce na zadanou hodnotu.  
  
```  
template <class Operation, class Type>  
binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```  
  
### <a name="parameters"></a>Parametry  
 `func`  
 Objekt binární funkce, která má být převeden na objekt unární funkce.  
  
 `right`  
 Hodnota, na které má být vázána druhý argument funkce binární objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt unární funkce, která je výsledkem vazby druhý argument funkce binární objektu na hodnotu `right`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce vazače jsou druh funkce adaptéru a protože vracejí funkce objekty, můžete ji použít v určitých typů funkce – složení vytvořit složitý a výkonné výrazy.  
  
 Pokud `func` je objekt typu **operace** a `c` je konstanta, pak `bind2nd` ( `func`, `c` ) je ekvivalentní [binder2nd](../standard-library/binder2nd-class.md) – třída Konstruktor **binder2nd\<operaci >** ( `func`, `c` ) a pohodlnější.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// functional_bind2nd.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
// Creation of a user-defined function object  
// that inherits from the unary_function base class  
class greaterthan15: unary_function<int, bool>  
{  
public:  
    result_type operator()(argument_type i)  
    {  
        return (result_type)(i > 15);  
    }  
};  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    // Count the number of integers > 10 in the vector  
    vector<int>::iterator::difference_type result1a;  
    result1a = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1a << "." << endl;  
  
    // Compare counting the number of integers > 15 in the vector  
    // with a user-defined function object  
    vector<int>::iterator::difference_type result1b;  
    result1b = count_if(v1.begin(), v1.end(), greaterthan15());  
    cout << "The number of elements in v1 greater than 15 is: "  
         << result1b << "." << endl;  
  
    // Count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(), bind1st(greater<int>(), 10));  
    cout << "The number of elements in v1 less than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
```Output  
The vector v1 = ( 0 5 10 15 20 25 )  
The number of elements in v1 greater than 10 is: 3.  
The number of elements in v1 greater than 15 is: 2.  
The number of elements in v1 less than 10 is: 2.  
```  
  
##  <a name="bit_and"></a>  bit_and –  
 Předdefinované funkce objekt, který provádí bitové operace AND (binární `operator&`) na její argumenty.  
  
```  
template <class Type = void>  
struct bit_and : public binary_function<Type, Type, Type> {  
    Type operator()(
    const Type& Left,   
    const Type& Right) const; 
 };  
 
// specialized transparent functor for operator& 
template <>
struct bit_and<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const  ->
        decltype(std::forward<T>(Left) & std::forward<U>(Right));
};
```  
  
### <a name="parameters"></a>Parametry  
 `Type`, `T`, `U`  
 Žádný typ, který podporuje `operator&` , která má operandy zadán nebo odvozené typy.  
  
 `Left`  
 Levý operand bitové operace AND. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `T`.  
  
 `Right`  
 Pravý operand bitové operace AND. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `U`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek `Left & Right`. Specializované šablony ideální předávání výsledku, který má typ, který je vrácen rutinou `operator&`.  
  
### <a name="remarks"></a>Poznámky  
 `bit_and` Functor je omezený na integrální typy pro základní typy dat, nebo na uživatelem definované typy tento binární soubor implementace `operator&`.  
  
##  <a name="bit_not"></a>  bit_not  
 Předdefinované funkce objekt, který provádí bitového doplňku (ne) operaci (unární `operator~`) na jeho argumentem.  
  
```  
template <class Type = void>  
struct bit_not : public unary_function<Type, Type>   
 {  
    Type operator()(const Type& Right) const; 
 };  
 
// specialized transparent functor for operator~  
template <>  
struct bit_not<void>   
 {  
    template <class Type>  
    auto operator()(Type&& Right) const  ->  decltype(~std::forward<Type>(Right));
 };  
```  
  
### <a name="parameters"></a>Parametry  
 `Type`  
 Typ, který podporuje unární operátor `operator~`.  
  
 `Right`  
 Operand operace bitového doplňku. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání argument odkazu lvalue a rvalue odvozené typu `Type`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek `~ Right`. Specializované šablony ideální předávání výsledku, který má typ, který je vrácen rutinou `operator~`.  
  
### <a name="remarks"></a>Poznámky  
 `bit_not` Functor je omezený na integrální typy pro základní typy dat, nebo na uživatelem definované typy tento binární soubor implementace `operator~`.  
  
##  <a name="bit_or"></a>  bit_or –  
 Předdefinované funkce objekt, který provádí bitové operace OR ( `operator|`) na její argumenty.  
  
```  
template <class Type = void>  
struct bit_or : public binary_function<Type, Type, Type> {  
    Type operator()(
    const Type& Left,   
    const Type& Right) const; 
 };  
 
// specialized transparent functor for operator|  
template <>
struct bit_or<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        ->  decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```  
  
### <a name="parameters"></a>Parametry  
 `Type`, `T`, `U`  
 Žádný typ, který podporuje `operator|` , která má operandy zadán nebo odvozené typy.  
  
 `Left`  
 Levý operand bitové operace OR. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `T`.  
  
 `Right`  
 Pravý operand bitové operace OR. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `U`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek `Left | Right`. Specializované šablony ideální předávání výsledku, který má typ, který je vrácen rutinou `operator|`.  
  
### <a name="remarks"></a>Poznámky  
 `bit_or` Functor je omezený na integrální typy pro základní typy dat, nebo na uživatelem definované typy, které implementují `operator|`.  
  
##  <a name="bit_xor"></a>  bit_xor –  
 Předdefinované funkce objekt, který provádí bitové operace XOR (binární `operator^`) na její argumenty.  
  
```  
template <class Type = void>  
struct bit_xor : public binary_function<Type, Type, Type> {  
    Type operator()(
    const Type& Left,   
    const Type& Right) const; 
 };  
 
// specialized transparent functor for operator^  
template <>
struct bit_xor<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) ^ std::forward<U>(Right));
};
```  
  
### <a name="parameters"></a>Parametry  
 `Type`, `T`, `U`  
 Žádný typ, který podporuje `operator^` , která má operandy zadán nebo odvozené typy.  
  
 `Left`  
 Levý operand bitové operace XOR. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `T`.  
  
 `Right`  
 Pravý operand bitové operace XOR. Unspecialized šablona má argument typu odkazu lvalue `Type`. Specializované šablony ideální předávání lvalue a rvalue odkaz argumenty odvodit typ `U`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek `Left ^ Right`. Specializované šablony ideální předávání výsledku, který má typ, který je vrácen rutinou `operator^`.  
  
### <a name="remarks"></a>Poznámky  
 `bit_xor` Functor je omezený na integrální typy pro základní typy dat, nebo na uživatelem definované typy tento binární soubor implementace `operator^`.  
  
##  <a name="cref"></a>  cref –  
 Z argumentu vytvoří konstantní `reference_wrapper`.  
  
```  
template <class Ty>  
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>  
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```  
  
### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ argumentu zabalit.  
  
 `arg`  
 Argument zabalit.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí první funkce `reference_wrapper<const Ty>(arg.get())`. Použijte k zabalení const odkaz. Vrátí druhou funkce `reference_wrapper<const Ty>(arg)`. Použijete ho k zalomit jako const odkaz zabalené odkaz.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__functional__cref.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    int i = 1;   
  
    std::cout << "i = " << i << std::endl;   
    std::cout << "cref(i) = " << std::cref(i) << std::endl;   
    std::cout << "cref(neg)(i) = "   
        << std::cref(&neg)(i) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
i = 1  
cref(i) = 1  
cref(neg)(i) = -1  
```  
  
##  <a name="mem_fn"></a>  mem_fn  
 Vygeneruje jednoduchou obálku volání.  
  
```  
template <class Ret, class Ty>  
unspecified mem_fn(Ret Ty::*pm);
```  
  
### <a name="parameters"></a>Parametry  
 `Ret`  
 Návratový typ zabalené funkce.  
  
 `Ty`  
 Typ ukazatel na funkci člen.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí obálku jednoduché volání funkce šablony `cw`, s typem výsledku slabé, tak, aby výraz `cw(t, a2, ..., aN)` je ekvivalentní `INVOKE(pm, t, a2, ..., aN)`. Jakékoli výjimky nevyvolá výjimku.  
  
 Obálka vrácený volání je odvozený od `std::unary_function<cv Ty*, Ret>` (proto definování vnořené typy `result_type` jako synonymum pro `Ret` a vnořené typy `argument_type` jako synonymum pro `cv Ty*`) pouze v případě typu `Ty` ukazatel na člena funkce s odchylka nákladů kvalifikátor `cv` které nepřijímá žádné argumenty.  
  
 Obálka vrácený volání je odvozený od `std::binary_function<cv Ty*, T2, Ret>` (proto definování vnořené typy `result_type` jako synonymum pro `Ret`, vnořené typ `first argument_type` jako synonymum pro `cv Ty*`a vnořené typy `second argument_type` jako synonymum pro `T2`) pouze v případě typu `Ty` je ukazatel na funkci člena s odchylka nákladů kvalifikátor `cv` , která má jeden argument typu `T2`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__functional__mem_fn.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
class Funs   
    {   
public:   
    void square(double x)   
        {   
        std::cout << x << "^2 == " << x * x << std::endl;   
        }   
  
    void product(double x, double y)   
        {   
        std::cout << x << "*" << y << " == " << x * y << std::endl;   
        }   
    };   
  
int main()   
    {   
    Funs funs;   
  
    std::mem_fn(&Funs::square)(funs, 3.0);   
    std::mem_fn(&Funs::product)(funs, 3.0, 2.0);   
  
    return (0);   
    }  
  
```  
  
```Output  
3^2 == 9  
3*2 == 6  
```  
  
##  <a name="mem_fun"></a>  mem_fun  
 Pomocné funkce šablony použité k vytvoření adaptérů objektu funkce pro členské funkce při inicializaci pomocí argumentů ukazatelů.  
  
```  
template <class Result, class Type>  
mem_fun_t<Result, Type> mem_fun (Result(Type::* pmem)());

template <class Result, class Type, class Arg>  
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg));

template <class Result, class Type>  
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pmem)() const);

template <class Result, class Type, class Arg>  
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg) const);
```  
  
### <a name="parameters"></a>Parametry  
 `pmem`  
 Ukazatel na funkci člena třídy **typ** má být převeden na objekt funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **const** nebo **non_const** objekt funkce typu `mem_fun_t` nebo `mem_fun1_t`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// functional_mem_fun.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
class StoreVals     
{  
    int val;  
public:  
    StoreVals() { val = 0; }  
    StoreVals(int j) { val = j; }  
  
    bool display() { cout << val << " "; return true; }  
    int squareval() { val *= val; return val; }  
    int lessconst(int k) {val -= k; return val; }  
};  
  
int main( )  
{  
    vector<StoreVals *> v1;  
  
    StoreVals sv1(5);  
    v1.push_back(&sv1);  
    StoreVals sv2(10);  
    v1.push_back(&sv2);  
    StoreVals sv3(15);  
    v1.push_back(&sv3);  
    StoreVals sv4(20);  
    v1.push_back(&sv4);  
    StoreVals sv5(25);  
    v1.push_back(&sv5);  
  
    cout << "The original values stored are: " ;  
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));  
    cout << endl;  
  
    // Use of mem_fun calling member function through a pointer  
    // square each value in the vector using squareval ()  
    for_each(v1.begin(), v1.end(), mem_fun<int, StoreVals>(&StoreVals::squareval));     
    cout << "The squared values are: " ;  
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));  
    cout << endl;  
  
    // Use of mem_fun1 calling member function through a pointer  
    // subtract 5 from each value in the vector using lessconst ()  
    for_each(v1.begin(), v1.end(),   
        bind2nd (mem_fun1<int, StoreVals,int>(&StoreVals::lessconst), 5));     
    cout << "The squared values less 5 are: " ;  
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));  
    cout << endl;  
}  
```  
  
##  <a name="mem_fun_ref"></a>  mem_fun_ref  
 Podpůrné funkce šablony použitý k vytvoření objektu adaptéry funkce pro členské funkce při inicializaci pomocí odkazu argumenty.  
  
```  
template <class Result, class Type>  
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pmem)());

template <class Result, class Type, class Arg>  
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pmem)(Arg));

template <class Result, class Type>  
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pmem)() const);

template <class Result, class Type, class Arg>  
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pmem)(Arg) const);
```  
  
### <a name="parameters"></a>Parametry  
 `pmem`  
 Ukazatel na funkci člena třídy `Type` má být převeden na objekt funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `const` nebo `non_const` objekt funkce typu `mem_fun_ref_t` nebo `mem_fun1_ref_t`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// functional_mem_fun_ref.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
class NumVals  
   {  
   int val;  
   public:  
   NumVals ( ) { val = 0; }  
   NumVals ( int j ) { val = j; }  
  
   bool display ( ) { cout << val << " "; return true; }  
   bool isEven ( ) { return ( bool )  !( val %2 ); }  
   bool isPrime( )  
   {  
      if (val < 2) { return true; }  
      for (int i = 2; i <= val / i; ++i)  
      {  
         if (val % i == 0) { return false; }  
      }  
      return true;  
   }  
};  
  
int main( )  
{  
   vector <NumVals> v1 ( 13 ), v2 ( 13 );  
   vector <NumVals>::iterator v1_Iter, v2_Iter;  
   int i, k;  
  
   for ( i = 0; i < 13; i++ ) v1 [ i ] = NumVals ( i+1 );  
   for ( k = 0; k < 13; k++ ) v2 [ k ] = NumVals ( k+1 );  
  
   cout << "The original values stored in v1 are: " ;  
   for_each( v1.begin( ), v1.end( ),   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
  
   // Use of mem_fun_ref calling member function through a reference  
   // remove the primes in the vector using isPrime ( )  
   v1_Iter = remove_if ( v1.begin( ),  v1.end( ),   
      mem_fun_ref ( &NumVals::isPrime ) );     
   cout << "With the primes removed, the remaining values in v1 are: " ;  
   for_each( v1.begin( ), v1_Iter,   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
  
   cout << "The original values stored in v2 are: " ;  
   for_each( v2.begin( ), v2.end( ),   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
  
   // Use of mem_fun_ref calling member function through a reference  
   // remove the even numbers in the vector v2 using isEven ( )  
   v2_Iter = remove_if ( v2.begin( ),  v2.end( ),   
      mem_fun_ref ( &NumVals::isEven ) );     
   cout << "With the even numbers removed, the remaining values are: " ;  
   for_each( v2.begin( ),  v2_Iter,   
   mem_fun_ref ( &NumVals::display ) );  
   cout << endl;  
}  
```  
  
```Output  
The original values stored in v1 are: 1 2 3 4 5 6 7 8 9 10 11 12 13   
With the primes removed, the remaining values in v1 are: 4 6 8 9 10 12   
The original values stored in v2 are: 1 2 3 4 5 6 7 8 9 10 11 12 13   
With the even numbers removed, the remaining values are: 1 3 5 7 9 11 13   
```  
  
##  <a name="not1"></a>  not1 –  
 Vrací doplněk jednočlenného predikátu.  
  
```  
template <class UnaryPredicate>  
unary_negate<UnaryPredicate> not1(const UnaryPredicate& pred);
```  
  
### <a name="parameters"></a>Parametry  
 `pred`  
 Unární predikátu. Chcete-li být Negované.  
  
### <a name="return-value"></a>Návratová hodnota  
 Predikát unární, který je negace unární predikátu upravit.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `unary_negate` sestavený ze unárního predikátu **před**( *x*), pak vrátí **! Před**( *x*).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// functional_not1.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 7; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    vector<int>::iterator::difference_type result1;  
    // Count the elements greater than 10  
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
  
    vector<int>::iterator::difference_type result2;  
    // Use the negator to count the elements less than or equal to 10  
    result2 = count_if(v1.begin(), v1.end(),  
        not1(bind2nd(greater<int>(), 10)));  
  
    cout << "The number of elements in v1 not greater than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
```Output  
The vector v1 = ( 0 5 10 15 20 25 30 35 )  
The number of elements in v1 greater than 10 is: 5.  
The number of elements in v1 not greater than 10 is: 3.  
```  
  
##  <a name="not2"></a>  not2 –  
 Vrací doplněk binárního predikátu.  
  
```  
template <class BinaryPredicate>  
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```  
  
### <a name="parameters"></a>Parametry  
 `func`  
 Binární predikát pro být Negované.  
  
### <a name="return-value"></a>Návratová hodnota  
 Predikát binární, který je negace binární predikátu upravit.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `binary_negate` je vytvořený z binárního predikátu **BinPred**( *x*, *y*), pak vrátí! **BinPred**( *x*, *y*).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// functional_not2.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <cstdlib>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <int> v1;  
   vector <int>::iterator Iter1;  
  
   int i;  
   v1.push_back( 6262 );  
   v1.push_back( 6262 );  
   for ( i = 0 ; i < 5 ; i++ )  
   {  
      v1.push_back( rand( ) );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   // use default binary predicate less<int>( )  
   sort( v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order,   
   // use the binary_negate helper function not2  
   sort( v1.begin( ), v1.end( ), not2(less<int>( ) ) );  
   cout << "Resorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
```Output  
Original vector v1 = ( 6262 6262 41 18467 6334 26500 19169 )  
Sorted vector v1 = ( 41 6262 6262 6334 18467 19169 26500 )  
Resorted vector v1 = ( 26500 19169 18467 6334 6262 6262 41 )  
```  
  
##  <a name="ptr_fun"></a>  ptr_fun –  
 Podpůrné funkce šablona používá k převodu Unární a ukazatelů na funkce binární, na přizpůsobivé funkce Unární a binární.  
  
```  
template <class Arg, class Result>  
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>  
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```  
  
### <a name="parameters"></a>Parametry  
 `pfunc`  
 Unární nebo binární funkce ukazatele má být převeden na přizpůsobivé funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první funkce šablony funkce unární [pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md) < `Arg`, **výsledek**> (* `pfunc`).  
  
 Druhá šablona funkce vrátí hodnotu binární funkce [pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \< **Arg1**, **Arg2**, **výsledek**> (* `pfunc`).  
  
### <a name="remarks"></a>Poznámky  
 Ukazatel na funkci je objekt funkce, může předat libovolný algoritmus standardní knihovna C++, která očekává jako parametr funkce, ale není přizpůsobitelné. Pro použití s adaptéru, jako je vytvoření vazby hodnotu nebo pomocí negator, musí zadat s vnořené typy, které umožňují takové přizpůsobit. Převod Unární a binární ukazatelů na funkce pomocí `ptr_fun` pomocné funkce umožňuje adaptéry funkce pro práci s Unární a binární ukazatelů na funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]  
  
##  <a name="ref"></a>  REF  
 Vytvoří `reference_wrapper` z argumentu.  
  
```  
template <class Ty>  
reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>  
reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `arg`; konkrétně `reference_wrapper<Ty>(arg)`.  
  
### <a name="example"></a>Příklad  
  V následujícím příkladu definuje dvě funkce: jeden vázaný na proměnnou string, ostatní vázaných ke odkaz na proměnnou string počítaný voláním `ref`. Při změně hodnoty proměnné, první funkce budou nadále používat starou hodnotu a druhý funkce používá nová hodnota.  
  
```cpp  
#include <algorithm>  
#include <functional>  
#include <iostream>  
#include <iterator>  
#include <ostream>  
#include <string>  
#include <vector>  
using namespace std;  
using namespace std;  
using namespace std::placeholders;  
  
bool shorter_than(const string& l, const string& r) {  
    return l.size() < r.size();  
}  
  
int main() {  
    vector<string> v_original;  
    v_original.push_back("tiger");  
    v_original.push_back("cat");  
    v_original.push_back("lion");  
    v_original.push_back("cougar");  
  
    copy(v_original.begin(), v_original.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
  
    string s("meow");  
  
    function<bool (const string&)> f = bind(shorter_than, _1, s);  
    function<bool (const string&)> f_ref = bind(shorter_than, _1, ref(s));  
  
    vector<string> v;  
  
    // Remove elements that are shorter than s ("meow")  
  
    v = v_original;  
    v.erase(remove_if(v.begin(), v.end(), f), v.end());  
  
    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
  
    // Now change the value of s.  
    // f_ref, which is bound to ref(s), will use the  
    // new value, while f is still bound to the old value.  
  
    s = "kitty";  
  
    // Remove elements that are shorter than "meow" (f is bound to old value of s)  
  
    v = v_original;  
    v.erase(remove_if(v.begin(), v.end(), f), v.end());  
  
    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
  
    // Remove elements that are shorter than "kitty" (f_ref is bound to ref(s))  
  
    v = v_original;  
    v.erase(remove_if(v.begin(), v.end(), f_ref), v.end());  
  
    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));  
    cout << endl;  
}  
```  
  
```Output  
tiger cat lion cougar  
tiger lion cougar  
tiger lion cougar  
tiger cougar  
```  
  
##  <a name="swap"></a>  Swap  
 Prohození dva `function` objekty.  
  
```  
template <class Fty>  
void swap(function<Fty>& f1, function<Fty>& f2);
```  
  
### <a name="parameters"></a>Parametry  
 `Fty`  
 Typ řízené objekty funkcí.  
  
 `f1`  
 První objekt funkce.  
  
 `f2`  
 Druhý objekt funkce.  
  
### <a name="remarks"></a>Poznámky  
 Funkce vrátí hodnotu `f1.swap(f2)`.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// std__functional__swap.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val)   
    {   
    return (-val);   
    }   
  
int main()   
    {   
    std::function<int (int)> fn0(neg);   
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;   
    std::cout << "val == " << fn0(3) << std::endl;   
  
    std::function<int (int)> fn1;   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
    std::cout << std::endl;   
  
    swap(fn0, fn1);   
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;   
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;   
    std::cout << "val == " << fn1(3) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
empty == false  
val == -3  
empty == true  
  
empty == true  
empty == false  
val == -3  
```  
  
## <a name="see-also"></a>Viz také  
 [\<funkční >](../standard-library/functional.md)

