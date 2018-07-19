---
title: funkce třídy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
dev_langs:
- C++
helpviewer_keywords:
- std::function [C++]
- std::function [C++], result_type
- std::function [C++], assign
- std::function [C++], swap
- std::function [C++], target
- std::function [C++], target_type
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ca8621067c851b5a1e107eb16800d546562fbb6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959926"
---
# <a name="function-class"></a>function – třída

Obálka pro volatelný objekt.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Fty>
class function  // Fty of type Ret(T1, T2, ..., TN)
    : public unary_function<T1, Ret>       // when Fty is Ret(T1)
    : public binary_function<T1, T2, Ret>  // when Fty is Ret(T1, T2)
{
public:
    typedef Ret result_type;

    function();
    function(nullptr_t);
    function(const function& right);
    template <class Fty2>
        function(Fty2 fn);
    template <class Fty2, class Alloc>
        function(reference_wrapper<Fty2>, const Alloc& Ax);

    template <class Fty2, class Alloc>
        void assign(Fty2, const Alloc& Ax);
    template <class Fty2, class Alloc>
        void assign(reference_wrapper<Fty2>, const Alloc& Ax);
    function& operator=(nullptr_t);
    function& operator=(const function&);
    template <class Fty2>
        function& operator=(Fty2);
    template <class Fty2>
        function& operator=(reference_wrapper<Fty2>);

    void swap(function&);
    explicit operator bool() const;

    result_type operator()(T1, T2, ....., TN) const;
    const std::type_info& target_type() const;
    template <class Fty2>
        Fty2 *target();

    template <class Fty2>
        const Fty2 *target() const;

    template <class Fty2>
        void operator==(const Fty2&) const = delete;
    template <class Fty2>
        void operator!=(const Fty2&) const = delete;
};
```

### <a name="parameters"></a>Parametry

*Fty* typ funkce zahrnující.

*AX* funkci alokátoru.

## <a name="remarks"></a>Poznámky

Třída šablony je obálka volání, jehož signatura volání je `Ret(T1, T2, ..., TN)`. Použijete ji k uzavření širokou škálu volatelných objektů v obálce jednotné.

Některé členské funkce přijímají operand, který označuje požadovaný cílový objekt. Takové operand můžete zadat několika způsoby:

`fn` --volatelný objekt `fn`; po volání `function` obsahuje kopii `fn`

`fnref` --volatelný objekt s názvem podle `fnref.get()`; po volání `function` obsahuje odkaz na objekt `fnref.get()`

`right` --volatelný objekt, pokud existuje, drží `function` objektu `right`

`npc` – ukazatel s hodnotou null; Po volání `function` objekt je prázdný

Ve všech případech `INVOKE(f, t1, t2, ..., tN)`, kde `f` je volatelný objekt a `t1, t2, ..., tN` jsou l-hodnoty typů `T1, T2, ..., TN` , musí být ve správném formátu a v případě `Ret` není void, lze převést na `Ret`.

Prázdná `function` objekt neobsahuje volatelného objektu nebo odkazem na volatelný objekt.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[– funkce](#function)|Vytvoří obálku, která je prázdná nebo uchovává volatelný objekt libovolného typu s pevnou podpis.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[result_type](#result_type)|Návratový typ uložený volatelný objekt.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[přiřazení](#assign)|Volatelný objekt přiřadí k tomuto objektu funkce.|
|[Prohození](#swap)|Zamění dvě volatelných objektů.|
|[Cíl](#target)|Testuje, zda je uložená volatelný objekt lze volat jako zadaný.|
|[target_type](#target_type)|Získá typ informací na volatelný objekt.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[Tento parametr zadán Function::Operator](#op_unspecified)|Testuje, zda existuje uložené volatelný objekt.|
|[funkce:: operator()](#op_call)|Volá volatelný objekt.|
|[Function::Operator =](#op_eq)|Nahradí uloženou volatelný objekt.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** std

## <a name="assign"></a>  Function::Assign

Volatelný objekt přiřadí k tomuto objektu funkce.

```cpp
template <class Fx, class Alloc>
    void assign(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    void assign(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>Parametry

*_Func* volatelný objekt.

*_Fnref* obálku odkaz, který obsahuje volatelný objekt.

*AX* objekt alokátoru.

### <a name="remarks"></a>Poznámky

Členské funkce jednotlivých nahradit `callable object` drží `*this` s volatelný objekt předán jako `operand`. Obě přidělení úložiště s objekt alokátoru, který *Ax*.

## <a name="function"></a>  Function::Function

Vytvoří obálku, která je prázdná nebo uchovává volatelný objekt libovolného typu s pevnou podpis.

```cpp
function();
function(nullptr_t npc);
function(const function& right);
template <class Fx>
    function(Fx _Func);
template <class Fx>
    function(reference_wrapper<Fx> _Fnref);
template <class Fx, class Alloc>
    function(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    function(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>Parametry

*správné* objektu funkce pro kopírování.

*FX* typu volatelný objekt.

*_Func* volatelný objekt zabalit.

*ALLOC* typ alokátoru.

*AX* přidělujícího modulu.

*_Fnref* odkaz volatelný objekt zabalit.

### <a name="remarks"></a>Poznámky

První dva konstruktory vytvořit prázdnou `function` objektu. Vytvořit následující tři konstruktory `function` objekt, který uchovává volatelný objekt předán jako operand. Poslední dva konstruktory přidělení úložiště s objekt alokátoru Ax.

### <a name="example"></a>Příklad

```cpp
// std__functional__function_function.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <vector>

int square(int val)
{
    return val * val;
}

class multiply_by
{
public:
    explicit multiply_by(const int n) : m_n(n) { }

    int operator()(const int x) const
    {
        return m_n * x;
    }

private:
    int m_n;
};

int main()
{

    typedef std::vector< std::function<int (int)> > vf_t;

    vf_t v;
    v.push_back(square);
    v.push_back(std::negate<int>());
    v.push_back(multiply_by(3));

    for (vf_t::const_iterator i = v.begin(); i != v.end(); ++i)
    {
        std::cout << (*i)(10) << std::endl;
    }

    std::function<int (int)> f = v[0];
    std::function<int (int)> g;

    if (f) {
        std::cout << "f is non-empty (correct)." << std::endl;
    } else {
        std::cout << "f is empty (can't happen)." << std::endl;
    }

    if (g) {
        std::cout << "g is non-empty (can't happen)." << std::endl;
    } else {
        std::cout << "g is empty (correct)." << std::endl;
    }

    return 0;
}
```

```Output
100
-10
30
f is non-empty (correct).
g is empty (correct).
```

## <a name="op_unspecified"></a>  Tento parametr zadán Function::Operator

Testuje, zda existuje uložené volatelný objekt.

```cpp
operator unspecified();
```

### <a name="remarks"></a>Poznámky

Operátor vrátí hodnotu, která je převoditelná na **bool** s hodnotu true pouze v případě, že objekt není prázdný. Použijete ji k ověření, zda objekt je prázdný.

### <a name="example"></a>Příklad

```cpp
// std__functional__function_operator_bool.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == " << (bool)fn0 << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == " << (bool)fn1 << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```

## <a name="op_call"></a>  funkce:: operator()

Volá volatelný objekt.

```cpp
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```

### <a name="parameters"></a>Parametry

*TN* typ argumentu n-tý volání.

*tN* n-tý argument volání.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `INVOKE(fn, t1, t2, ..., tN, Ret)`, kde `fn` je cílový objekt uložený v `*this`. Použít jej k vyvolání zkomprimovaného volatelného objektu.

### <a name="example"></a>Příklad

```cpp
// std__functional__function_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="op_eq"></a>  Function::Operator =

Nahradí uloženou volatelný objekt.

```cpp
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>
    function& operator=(Fty fn);
template <class Fty>
    function& operator=(reference_wrapper<Fty> fnref);
```

### <a name="parameters"></a>Parametry

*NPC* konstantu nulového ukazatele.

*správné* objektu funkce pro kopírování.

*fn* volatelný objekt zabalit.

*fnref* odkaz volatelný objekt zabalit.

### <a name="remarks"></a>Poznámky

Operátory každý nahradit volatelný objekt uchovaný podle `*this` s volatelný objekt předán jako operand.

### <a name="example"></a>Příklad

```cpp
// std__functional__function_operator_as.cpp
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
    fn1 = 0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    fn1 = neg;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = fn0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = std::cref(fn1);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true
empty == false
val == -3
empty == false
val == -3
empty == false
val == -3
```

## <a name="result_type"></a>  Function::result_type

Návratový typ uložený volatelný objekt.

```cpp
typedef Ret result_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ `Ret` v podpisu volání šablony. To umožňuje určit návratový typ zkomprimovaného volatelného objektu.

### <a name="example"></a>Příklad

```cpp
// std__functional__function_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    std::function<int (int)>::result_type val = fn1(3);
    std::cout << "val == " << val << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="swap"></a>  Function::swap

Zamění dvě volatelných objektů.

```cpp
void swap(function& right);
```

### <a name="parameters"></a>Parametry

*správné* objekt funkce, který chcete Prohodit s.

### <a name="remarks"></a>Poznámky

Členská funkce Zamění cílové objektů mezi `*this` a *správné*. Provádí se v konstantním času a vyvolá výjimku žádné výjimky.

### <a name="example"></a>Příklad

```cpp
// std__functional__function_swap.cpp
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

    fn0.swap(fn1);
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

## <a name="target"></a>  Function::target

Testuje, zda je uložená volatelný objekt lze volat jako zadaný.

```cpp
template <class Fty2>
    Fty2 *target();
template <class Fty2>
    const Fty2 *target() const;
```

### <a name="parameters"></a>Parametry

*Fty2* cílový typ volatelný objekt k testování.

### <a name="remarks"></a>Poznámky

Typ *Fty2* musí být pro typy argumentů `T1, T2, ..., TN` a návratový typ `Ret`. Pokud `target_type() == typeid(Fty2)`, členská funkce šablony vrátí adresu cílového objektu; v opačném případě vrátí hodnotu 0.

Typ *Fty2* lze volat pro typy argumentů `T1, T2, ..., TN` a návratový typ `Ret` po dobu hodnotami lvalues `fn, t1, t2, ..., tN` typů `Fty2, T1, T2, ..., TN`, `INVOKE(fn, t1, t2, ..., tN)` ve správném formátu a v případě `Ret`není **void**, lze převést na `Ret`.

### <a name="example"></a>Příklad

```cpp
// std__functional__function_target.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    typedef int (*Myfun)(int);
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "no target == " << (fn0.target<Myfun>() == 0) << std::endl;

    Myfun *fptr = fn0.target<Myfun>();
    std::cout << "val == " << (*fptr)(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "no target == " << (fn1.target<Myfun>() == 0) << std::endl;

    return (0);
    }

```

```Output
empty == false
no target == false
val == -3
empty == true
no target == true
```

## <a name="target_type"></a>  Function::target_type

Získá typ informací na volatelný objekt.

```cpp
const std::type_info& target_type() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `typeid(void)` Pokud `*this` je prázdný, v opačném případě vrátí `typeid(T)`, kde `T` je typ cílového objektu.

### <a name="example"></a>Příklad

```cpp
// std__functional__function_target_type.cpp
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
    std::cout << "type == " << fn0.target_type().name() << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "type == " << fn1.target_type().name() << std::endl;

    return (0);
    }
```

```Output
empty == false
type == int (__cdecl*)(int)
empty == true
type == void
```

## <a name="see-also"></a>Viz také:

[mem_fn](../standard-library/functional-functions.md#mem_fn)<br/>
[reference_wrapper – třída](../standard-library/reference-wrapper-class.md)<br/>
