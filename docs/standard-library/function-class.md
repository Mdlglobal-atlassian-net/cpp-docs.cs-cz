---
title: function – třída
ms.date: 11/04/2016
f1_keywords:
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
helpviewer_keywords:
- std::function [C++]
- std::function [C++], result_type
- std::function [C++], assign
- std::function [C++], swap
- std::function [C++], target
- std::function [C++], target_type
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
ms.openlocfilehash: 432b61c7bc5b7f0e6f82e5bfeca7758c70785774
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689640"
---
# <a name="function-class"></a>function – třída

Obálka pro objekt, který se bude volat

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

*Fty* \
Typ funkce, která se má zabalit

@No__t_1 *AX*
Funkce přidělování.

## <a name="remarks"></a>Poznámky

Šablona třídy je obálka volání, jejíž signatura volání je `Ret(T1, T2, ..., TN)`. Použijete ho k uzavření celé řady volatelné objekty v rámci jednotné obálky.

Některé členské funkce přebírají operand, který název požadovaného cílového objektu. Takový operand můžete zadat několika způsoby:

`fn` – volatelné objekty `fn`; Po volání `function` objekt drží kopii `fn`

`fnref` – volatelné objekty s názvem `fnref.get()`; Po volání obsahuje objekt `function` odkaz na `fnref.get()`

`right` – vydaný objekt, pokud existuje, je uložený objektem `function` `right`

`npc`--ukazatel s hodnotou null; Po volání je objekt `function` prázdný.

Ve všech případech `INVOKE(f, t1, t2, ..., tN)`, kde `f` je volatelné objekty a `t1, t2, ..., tN` jsou hodnoty lvalue typu `T1, T2, ..., TN`, musí být ve správném formátu a, pokud `Ret` není void, převést na `Ret`.

