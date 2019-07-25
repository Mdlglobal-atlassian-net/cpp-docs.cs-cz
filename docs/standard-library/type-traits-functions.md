---
title: '&lt;funkce&gt; type_traits'
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
ms.openlocfilehash: 48ca51d56994f3d487af6744801acedf5c6cc79c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447034"
---
# <a name="lttypetraitsgt-functions"></a>&lt;funkce&gt; type_traits

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_nothrow_swappable](#is_nothrow_swappable)|[is_nothrow_swappable_with](#is_nothrow_swappable_with)|
|[is_swappable](#is_swappable)|[is_swappable_with](#is_swappable_with)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|
|[is_trivially_move_assignable](#is_trivially_move_assignable)|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a>is_assignable

Testuje, zda lze *k typu přiřadit* hodnotu *z* typu.

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

*Schopn*\
Typ objektu, který přijímá přiřazení.

*Výsledkem*\
Typ objektu, který poskytuje hodnotu.

### <a name="remarks"></a>Poznámky

Vyhodnocený výraz `declval<To>() = declval<From>()` musí být ve správném formátu. *Mezi* i *pro* musí být úplné typy, **void**nebo pole neznámého typu Bound.

## <a name="is_copy_assignable"></a>is_copy_assignable

Testuje, zda je možné kopírovat typ při přiřazení.

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, *Pokud typ je* třída, která má operátor přiřazení kopie, v opačném případě obsahuje hodnotu false. Ekvivalentem is_assignable\<&, const Ty & >.

## <a name="is_copy_constructible"></a>is_copy_constructible

Testuje, zda typ obsahuje kopírovací konstruktor.

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud *je typ,* který je třída, která má kopírovací konstruktor, jinak obsahuje hodnotu false.

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

## <a name="is_default_constructible"></a>is_default_constructible

Testuje, zda má typ výchozí konstruktor.

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud typ *T* je typ třídy, která má výchozí konstruktor, jinak má hodnotu false. To je ekvivalentní predikátu `is_constructible<T>`. Typ *T* musí být úplný typ, **void**nebo pole s neznámou vazbou.

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

## <a name="is_move_assignable"></a>is_move_assignable

Testuje, zda lze typ přesunout přiřazeno.

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Typ je přesunutý, pokud odkaz na rvalue typ může být přiřazený odkaz na typ. Predikát typu je ekvivalentem `is_assignable<T&, T&&>`. Přesunoutelné typy zahrnují referenční skalární typy a typy tříd, které mají buď operátory vygenerované kompilátorem, nebo uživatelsky definované operátory přiřazení přesunutí.

## <a name="is_move_constructible"></a>is_move_constructible

Testuje, zda typ obsahuje konstruktor Move.

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, který se má vyhodnotit

### <a name="remarks"></a>Poznámky

Predikát typu, který se vyhodnotí jako true, pokud typ *T* může být vytvořen pomocí operace přesunutí. Tento predikát je ekvivalentem `is_constructible<T, T&&>`.

## <a name="is_nothrow_move_assignable"></a>is_nothrow_move_assignable

Testuje, zda typ obsahuje operátor **přiřazení přesunu** .

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud *má typ s* operátorem přiřazení přesunutí, v opačném případě má hodnotu false.

## <a name="is_nothrow_swappable"></a>is_nothrow_swappable

```cpp
template <class T> struct is_nothrow_swappable;
```

## <a name="is_nothrow_swappable_with"></a>is_nothrow_swappable_with

```cpp
template <class T, class U> struct is_nothrow_swappable_with;
```

## <a name="is_swappable"></a>is_swappable

```cpp
template <class T> struct is_swappable;
```

## <a name="is_swappable_with"></a>is_swappable_with

```cpp
template <class T, class U> struct is_swappable_with;
```

## <a name="is_trivially_copy_assignable"></a>is_trivially_copy_assignable

Testuje, zda má typ operátor přiřazení triviální kopie.

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Š*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud typ *T* je třída, která má operátor přiřazení triviální kopie, v opačném případě obsahuje hodnotu false.

Konstruktor přiřazení pro třídu *t* je triviální, pokud je implicitně poskytnutý, třída *t* nemá žádné virtuální funkce, třída *t* nemá žádné virtuální základy, třídy všech nestatických datových členů typu třídy mají triviální přiřazení. operátory a třídy všech nestatických datových členů typu Array třídy mají operátory přiřazení triviální.

## <a name="is_trivially_move_assignable"></a>is_trivially_move_assignable

Testuje, zda má typ operátor přiřazení triviálního přesunutí.

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, *Pokud typ je* třída, která má operátor přiřazení triviálního přesunu, jinak obsahuje hodnotu false.

Operátor přiřazení přesunu pro *danou třídu je* triviální, pokud:

implicitně se poskytuje

Třída *ty* nemá žádné virtuální funkce.

Třída *ty* nemá žádné virtuální základy.

třídy všech nestatických datových členů typu třídy mají operátory přiřazení triviálního přesunutí.

třídy všech nestatických datových členů typu Array třídy mají operátory přiřazení triviálního přesunutí.

## <a name="is_trivially_move_constructible"></a>is_trivially_move_constructible

Testuje, zda typ obsahuje konstruktor triviálního přesunu.

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Ty*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance predikátu typu má hodnotu true, pokud *je typ,* který je třída, která má konstruktor triviálního přesunu, v opačném případě obsahuje hodnotu false.

Konstruktor přesunu pro třídu *ty* je triviální, pokud:

je implicitně deklarována

jeho typy parametrů jsou ekvivalentní k těm implicitní deklarace.

Třída *ty* nemá žádné virtuální funkce.

Třída *ty* nemá žádné virtuální základy.

Třída nemá žádné nestálé nestatické datové členy.

všechny přímé základny třídy *ty* mají konstruktory triviálního přesunu.

třídy všech nestatických datových členů typu třídy mají konstruktory triviálního přesunu.

třídy všech nestatických datových členů typu Array třídy mají konstruktory triviálního přesunu.

## <a name="see-also"></a>Viz také:

[<type_traits>](../standard-library/type-traits.md)
