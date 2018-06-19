---
title: Funkce třída | Microsoft Docs
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
ms.openlocfilehash: 26164c391689c8fb7f24f49464e141f74a3058ee
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847839"
---
# <a name="function-class"></a>function – třída

Obálka volatelná aplikacemi objektu.

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

`Fty` Typ funkce zabalit.

`Ax` Funkce přidělení.

## <a name="remarks"></a>Poznámky

Šablony třídy je volání obálky, jejíž volání podpis je `Ret(T1, T2, ..., TN)`. Použijete jej uzavřete celou řadu s objekty do uniform obálku.

Některé funkce člen trvat operand názvy požadované cílový objekt. Můžete určit takový operand několika způsoby:

`fn` --objekt s `fn`; po volání `function` objektu obsahuje kopii `fn`

`fnref` --s objekt s názvem podle `fnref.get()`; po volání `function` má odkaz na objekt `fnref.get()`

`right` --s objekt, pokud existuje, ukládaná společností `function` objektu `right`

`npc` – ukazatel s hodnotou null; Po volání `function` objekt je prázdný

Ve všech případech `INVOKE(f, t1, t2, ..., tN)`, kde `f` je možné volat objekt a `t1, t2, ..., tN` jsou hodnoty lvalue typů `T1, T2, ..., TN` , musí být ve správném formátu a pokud `Ret` není void, převést na `Ret`.

Prázdná `function` objekt nemá s objekt nebo odkaz na objekt volatelná aplikacemi.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[Funkce](#function)|Vytvoří obálku, který je prázdný nebo ukládá objekt s libovolného typu s pevnou podpis.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[result_type](#result_type)|Návratový typ objektu uložené volatelná aplikacemi.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[přiřazení](#assign)|Objekt s přiřadí k tomuto objektu funkce.|
|[Swap](#swap)|Prohodit s dva objekty.|
|[cíl](#target)|Testů, pokud je uložen s objektu je možné volat jako zadaný.|
|[target_type](#target_type)|Získá typ informace s objektu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[Function::Operator neurčené](#op_unspecified)|Testy, pokud je uložen s objekt existuje.|
|[funkce:: Operator() –](#op_call)|Volání s objektu.|
|[Function::Operator =](#op_eq)|Nahradí objekt uložené volatelná aplikacemi.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<funkční >

**Namespace:** – std

## <a name="assign"></a>  Function::Assign

Objekt s přiřadí k tomuto objektu funkce.

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

`_Func` Objekt s.

`_Fnref` Obálka odkaz, který obsahuje objekt s.

`Ax` Objekt přidělení.

### <a name="remarks"></a>Poznámky

Členské funkce každý nahradit `callable object` držené `*this` s s objekt předaný jako `operand`. Obě přidělit úložiště s objektem přidělení `Ax`.

## <a name="function"></a>  Function::Function

Vytvoří obálku, který je prázdný nebo ukládá objekt s libovolného typu s pevnou podpis.

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

`right` Objekt funkce pro kopírování.

`Fx` Typ objektu, kterou lze volat.

`_Func` Objekt s zabalit.

`Alloc` Typ přidělení.

`Ax` Přidělení.

`_Fnref` Odkaz na objekt s zabalit.

### <a name="remarks"></a>Poznámky

První dva konstruktory vytvořit prázdnou `function` objektu. Vytvořit následující tři konstruktory `function` předá objekt, který obsahuje objekt s jako operand. Poslední dva konstruktory přidělit úložiště s objektem přidělení Ax.

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

## <a name="op_unspecified"></a>  Function::Operator neurčené

Testy, pokud je uložen s objekt existuje.

```cpp
operator unspecified();
```

### <a name="remarks"></a>Poznámky

Vrátí hodnotu, která je převést na operátor `bool` s hodnotou true pouze v případě, že objekt není prázdný. Můžete použít k ověření, zda objekt je prázdný.

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

## <a name="op_call"></a>  funkce:: Operator() –

Volání s objektu.

```cpp
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```

### <a name="parameters"></a>Parametry

`TN` Typ n. volání argument.

`tN` N-tou volání argument.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu `INVOKE(fn, t1, t2, ..., tN, Ret)`, kde `fn` je cílový objekt, který je uložen v `*this`. Můžete využít k volání objekt zabalené volatelná aplikacemi.

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

Nahradí objekt uložené volatelná aplikacemi.

```cpp
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>
    function& operator=(Fty fn);
template <class Fty>
    function& operator=(reference_wrapper<Fty> fnref);
```

### <a name="parameters"></a>Parametry

`npc` Toto je konstanta ukazatele null.

`right` Objekt funkce pro kopírování.

`fn` Objekt s zabalit.

`fnref` Odkaz na objekt s zabalit.

### <a name="remarks"></a>Poznámky

Operátory každý nahradit objekt s držené `*this` s objektem předány jako operand.

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

Návratový typ objektu uložené volatelná aplikacemi.

```cpp
typedef Ret result_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ `Ret` v podpisu volání šablony. Použijte k určení návratový typ objektu zabalené volatelná aplikacemi.

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

Prohodit s dva objekty.

```cpp
void swap(function& right);
```

### <a name="parameters"></a>Parametry

`right` Objekt funkce, které chcete Prohodit s.

### <a name="remarks"></a>Poznámky

Členská funkce prohození cílové objekty mezi `*this` a `right`. Ho probíhá ve konstantní čas a vyvolá žádné výjimky.

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

Testů, pokud je uložen s objektu je možné volat jako zadaný.

```cpp
template <class Fty2>
    Fty2 *target();
template <class Fty2>
    const Fty2 *target() const;
```

### <a name="parameters"></a>Parametry

`Fty2` Cílový typ objektu s otestovat.

### <a name="remarks"></a>Poznámky

Typ `Fty2` musí být s typy argumentů `T1, T2, ..., TN` a návratový typ `Ret`. Pokud `target_type() == typeid(Fty2)`, funkce šablony člen vrátí adresu cílového objektu; jinak vrátí hodnotu 0.

Typ `Fty2` lze volat pro typy argumentů `T1, T2, ..., TN` a návratový typ `Ret` Pokud pro hodnoty lvalue `fn, t1, t2, ..., tN` typů `Fty2, T1, T2, ..., TN`, `INVOKE(fn, t1, t2, ..., tN)` je ve správném formátu a pokud `Ret` není `void`, převést na `Ret`.

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

Získá typ informace s objektu.

```cpp
const std::type_info& target_type() const;
```

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu `typeid(void)` Pokud `*this` je prázdný, v opačném případě vrátí `typeid(T)`, kde `T` je typ cílového objektu.

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

## <a name="see-also"></a>Viz také

[mem_fn](../standard-library/functional-functions.md#mem_fn)<br/>
[reference_wrapper – třída](../standard-library/reference-wrapper-class.md)<br/>