Prázdný objekt `function` neobsahuje objekt, který lze volat, ani odkaz na volatelné objekty.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[slouží](#function)|Vytvoří obálku, která je buď prázdná, nebo ukládá objekt, který je libovolný typ s pevným podpisem.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[result_type](#result_type)|Návratový typ uloženého objektu, který se má volat|

### <a name="functions"></a>Funkce

|||
|-|-|
|[řadit](#assign)|Přiřadí objekt, který je k tomuto objektu funkce, volat.|
|[adresu](#swap)|Proměňte dva objekty, které se budou volat.|
|[cílové](#target)|Testuje, zda je uložený objekt, který je možno volat, zadán.|
|[target_type](#target_type)|Načte informace o typu u objektu, který se nedá volat.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[nespecifikovaný operátor](#op_unspecified)|Testuje, zda existuje uložený objekt, který se má volat.|
|[operator () – operátor](#op_call)|Volá volatelné objekty.|
|[operátor =](#op_eq)|Nahradí uložený objekt, který se bude volat.|

## <a name="assign"></a>řadit

Přiřadí objekt, který je k tomuto objektu funkce, volat.

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

*_Func* \
Objekt, který se může volat.

*_Fnref* \
Referenční obálka obsahující objekt, který je k

@No__t_1 *AX*
Objekt přidělování.

### <a name="remarks"></a>Poznámky

Členské funkce každé nahradí `callable object` držené `*this` s voláním objektu, který je předán jako `operand`. Obě tyto služby přidělují úložiště k objektu přidělování objektů *AX*.

## <a name="function"></a>slouží

Vytvoří obálku, která je buď prázdná, nebo ukládá objekt, který je libovolný typ s pevným podpisem.

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

*pravé* \
Objekt funkce, který se má zkopírovat

@No__t_1 *FX*
Typ objektu, který se má volat

*_Func* \
Objekt, který se má volat, se zabalí.

@No__t_1 *přidělení*
Typ přidělování.

@No__t_1 *AX*
Alokátor.

*_Fnref* \
Odkaz na volat objekt pro zabalení.

### <a name="remarks"></a>Poznámky

První dva konstruktory vytvoří prázdný objekt `function`. Následující tři konstruktory vytvoří objekt `function`, který obsahuje volatelné objekty předané jako operand. Poslední dva konstruktory přidělují úložiště k objektu Alokátor AX.

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

## <a name="op_unspecified"></a>nespecifikovaný operátor

Testuje, zda existuje uložený objekt, který se má volat.

```cpp
operator unspecified();
```

### <a name="remarks"></a>Poznámky

Operátor vrátí hodnotu, která je převoditelná na **bool** s hodnotou true pouze v případě, že objekt není prázdný. Použijete ho k otestování, jestli je objekt prázdný.

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

## <a name="op_call"></a>operator () – operátor

Volá volatelné objekty.

```cpp
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```

### <a name="parameters"></a>Parametry

@No__t_1 *TN*
Typ argumentu volání n-tý.

\ *TN*
Argument pro volání n-tý.

### <a name="remarks"></a>Poznámky

Členská funkce vrací `INVOKE(fn, t1, t2, ..., tN, Ret)`, kde `fn` je cílový objekt uložený v `*this`. Použijete ho k volání zabaleného objektu, který se dá volat.

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

## <a name="op_eq"></a>operátor =

Nahradí uložený objekt, který se bude volat.

```cpp
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>
    function& operator=(Fty fn);
template <class Fty>
    function& operator=(reference_wrapper<Fty> fnref);
```

### <a name="parameters"></a>Parametry

*npc* \
Konstanta ukazatele s hodnotou null.

*pravé* \
Objekt funkce, který se má zkopírovat

*fn* \
Objekt, který se má volat, se zabalí.

*fnref* \
Odkaz na volat objekt pro zabalení.

### <a name="remarks"></a>Poznámky

Jednotlivé operátory nahrazují objekt, který je k dis`*this`, s voláním objektu, který je předán jako operand.

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

## <a name="result_type"></a>result_type

Návratový typ uloženého objektu, který se má volat

```cpp
typedef Ret result_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ `Ret` v podpisu volání šablony. Použijete ji k určení návratového typu zabaleného objektu, který se dá volat.

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

## <a name="swap"></a>adresu

Proměňte dva objekty, které se budou volat.

```cpp
void swap(function& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Objekt funkce, pomocí kterého se má prohodit.

### <a name="remarks"></a>Poznámky

Členská funkce přemění cílové objekty mezi `*this` a *Right*. Provede to v konstantním čase a nevyvolává žádné výjimky.

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

## <a name="target"></a>cílové

Testuje, zda je uložený objekt, který je možno volat, zadán.

```cpp
template <class Fty2>
    Fty2 *target();
template <class Fty2>
    const Fty2 *target() const;
```

### <a name="parameters"></a>Parametry

*Fty2* \
Cílový typ objektu, který lze volat pro testování.

### <a name="remarks"></a>Poznámky

Typ *Fty2* musí být možné volat pro typy argumentů `T1, T2, ..., TN` a návratový typ `Ret`. Pokud `target_type() == typeid(Fty2)`, funkce šablony člena vrátí adresu cílového objektu; v opačném případě vrátí 0.

Typ *Fty2* je možné volat pro typy argumentů `T1, T2, ..., TN` a návratový typ `Ret` if, for hodnoty lvalue `fn, t1, t2, ..., tN` typů `Fty2, T1, T2, ..., TN`, v uvedeném pořadí, `INVOKE(fn, t1, t2, ..., tN)` je ve správném formátu, a pokud `Ret` není **void**, převést na `Ret`.

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

## <a name="target_type"></a>target_type

Načte informace o typu u objektu, který se nedá volat.

```cpp
const std::type_info& target_type() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `typeid(void)`, pokud je `*this` prázdné, jinak vrátí `typeid(T)`, kde `T` je typ cílového objektu.

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
