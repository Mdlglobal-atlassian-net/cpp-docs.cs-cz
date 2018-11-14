---
title: '&lt;type_traits&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
- type_traits/std::is_copy_assignable
- type_traits/std::is_copy_constructible
- type_traits/std::is_default_constructible
- type_traits/std::is_move_assignable
- type_traits/std::is_move_constructible
- type_traits/std::is_nothrow_move_assignable
- type_traits/std::is_trivially_copy_assignable
- type_traits/std::is_trivially_move_assignable
- type_traits/std::is_trivially_move_constructible
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: 027ed3052f5341860112f564974b7a96aea7ff51
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524596"
---
# <a name="lttypetraitsgt-functions"></a>&lt;type_traits&gt; funkce

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible –](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|[is_trivially_move_assignable –](#is_trivially_move_assignable)|
|[is_trivially_move_constructible –](#is_trivially_move_constructible)|

## <a name="is_assignable"></a>  is_assignable –

Testuje, zda je hodnota *z* typ lze přiřadit k *k* typu.

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

*k*<br/>
Typ objektu, která obdrží přiřazení.

*z*<br/>
Typ objektu, který obsahuje hodnotu.

### <a name="remarks"></a>Poznámky

Nevyhodnoceném výrazu `declval<To>() = declval<From>()` musí být ve správném formátu. Obě *z* a *k* musí být kompletními typy **void**, nebo pole s neznámým rozsahem.

## <a name="is_copy_assignable"></a>  is_copy_assignable –

Testy, zda má typ je zkopírovat na přiřazení.

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má operátor přiřazení kopie, jinak má hodnotu false. Ekvivalentní is_assignable –\<Ty & const Ty & >.

## <a name="is_copy_constructible"></a>  is_copy_constructible –

Testuje, zda je typ má konstruktor kopie.

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má konstruktor kopie, jinak má hodnotu false.

### <a name="example"></a>Příklad

```cpp
#include <type_traits>
#include <iostream>

struct Copyable
{
    int val;
};

struct NotCopyable
{
   NotCopyable(const NotCopyable&) = delete;
   int val;

};

int main()
{
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha
        << std::is_copy_constructible<Copyable>::value << std::endl;
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha
        << std::is_copy_constructible<NotCopyable>::value << std::endl;

    return (0);
}
```

```Output
is_copy_constructible<Copyable> == true
is_copy_constructible<NotCopyable > == false
```

## <a name="is_default_constructible"></a>  is_default_constructible –

Testuje, zda má typ výchozí konstruktor.

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je typ třídy, která má výchozí konstruktor, jinak má hodnotu false. Jedná se o ekvivalent predikátu `is_constructible<T>`. Typ *T* musí být dokončený typ **void**, nebo pole neznámým rozsahem.

### <a name="example"></a>Příklad

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="is_move_assignable"></a>  is_move_assignable –

Testuje, zda může být typu přesuňte přiřazené.

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Typ je přiřaditelný přesunout, pokud odkaz rvalue na typ, je možné přiřadit na odkaz na typ. Predikát typu je ekvivalentní `is_assignable<T&, T&&>`. Přesuňte přiřadit typy zahrnují označím Skalární typy a typy tříd, které se mají generované kompilátorem nebo uživatelem definované operátory přiřazení přesunutí.

## <a name="is_move_constructible"></a>  is_move_constructible –

Ověřuje, zda typ má konstruktor move.

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, který má být vyhodnocen

### <a name="remarks"></a>Poznámky

Predikát typu, který se vyhodnotí jako true, pokud typ *T* lze sestavit pomocí operace přesunu. Tento predikát je ekvivalentní `is_constructible<T, T&&>`.

## <a name="is_nothrow_move_assignable"></a>  is_nothrow_move_assignable –

Testuje, jestli má typ **nothrow** operátor move assignment.

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* má nothrow operátor přiřazení přesunutí, jinak má hodnotu false.

## <a name="is_trivially_copy_assignable"></a>  is_trivially_copy_assignable –

Ověřuje, zda má typ jednoduchého dotazu kopírovacího operátoru přiřazení.

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *T* je třída, která má triviální operátor přiřazení kopie, jinak má hodnotu false.

Přiřazení konstruktor pro třídu *T* je jednoduché, pokud je implicitně určen, třída *T* nemá žádné virtuální funkce třídy *T* nemá žádné virtuální báze třídy všechny nestatické datové členy typu třídy mají operátory jednoduchého dotazu přiřazení a třídy nestatických datových členů typu pole třídy mají operátory přiřazení triviální.

## <a name="is_trivially_move_assignable"></a>  is_trivially_move_assignable –

Ověřuje, zda tento typ nemá operátor přiřazení přesunutí triviální.

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má triviální operátor přiřazení přesunutí, jinak má hodnotu false.

Operátor přiřazení přesunu pro třídu *Ty* triviální pokud:

implicitně se poskytuje

Třída *Ty* nemá žádné virtuální funkce

Třída *Ty* nemá žádné virtuálních základních tříd

třídy všechny nestatické datové členy typu třídy mají operátory přiřazení pro přesunutí jednoduchého dotazu

třídy nestatických datových členů typu pole třídy mají operátory přiřazení pro přesunutí jednoduchého dotazu

## <a name="is_trivially_move_constructible"></a>  is_trivially_move_constructible –

Konstruktor přesunu testuje, zda má typ jednoduchého dotazu.

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu obsahuje hodnotu true, pokud typ *Ty* je třída, která má triviální konstruktor přesunutí, jinak má hodnotu false.

Konstruktor přesunu pro třídu *Ty* triviální pokud:

je implicitně deklarován

typy parametrů jsou rovnocenné těm implicitní deklaraci

Třída *Ty* nemá žádné virtuální funkce

Třída *Ty* nemá žádné virtuálních základních tříd

Třída nemá žádné nestálá nestatické datové členy

všechny přímo základů třídy *Ty* mají triviální konstruktorů

třídy všechny nestatické datové členy typu třídy mají triviální konstruktorů

třídy nestatických datových členů typu pole třídy mají triviální konstruktorů

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)<br/>
