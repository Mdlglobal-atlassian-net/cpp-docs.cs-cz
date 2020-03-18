---
title: '&lt;funkčních&gt; funkcí'
ms.date: 02/21/2019
f1_keywords:
- functional/std::bind
- functional/std::bind1st
- functional/std::bind2nd
- functional/std::bit_and
- functional/std::bit_not
- functional/std::bit_or
- functional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- functional/std::mem_fn
- functional/std::mem_fun_ref
- functional/std::not1
- functional/std::not2
- functional/std::not_fn
- functional/std::ptr_fun
- functional/std::ref
- functional/std::swap
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
ms.openlocfilehash: 546d8c61e875dd7c295e892359e39fa5a76867b4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421798"
---
# <a name="ltfunctionalgt-functions"></a>&lt;funkčních&gt; funkcí

Tyto funkce jsou zastaralé v C++ 11 a odebrané v C++ 17:

||||
|-|-|-|
|[bind1st –](#bind1st) |[bind2nd –](#bind2nd)|[mem_fun](#mem_fun)|
|[mem_fun_ref](#mem_fun_ref)|[ptr_fun](#ptr_fun)||

Tyto funkce jsou v C++ 17 zastaralé:

|||
|-|-|
|[not1 –](#not1)|[not2 –](#not2)|

## <a name="bind"></a>zapisovat

Naváže argumenty na volatelný objekt.

```cpp
template <class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);

template <class RTy, class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>Parametry

*Fey*\
Typ objektu, který má být volán.

\ *TN*
Typ argumentu volání n-tý.

*fn*\
Objekt, který má být volán.

\ *TN*
Argument pro volání n-tý.

### <a name="remarks"></a>Poznámky

Typy `FT, T1, T2, ..., TN` musí být Copy-constructible a `INVOKE(fn, t1, ..., tN)` musí být platným výrazem pro některé hodnoty `w1, w2, ..., wN`.

První funkce šablony vrací obálku přesměrovacího volání `g` s slabým výsledným typem. Účinek `g(u1, u2, ..., uM)` je `INVOKE(f, v1, v2, ..., vN, `[invoke_result](../standard-library/invoke-result-class.md)`<FT cv (V1, V2, ..., VN)>::type)`, kde `cv` jsou kvalifikátory cv `g` a hodnoty a typy vázaných argumentů `v1, v2, ..., vN` jsou určeny jak je uvedeno níže. Použijete ho ke svázání argumentů s navázaným objektem, aby bylo možné volat objekt se seznamem argumentů, který je přizpůsobený.

Druhá funkce šablony vrací obálku přesměrovacího volání `g` s vnořeným typem `result_type`, který je synonymem pro `RTy`. Účinek `g(u1, u2, ..., uM)` je `INVOKE(f, v1, v2, ..., vN, RTy)`, kde `cv` jsou kvalifikátory cv `g` a hodnoty a typy vázaných argumentů `v1, v2, ..., vN` jsou určené níže. Použijete ho ke svázání argumentů s vydaným objektem, aby bylo možné volat objekt s přizpůsobeným seznamem argumentů a se zadaným návratovým typem.

Hodnoty vázaných argumentů `v1, v2, ..., vN` a jejich odpovídající typy `V1, V2, ..., VN` závisí na typu odpovídajícího argumentu `ti` typu `Ti` ve volání metody `bind` a kvalifikátory cv `cv` z obálky volání `g` následujícím způsobem:

Pokud je `ti` typu `reference_wrapper<T>` je argument `vi` `ti.get()` a jeho typ `Vi` je `T&`;

Pokud je hodnota `std::is_bind_expression<Ti>::value` **true** , argument `vi` je `ti(u1, u2, ..., uM)` a jeho typ `Vi` je `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`;

Pokud hodnota `j` `std::is_placeholder<Ti>::value` není nula, je argument `vi` `uj` a jeho typ `Vi` je `Uj&`;

v opačném případě je argument `vi` `ti` a jeho typ `Vi` je `Ti` `cv` `&`.

Například při zadání funkce `f(int, int)` výrazu `bind(f, _1, 0)` vrátí obálku přesměrovacího volání `cw` taková, `cw(x)` volá `f(x, 0)`. Výraz `bind(f, 0, _1)` vrátí obálku pro přesměrování volání `cw` tak, aby `cw(x)` volání `f(0, x)`.

Počet argumentů v volání `bind` a argument `fn` musí být roven počtu argumentů, které mohou být předány volajícímu objektu `fn`. Například `bind(cos, 1.0)` je správné a `bind(cos)` a `bind(cos, _1, 0.0)` jsou nesprávné.

Počet argumentů ve volání funkce obálky volání vrácené `bind` musí být alespoň tak velký, jako nejvyšší číslovaná hodnota `is_placeholder<PH>::value` pro všechny zástupné znaky v volání `bind`. Například `bind(cos, _2)(0.0, 1.0)` je správný (a vrátí `cos(1.0)`) a `bind(cos, _2)(0.0)` je nesprávná.

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

## <a name="bind1st"></a>bind1st –

Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na unární objekt funkce. Vytvoří vazby prvního argumentu binární funkce na zadanou hodnotu. Zastaralé v C++ 11, odebrané v C++ 17.

```cpp
template <class Operation, class Type>
    binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>Parametry

\ *Func*
Objekt binární funkce, který má být převeden na unární objekt funkce.

*levý*\
Hodnota, na kterou má být první argument objektu binární funkce svázán.

### <a name="return-value"></a>Návratová hodnota

Unární objekt funkce, který je výsledkem vazby prvního argumentu objektu binární funkce na hodnotu *Left*.

### <a name="remarks"></a>Poznámky

Vazby funkcí jsou druhem adaptéru funkce. Vzhledem k tomu, že vracejí objekty funkce, mohou být použity v určitých typech složení funkce k vytvoření složitějších a výkonných výrazů.

Pokud *Func* je objekt typu `Operation` a `c` je konstanta, pak `bind1st( func, c )` je stejný jako `binder1st<Operation>(func, c)`konstruktoru třídy [binder1st –](../standard-library/binder1st-class.md) a je pohodlnější použít.

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

## <a name="bind2nd"></a>bind2nd –

Pomocná funkce šablony, která vytvoří adaptér pro převedení objektu binární funkce na unární objekt funkce. Naváže druhý argument binární funkce na zadanou hodnotu. Zastaralé v C++ 11, odebrané v C++ 17.

```cpp
template <class Operation, class Type>
    binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>Parametry

\ *Func*
Objekt binární funkce, který má být převeden na unární objekt funkce.

*pravé*\
Hodnota, na kterou má být druhý argument objektu binární funkce svázán.

### <a name="return-value"></a>Návratová hodnota

Výsledkem objektu unární funkce je vytvoření vazby druhého argumentu objektu binární funkce *vpravo*.

### <a name="remarks"></a>Poznámky

Vazby funkcí jsou druhem adaptéru funkce. Vzhledem k tomu, že vracejí objekty funkce, mohou být použity v určitých typech složení funkce k vytvoření složitějších a výkonných výrazů.

Pokud je *Func* objekt typu `Operation` a `c` je konstanta, pak `bind2nd(func, c)` je stejný jako `binder2nd<Operation>(func, c)`konstruktoru třídy [binder2nd –](../standard-library/binder2nd-class.md) a pohodlnější pro použití.

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

## <a name="bit_and"></a>bit_and

Předdefinovaný objekt funkce, který provádí v argumentech bitovou a operaci (binární `operator&`).

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

*Type*, *T*, *U*\
Jakýkoli typ, který podporuje `operator&`, které přebírají operandy zadaných nebo odvozených typů.

*Levý*\
Levý operand bitové operace AND. Nespecializovaná šablona přebírá argument odkazu *lvalue typu typ.* Specializovaná šablona provede dokonalé přesměrování na lvalue a odkazy rvalue na odvozený typ *T*.

*Pravé*\
Pravý operand bitové operace AND. Nespecializovaná šablona přebírá argument odkazu *lvalue typu typ.* Specializovaná šablona provede dokonalé přesměrování na lvalue a odkazy rvalue na odvozený typ *U*.

### <a name="return-value"></a>Návratová hodnota

Výsledek `Left & Right`. Specializovaná šablona provede dokonalé přesměrování výsledku, který má typ vrácený `operator&`.

### <a name="remarks"></a>Poznámky

`bit_and` funktor je omezen na celočíselné typy pro základní datové typy nebo na uživatelsky definované typy, které implementují binární `operator&`.

## <a name="bit_not"></a>bit_not

Předdefinovaný objekt funkce, který provádí v argumentu operaci bitového doplňku (nejedná se o unární `operator~`). Přidáno v C++ 14.

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
    auto operator()(Type&& Right) const -> decltype(~std::forward<Type>(Right));
};
```

### <a name="parameters"></a>Parametry

*Zadejte*\
Typ, který podporuje unární `operator~`.

*Pravé*\
Operand operace bitového doplňku. Nespecializovaná šablona přebírá argument odkazu *lvalue typu typ.* Specializovaná šablona provede dokonalé přesměrování argumentu lvalue nebo odkazu rvalue *typu*odvozeného typu.

### <a name="return-value"></a>Návratová hodnota

Výsledek `~ Right`. Specializovaná šablona provede dokonalé přesměrování výsledku, který má typ vrácený `operator~`.

### <a name="remarks"></a>Poznámky

`bit_not` funktor je omezen na celočíselné typy pro základní datové typy nebo na uživatelsky definované typy, které implementují binární `operator~`.

## <a name="bit_or"></a>bit_or

Předdefinovaný objekt funkce, který provádí v argumentech bitovou nebo operaci (`operator|`).

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
        -> decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parametry

*Type*, *T*, *U*\
Jakýkoli typ, který podporuje `operator|`, které přebírají operandy zadaných nebo odvozených typů.

*Levý*\
Levý operand bitové operace OR. Nespecializovaná šablona přebírá argument odkazu *lvalue typu typ.* Specializovaná šablona provede dokonalé přesměrování na lvalue a odkazy rvalue na odvozený typ *T*.

*Pravé*\
Pravý operand bitové operace OR. Nespecializovaná šablona přebírá argument odkazu *lvalue typu typ.* Specializovaná šablona provede dokonalé přesměrování na lvalue a odkazy rvalue na odvozený typ *U*.

### <a name="return-value"></a>Návratová hodnota

Výsledek `Left | Right`. Specializovaná šablona provede dokonalé přesměrování výsledku, který má typ vrácený `operator|`.

### <a name="remarks"></a>Poznámky

`bit_or` funktor je omezen na celočíselné typy pro základní datové typy nebo na uživatelsky definované typy, které implementují `operator|`.

## <a name="bit_xor"></a>bit_xor

Předdefinovaný objekt funkce, který provádí v argumentech operaci bitové operace XOR (binární `operator^`).

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

*Type*, *T*, *U*\
Jakýkoli typ, který podporuje `operator^`, které přebírají operandy zadaných nebo odvozených typů.

*Levý*\
Levý operand bitové operace XOR Nespecializovaná šablona přebírá argument odkazu *lvalue typu typ.* Specializovaná šablona provede dokonalé přesměrování na lvalue a odkazy rvalue na odvozený typ *T*.

*Pravé*\
Pravý operand operace logického operátoru XOR. Nespecializovaná šablona přebírá argument odkazu *lvalue typu typ.* Specializovaná šablona provede dokonalé přesměrování na lvalue a odkazy rvalue na odvozený typ *U*.

### <a name="return-value"></a>Návratová hodnota

Výsledek `Left ^ Right`. Specializovaná šablona provede dokonalé přesměrování výsledku, který má typ vrácený `operator^`.

### <a name="remarks"></a>Poznámky

`bit_xor` funktor je omezen na celočíselné typy pro základní datové typy nebo na uživatelsky definované typy, které implementují binární `operator^`.

## <a name="cref"></a>cref

Z argumentu vytvoří konstantní `reference_wrapper`.

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ argumentu, který se má zabalit

*arg* –\
Argument, který se má zabalit

### <a name="remarks"></a>Poznámky

První funkce vrátí `reference_wrapper<const Ty>(arg.get())`. Použijete ho k zabalení odkazu const. Druhá funkce vrátí `reference_wrapper<const Ty>(arg)`. Použijete ho k přebalení zabalených odkazů jako odkazu const.

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

## <a name="invoke"></a>Zavolejte

Vyvolá libovolný objekt, který se má volat, s danými argumenty. Přidáno v C++ 17.

```cpp
template <class Callable, class... Args>
invoke_result_t<Callable, Args...>
    invoke(Callable&& fn, Args&&... args) noexcept(/* specification */);
```

### <a name="parameters"></a>Parametry

*Volat*\
Typ objektu, který má být volán.

\ *argumentů*
Typy argumentů volání.

*fn*\
Objekt, který má být volán.

\ *argumentů*
Argumenty volání.

\ *specifikace*
`std::is_nothrow_invocable_v<Callable, Args>)`specifikace **s výjimkou** .

### <a name="remarks"></a>Poznámky

Vyvolá přivolaný objekt *FN* pomocí *argumentů*Parameters. Efektivně `INVOKE(std::forward<Callable>(fn), std::forward<Args>(args)...)`, kde `INVOKE(f, t1, t2, ..., tN)` pseudo-function znamená jednu z následujících akcí:

- `(t1.*f)(t2, ..., tN)`, je-li `f` ukazatel na členskou funkci třídy `T` a `t1` je objekt typu `T` nebo odkaz na objekt typu `T` nebo odkaz na objekt typu odvozeného z `T`. To znamená, když `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` má hodnotu true.

- `(t1.get().*f)(t2, ..., tN)`, když je `f` ukazatel na členskou funkci třídy `T` a `std::decay_t<decltype(t1)>` je specializace `std::reference_wrapper`.

- `((*t1).*f)(t2, ..., tN)`, je-li `f` ukazatel na členskou funkci třídy `T` a `t1` není jedním z předchozích typů.

- `t1.*f`, když N = 1 a `f` je ukazatel na Členská data třídy `T` a `t1` je objekt typu `T` nebo odkaz na objekt typu `T` nebo odkaz na objekt typu odvozeného z `T`.  To znamená, když `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` má hodnotu true.

- `t1.get().*f`, když N = 1 a `f` je ukazatel na Členská data třídy `T` a `std::decay_t<decltype(t1)>` je specializace `std::reference_wrapper`.

- `(*t1).*f`, když N = 1 a `f` je ukazatel na Členská data třídy `T` a `t1` není jedním z předchozích typů.

- `f(t1, t2, ..., tN)` ve všech ostatních případech.

Informace o typu výsledného objektu, který se nedá volat, najdete v tématu [invoke_result](invoke-result-class.md). Predikáty na volatelné typy naleznete v tématu [is_invocable, is_invocable_r, is_nothrow_invocable is_nothrow_invocable_r třídy](is-invocable-classes.md).

### <a name="example"></a>Příklad

```cpp
// functional_invoke.cpp
// compile using: cl /EHsc /std:c++17 functional_invoke.cpp
#include <functional>
#include <iostream>

struct Demo
{
    int n_;

    Demo(int const n) : n_{n} {}

    void operator()( int const i, int const j ) const
    {
        std::cout << "Demo operator( " << i << ", "
            << j << " ) is " << i * j << "\n";
    }

    void difference( int const i ) const
    {
        std::cout << "Demo.difference( " << i << " ) is "
            << n_ - i << "\n";
    }
};

void divisible_by_3(int const i)
{
    std::cout << i << ( i % 3 == 0 ? " is" : " isn't" )
        << " divisible by 3.\n";
}

int main()
{
    Demo d{ 42 };
    Demo * pd{ &d };
    auto pmf = &Demo::difference;
    auto pmd = &Demo::n_;

    // Invoke a function object, like calling d( 3, -7 )
    std::invoke( d, 3, -7 );

    // Invoke a member function, like calling
    // d.difference( 29 ) or (d.*pmf)( 29 )
    std::invoke( &Demo::difference, d, 29 );
    std::invoke( pmf, pd, 13 );

    // Invoke a data member, like access to d.n_ or d.*pmd
    std::cout << "d.n_: " << std::invoke( &Demo::n_, d ) << "\n";
    std::cout << "pd->n_: " << std::invoke( pmd, pd ) << "\n";

    // Invoke a stand-alone (free) function
    std::invoke( divisible_by_3, 42 );

    // Invoke a lambda
    auto divisible_by_7 = []( int const i ) {
        std::cout << i << ( i % 7 == 0 ? " is" : " isn't" )
            << " divisible by 7.\n";
        };
    std::invoke( divisible_by_7, 42 );
}
```

```Output
Demo operator( 3, -7 ) is -21
Demo.difference( 29 ) is 13
Demo.difference( 13 ) is 29
d.n_: 42
pd->n_: 42
42 is divisible by 3.
42 is divisible by 7.
```

## <a name="mem_fn"></a>mem_fn

Vygeneruje jednoduchou obálku volání.

```cpp
template <class RTy, class Ty>
unspecified mem_fn(RTy Ty::*pm);
```

### <a name="parameters"></a>Parametry

*RTy*\
Návratový typ zabalené funkce.

*Ty*\
Typ ukazatele členské funkce

### <a name="remarks"></a>Poznámky

Funkce šablony vrací jednoduchý `cw`obálky volání s slabým typem výsledku, který je `cw(t, a2, ..., aN)` výrazu stejný jako `INVOKE(pm, t, a2, ..., aN)`. Nevyvolá žádné výjimky.

Vrácený obálka volání je odvozena od `std::unary_function<cv Ty*, RTy>` (a definováním vnořeného typu `result_type` jako synonymum pro *RTy* a vnořeného typu `argument_type` jako synonymum pro `cv Ty*`) pouze v případě, *že typ daného* typu je ukazatel na členskou funkci s kvalifikátorem CV `cv`, který nepřijímá žádné argumenty.

Vrácený obálka volání je odvozena od `std::binary_function<cv Ty*, T2, RTy>` (a definováním vnořeného typu `result_type` jako synonymum pro *RTy*, vnořený typ `first argument_type` jako synonymum pro `cv Ty*`a vnořený typ `second argument_type` jako synonymum pro `T2`) pouze v případě, že typ, který je ukazatelem na členskou funkci s kvalifikátorem CV `cv`, který přebírá jeden *argument typu `T2`* .

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

## <a name="mem_fun"></a>mem_fun

Pomocné funkce šablony použité k vytvoření adaptérů objektu funkce pro členské funkce při inicializaci pomocí argumentů ukazatelů. Zastaralé v C++ 11 pro [mem_fn](#mem_fn) a [BIND](#bind)a odebráno v c++ 17.

```cpp
template <class Result, class Type>
mem_fun_t<Result, Type> mem_fun (Result(Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg) const);
```

### <a name="parameters"></a>Parametry

*pMem*\
Ukazatel na členskou funkci třídy `Type`, která má být převedena na objekt funkce.

### <a name="return-value"></a>Návratová hodnota

Objekt funkce **const** nebo **non_const** typu `mem_fun_t` nebo `mem_fun1_t`.

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

## <a name="mem_fun_ref"></a>mem_fun_ref

Pomocné funkce šablon používané k vytvoření adaptérů objektu funkce pro členské funkce při inicializaci pomocí argumentů odkazů. Zastaralé v C++ 11, odebrané v C++ 17.

```cpp
template <class Result, class Type>
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pMem)(Arg) const);
```

### <a name="parameters"></a>Parametry

*pMem*\
Ukazatel na členskou funkci třídy `Type`, která má být převedena na objekt funkce.

### <a name="return-value"></a>Návratová hodnota

Objekt funkce **const** nebo `non_const` typu `mem_fun_ref_t` nebo `mem_fun1_ref_t`.

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

## <a name="not1"></a>not1 –

Vrací doplněk jednočlenného predikátu. Zastaralé pro [not_fn](#not_fn) v c++ 17.

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& predicate);
```

### <a name="parameters"></a>Parametry

\ *predikátu*
Unární predikát, který má být negace.

### <a name="return-value"></a>Návratová hodnota

Unární predikát, který je negací unárního predikátu změněn.

### <a name="remarks"></a>Poznámky

Pokud je `unary_negate` vytvořen z unárního predikátu `predicate(x)`, vrátí `!predicate(x)`.

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

## <a name="not2"></a>not2 –

Vrací doplněk binárního predikátu. Zastaralé pro [not_fn](#not_fn) v c++ 17.

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>Parametry

\ *Func*
Binární predikát, který má být negace.

### <a name="return-value"></a>Návratová hodnota

Binární predikát, který je negací nezměněného binárního predikátu.

### <a name="remarks"></a>Poznámky

Pokud je `binary_negate` vytvořen z binárního predikátu `binary_predicate(x, y)`, vrátí `!binary_predicate(x, y)`.

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

## <a name="not_fn"></a>not_fn

Šablona funkce `not_fn` přijímá objekt, který se dá volat, a vrátí objekt, který se dá volat. V případě, že vrácený objekt s voláním je později vyvolán s některými argumenty, předává je původní možnému objektu, který logicky negace výsledek. Zachovává chování const kvalifikace a kategorie hodnoty zabaleného volatelné objektu. `not_fn` je v C++ 17 novinkou a nahrazuje zastaralé `std::not1`, `std::not2`, `std::unary_negate`a `std::binary_negate`.

```cpp
template <class Callable>
/* unspecified */ not_fn(Callable&& func);
```

### <a name="parameters"></a>Parametry

\ *Func*
Objekt, který se používá k vytvoření obálky předávacího volání.

### <a name="remarks"></a>Poznámky

Funkce šablony vrátí obálku volání, jako je `return call_wrapper(std::forward<Callable>(func))`, na základě této třídy, která je jen pro Exposition:

```cpp
class call_wrapper
{
   using FD = decay_t<Callable>;
   explicit call_wrapper(Callable&& func);

public:
   call_wrapper(call_wrapper&&) = default;
   call_wrapper(call_wrapper const&) = default;

   template<class... Args>
     auto operator()(Args&&...) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());

private:
  FD fd;
};
```

Explicitní konstruktor funkce *Func* objektu pro vyžadování vyžaduje typ `std::decay_t<Callable>` pro splnění požadavků `MoveConstructible`a `is_constructible_v<FD, Callable>` musí mít hodnotu true. Inicializuje zabalený volaný objekt `fd` z `std::forward<Callable>(func)`a vyvolá jakoukoli výjimku vyvolanou konstrukcí `fd`.

Obálka zpřístupňuje operátory volání odlišené podle hodnoty lvalue nebo odkazové kategorie rvalue a konstantní kvalifikace, jak je znázorněno zde:

```cpp
template<class... Args> auto operator()(Args&&... args) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());
```

První dva jsou stejné jako `return !std::invoke(fd, std::forward<Args>(args)...)`. Druhá dvě jsou stejná jako `return !std::invoke(std::move(fd), std::forward<Args>(args)...)`.

### <a name="example"></a>Příklad

```cpp
// functional_not_fn_.cpp
// compile with: /EHsc /std:c++17
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    std::vector<int> v1 = { 99, 6264, 41, 18467, 6334, 26500, 19169 };
    auto divisible_by_3 = [](int i){ return i % 3 == 0; };

    std::cout << "Vector v1 = ( " ;
    for (const auto& item : v1)
    {
        std::cout << item << " ";
    }
    std::cout << ")" << std::endl;

    // Count the number of vector elements divisible by 3.
    int divisible =
        std::count_if(v1.begin(), v1.end(), divisible_by_3);
    std::cout << "Elements divisible by three: "
        << divisible << std::endl;

    // Count the number of vector elements not divisible by 3.
    int not_divisible =
        std::count_if(v1.begin(), v1.end(), std::not_fn(divisible_by_3));
    std::cout << "Elements not divisible by three: "
        << not_divisible << std::endl;
}
```

```Output
Vector v1 = ( 99 6264 41 18467 6334 26500 19169 )
Elements divisible by three: 2
Elements not divisible by three: 5
```

## <a name="ptr_fun"></a>ptr_fun

Pomocné funkce šablon používané pro převod unárních a binárních ukazatelů na funkce v uvedeném pořadí na unární a binární adaptivní funkce. Zastaralé v C++ 11, odebrané v C++ 17.

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>Parametry

*pfunc*\
Unární nebo binární ukazatel funkce, který má být převeden na přizpůsobitelnou funkci.

### <a name="return-value"></a>Návratová hodnota

První funkce šablony vrací Unární funkci [pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md) <`Arg`, **výsledek**> (\* `pfunc`).

Druhá funkce šablony vrátí binární funkci [pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \<**arg1**, **Arg2**, **Result**> (\* `pfunc`).

### <a name="remarks"></a>Poznámky

Ukazatel funkce je objekt funkce. Může být předán jakémukoli algoritmu, který jako parametr očekává funkci, ale nelze jej upravit. Informace o vnořených typech jsou vyžadovány pro použití s adaptérem, například k navázání hodnoty na ni nebo pro negaci. Převod unárních a binárních ukazatelů na funkce pomocí pomocné funkce `ptr_fun` umožňuje adaptivním funkcím pracovat s unárními a binárními ukazateli funkcí.

### <a name="example"></a>Příklad

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a>odkazů

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

Následující příklad definuje dvě funkce: jeden vázaný na proměnnou řetězce, druhý vázaný na odkaz proměnné řetězce vypočítané voláním `ref`. Když se změní hodnota proměnné, bude první funkce nadále používat starou hodnotu a druhá funkce použije novou hodnotu.

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

## <a name="swap"></a>adresu

Zamění dva objekty `function`.

```cpp
template <class FT>
    void swap(function<FT>& f1, function<FT>& f2);
```

### <a name="parameters"></a>Parametry

\ *ft*
Typ řízený objekty funkce.

\ *F1*
První objekt funkce.

*f2*\
Druhý objekt funkce.

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
