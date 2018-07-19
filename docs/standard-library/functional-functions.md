---
title: '&lt;funkční&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9033ba128714edde2593a09fbfb46f9f65d195ae
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957448"
---
# <a name="ltfunctionalgt-functions"></a>&lt;funkční&gt; funkce

||||
|-|-|-|
|[Vytvoření vazby](#bind)|[bind1st –](#bind1st)|[bind2nd –](#bind2nd)|
|[bit_and –](#bit_and)|[bit_not](#bit_not)|[bit_or](#bit_or)|
|[bit_xor](#bit_xor)|[cref](#cref)|[mem_fn](#mem_fn)|
|[mem_fun](#mem_fun)|[mem_fun_ref](#mem_fun_ref)|[not1 –](#not1)|
|[not2 –](#not2)|[ptr_fun](#ptr_fun)|[ref](#ref)|
|[Prohození](#swap)|

## <a name="bind"></a>  Vytvoření vazby

Naváže argumenty na volatelný objekt.

```cpp
template <class Fty, class T1, class T2, ..., class TN>
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);

template <class Ret, class Fty, class T1, class T2, ..., class TN>
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>Parametry

*Fty* typ objektu určeného k volání.

*TN* typ argumentu n-tý volání.

*fn* objekt, který chcete volat.

*tN* n-tý argument volání.

### <a name="remarks"></a>Poznámky

Typy `Fty, T1, T2, ..., TN` musí být kopie constructible, a `INVOKE(fn, t1, ..., tN)` musí být platný výraz pro některé hodnoty `w1, w2, ..., wN`.

První šablona funkce vrátí předávání volání obálky `g` typu slabé výsledku. Účinek `g(u1, u2, ..., uM)` je `INVOKE(f, v1, v2, ..., vN, ` [result_of –](../standard-library/result-of-class.md)`<Fty cv (V1, V2, ..., VN)>::type)`, kde `cv` je kvalifikátory cv z `g` a hodnoty a typy argumentů vázané `v1, v2, ..., vN` jsou určeny jako níže uvedené. Použijete ji k vytvoření vazby argumenty na volatelný objekt provádět se seznamem míru argument volatelný objekt.

Druhá funkce šablony vrátí předávání volání obálky `g` s vnořený typ `result_type` , který je synonymum pro `Ret`. Účinek `g(u1, u2, ..., uM)` je `INVOKE(f, v1, v2, ..., vN, Ret)`, kde `cv` je kvalifikátory cv z `g` a hodnoty a typy argumentů vázané `v1, v2, ..., vN` je zjištěno, jak je uvedeno níže. Použijete ji k vytvoření vazby argumenty na volatelný objekt volatelný objekt s seznam přizpůsobených argumentů a zadaný návratový typ.

Hodnoty vázané argumentů `v1, v2, ..., vN` a jejich odpovídající typy `V1, V2, ..., VN` závisí na typu odpovídající argument `ti` typu `Ti` ve volání `bind` a kvalifikátory cv `cv` z Obálka volání `g` následujícím způsobem:

Pokud `ti` je typu `reference_wrapper<T>` argument `vi` je `ti.get()` a její typ `Vi` je `T&`;

Pokud hodnota `std::is_bind_expression<Ti>::value` je **true** argument `vi` je `ti(u1, u2, ..., uM)` a její typ `Vi` je `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`;

Pokud hodnota `j` z `std::is_placeholder<Ti>::value` je argument nebyl nulovou `vi` je `uj` a její typ `Vi` je `Uj&`;

v opačném případě je argument `vi` je `ti` a její typ `Vi` je `Ti` `cv` `&`.

Mějme například funkci `f(int, int)` výraz `bind(f, _1, 0)` Obálka volání vrátí předávání `cw` tak, aby `cw(x)` volání `f(x, 0)`. Výraz `bind(f, 0, _1)` Obálka volání vrátí předávání `cw` tak, aby `cw(x)` volání `f(0, x)`.

Počet argumentů ve volání `bind` kromě argument `fn` musí být roven počtu argumentů, které mohou být předány volatelný objekt `fn`. Proto `bind(cos, 1.0)` je správný a obě `bind(cos)` a `bind(cos, _1, 0.0)` , nejsou správné.

Počet argumentů ve funkci volání Obálka volání, vrácený `bind` musí být přinejmenším stejně velká jako nejvyšší hodnotu číselného `is_placeholder<PH>::value` pro všechny zástupné argumenty ve volání `bind`. Proto `bind(cos, _2)(0.0, 1.0)` je správný (a vrátí `cos(1.0)`), a `bind(cos, _2)(0.0)` je nesprávný.

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

## <a name="bind1st"></a>  bind1st –

Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na objekt jednočlenné funkce pomocí vazby prvního argumentu binární funkce na zadanou hodnotu.

```cpp
template <class Operation, class Type>
binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>Parametry

*Func* objekt binární funkce pro převod na objekt jednočlenné funkce.

*levé* hodnotu, do kterého má být vázaný prvního argumentu binární funkce na objekt.

### <a name="return-value"></a>Návratová hodnota

Objekt jednočlenné funkce, která je výsledkem vazby prvního argumentu binární funkce na objekt na hodnotu *levé*.

### <a name="remarks"></a>Poznámky

Funkce vazače jsou druh adaptér funkce a protože vrátí objekty funkce, je možné v určitých typů funkce – složení vytvořit složité a výkonné výrazy.

Pokud *func* je objekt typu `Operation` a `c` je konstanta, pak `bind1st` ( `func`, `c`) odpovídá [binder1st –](../standard-library/binder1st-class.md) konstruktoru třídy `binder1st` <  `Operation`> ( `func`, `c`) a je snazší.

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

## <a name="bind2nd"></a>  bind2nd –

Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na objekt jednočlenné funkce pomocí vazby druhého argumentu binární funkce na zadanou hodnotu.

```cpp
template <class Operation, class Type>
binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>Parametry

*Func* objekt binární funkce pro převod na objekt jednočlenné funkce.

*správné* hodnotu, do kterého má být vázaný druhého argumentu binární funkce na objekt.

### <a name="return-value"></a>Návratová hodnota

Objekt jednočlenné funkce, která je výsledkem vazby druhého argumentu binární funkce na objekt na hodnotu *správné*.

### <a name="remarks"></a>Poznámky

Funkce vazače jsou druh adaptér funkce a protože vrátí objekty funkce, je možné v určitých typů funkce – složení vytvořit složité a výkonné výrazy.

Pokud *func* je objekt typu `Operation` a `c` je konstanta, pak `bind2nd` ( `func`, `c` ) odpovídá [binder2nd –](../standard-library/binder2nd-class.md) konstruktoru třídy **binder2nd –\<operace >** ( `func`, `c` ) a pohodlnější.

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

## <a name="bit_and"></a>  bit_and –

Předdefinovaný objekt funkce, který provádí logické bitové operace AND (binární `operator&`) na svých argumentů.

```cpp
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

*Typ*, *T*, *U* libovolný typ, který podporuje `operator&` , která přebírá operandů zadaný nebo odvozené typy.

*Vlevo* levý operand bitové operace AND. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *T*.

*Pravé* pravý operand bitové operace AND. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *U*.

### <a name="return-value"></a>Návratová hodnota

Výsledek `Left & Right`. Specializovaná šablona perfektní přesměrování výsledku, který má typ, který je vrácen `operator&`.

### <a name="remarks"></a>Poznámky

`bit_and` Funktor omezen na integrální typy pro základní typy dat, nebo do uživatelem definované typy tento binární soubor implementace `operator&`.

## <a name="bit_not"></a>  bit_not –

Předdefinovaný objekt funkce, která provádí bitového doplňku (ne) operaci (unární `operator~`) na svůj argument.

```cpp
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

*Typ* typ, který podporuje unární `operator~`.

*Pravé* operand operace bitového doplňku. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování argument typu odkaz lvalue nebo rvalue *typ*.

### <a name="return-value"></a>Návratová hodnota

Výsledek `~ Right`. Specializovaná šablona perfektní přesměrování výsledku, který má typ, který je vrácen `operator~`.

### <a name="remarks"></a>Poznámky

`bit_not` Funktor omezen na integrální typy pro základní typy dat, nebo do uživatelem definované typy tento binární soubor implementace `operator~`.

## <a name="bit_or"></a>  bit_or –

Předdefinovaný objekt funkce, který provádí logické bitové operace OR (`operator|`) na svých argumentů.

```cpp
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

*Typ*, *T*, *U* libovolný typ, který podporuje `operator|` , která přebírá operandů zadaný nebo odvozené typy.

*Vlevo* levý operand bitová operace OR. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *T*.

*Pravé* pravý operand bitová operace OR. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *U*.

### <a name="return-value"></a>Návratová hodnota

Výsledek `Left | Right`. Specializovaná šablona perfektní přesměrování výsledku, který má typ, který je vrácen `operator|`.

### <a name="remarks"></a>Poznámky

`bit_or` Funktor omezen na integrální typy pro základní typy dat, nebo do uživatelem definované typy, které implementují `operator|`.

## <a name="bit_xor"></a>  bit_xor –

Předdefinovaný objekt funkce, který provádí logické bitové operace XOR (binární `operator^`) na svých argumentů.

```cpp
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

*Typ*, *T*, *U* libovolný typ, který podporuje `operator^` , která přebírá operandů zadaný nebo odvozené typy.

*Vlevo* levý operand bitové operace XOR. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *T*.

*Pravé* pravý operand bitové operace XOR. Nespecializovaná šablony přebírá argument typu odkazu l-hodnoty *typ*. Specializovaná šablona perfektní přesměrování l-hodnoty a argumenty odkazu rvalue odvodit typ *U*.

### <a name="return-value"></a>Návratová hodnota

Výsledek `Left ^ Right`. Specializovaná šablona perfektní přesměrování výsledku, který má typ, který je vrácen `operator^`.

### <a name="remarks"></a>Poznámky

`bit_xor` Funktor omezen na integrální typy pro základní typy dat, nebo do uživatelem definované typy tento binární soubor implementace `operator^`.

## <a name="cref"></a>  cref

Z argumentu vytvoří konstantní `reference_wrapper`.

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>Parametry

*Ty* typ argumentu zabalit.

*arg* argument zabalit.

### <a name="remarks"></a>Poznámky

První funkce vrací `reference_wrapper<const Ty>(arg.get())`. Můžete použít ke sbalení odkazu const. Druhá funkce vrátí `reference_wrapper<const Ty>(arg)`. Použijete ji znovu zabalit jako konstantní odkaz zabalené odkaz.

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

## <a name="mem_fn"></a>  mem_fn

Vygeneruje jednoduchou obálku volání.

```cpp
template <class Ret, class Ty>
unspecified mem_fn(Ret Ty::*pm);
```

### <a name="parameters"></a>Parametry

*Staré* návratový typ zabalené funkce.

*Ty* typ ukazatele členské funkce.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí jednoduchou obálku volání `cw`, s typem výsledku slabé tak, že výraz `cw(t, a2, ..., aN)` je ekvivalentní `INVOKE(pm, t, a2, ..., aN)`. Nevyvolá žádné výjimky.

Obálka volání vrácené je odvozen z `std::unary_function<cv Ty*, Ret>` (proto definování vnořeného typu `result_type` jako synonymum pro *Ret* a vnořeného typu `argument_type` jako synonymum pro `cv Ty*`) pouze tehdy, pokud typ  *Ty* je ukazatel na členskou funkci s kvalifikátor cv-qualifier `cv` , která nepřijímá žádné argumenty.

Obálka volání vrácené je odvozen z `std::binary_function<cv Ty*, T2, Ret>` (proto definování vnořeného typu `result_type` jako synonymum pro *Ret*, vnořený typ `first argument_type` jako synonymum pro `cv Ty*`a vnořený typ `second argument_type`jako synonymum pro `T2`) pouze tehdy, pokud typ *Ty* je ukazatel na členskou funkci s kvalifikátor cv-qualifier `cv` , která přijímá jeden argument typu `T2`.

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

## <a name="mem_fun"></a>  mem_fun –

Pomocné funkce šablony použité k vytvoření adaptérů objektu funkce pro členské funkce při inicializaci pomocí argumentů ukazatelů.

```cpp
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

*pmem* ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

### <a name="return-value"></a>Návratová hodnota

A **const** nebo **nekonstantní** objektu funkce typu `mem_fun_t` nebo `mem_fun1_t`.

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

## <a name="mem_fun_ref"></a>  mem_fun_ref

Pomocné funkce šablony použité k vytvoření adaptérů objektu funkce pro členské funkce při inicializaci pomocí argumentů reference.

```cpp
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

*pmem* ukazatel na členskou funkci třídy `Type` má být převeden na objekt funkce.

### <a name="return-value"></a>Návratová hodnota

A **const** nebo `non_const` objektu funkce typu `mem_fun_ref_t` nebo `mem_fun1_ref_t`.

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

## <a name="not1"></a>  not1 –

Vrací doplněk jednočlenného predikátu.

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& pred);
```

### <a name="parameters"></a>Parametry

*před* unární predikát k bude negovat.

### <a name="return-value"></a>Návratová hodnota

Unární predikát, který je negace unární predikát, změnit.

### <a name="remarks"></a>Poznámky

Pokud `unary_negate` je vytvořen z unární predikát **před**( *x*), pak vrátí **! Před**( *x*).

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

## <a name="not2"></a>  not2 –

Vrací doplněk binárního predikátu.

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>Parametry

*Func* binárním predikátem bude negovat.

### <a name="return-value"></a>Návratová hodnota

Upravovat binární predikát, který je negace binárním predikátem.

### <a name="remarks"></a>Poznámky

Pokud `binary_negate` je vytvořen z binárním predikátem **BinPred**( *x*, *y*), pak vrátí! **BinPred**( *x*, *y*).

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

## <a name="ptr_fun"></a>  ptr_fun –

Pomocné funkce šablony použité k převést na jednočlenné a binární funkce ukazatele a binárních přizpůsobitelných funkcí.

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>Parametry

*pfunc* unární nebo binární ukazatel funkce pro převod na přizpůsobitelné funkce.

### <a name="return-value"></a>Návratová hodnota

První šablona funkce vrátí funkci unárního [pointer_to_unary_function –](../standard-library/pointer-to-unary-function-class.md) < `Arg`, **výsledek**> (* `pfunc`).

Druhá funkce šablony vrátí binární funkce [pointer_to_binary_function –](../standard-library/pointer-to-binary-function-class.md) \< **Arg1**, **Arg2**, **výsledek**> (* `pfunc`).

### <a name="remarks"></a>Poznámky

Ukazatel na funkci je objekt funkce a může být předán s libovolným algoritmem standardní knihovny C++, který očekává funkci jako parametr, ale není přizpůsobitelné. Pro použití s adaptér, jako jsou k němu po navázání hodnoty nebo pomocí negator, je nutné zadat vnořené typy, které umožňují tyto úpravy. Převod ukazatelů na jednočlenné a binární funkce podle `ptr_fun` pomocnou funkci umožňuje adaptérů funkce pro práci s ukazatelů na jednočlenné a binární funkce.

### <a name="example"></a>Příklad

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a>  REF

Vytvoří `reference_wrapper` z argumentu.

```cpp
template <class Ty>
reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>
reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na `arg`; konkrétně `reference_wrapper<Ty>(arg)`.

### <a name="example"></a>Příklad

Následující příklad definuje dvě funkce: jeden vázána na řetězcovou proměnnou, je mez na odkaz řetězcová hodnota vypočítaná aplikací volání `ref`. Při změně hodnoty proměnné, první funkce i nadále používat staré hodnoty a druhá funkce používá novou hodnotu.

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

## <a name="swap"></a>  Prohození

Prohodí dva `function` objekty.

```cpp
template <class Fty>
void swap(function<Fty>& f1, function<Fty>& f2);
```

### <a name="parameters"></a>Parametry

*Fty* typ řízený objekty funkce.

*F1* první objekt funkce.

*F2* druhý objekt funkce.

### <a name="remarks"></a>Poznámky

Funkce vrátí `f1.swap(f2)`.

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

## <a name="see-also"></a>Viz také:

[\<funkční >](../standard-library/functional.md)<br/>
