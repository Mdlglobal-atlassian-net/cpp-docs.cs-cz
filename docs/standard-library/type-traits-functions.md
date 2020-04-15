---
title: '&lt;type_traits&gt; funkce'
ms.date: 11/04/2016
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
ms.openlocfilehash: bc25c82629139c5bc2f6fa53d3555068374dca35
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367988"
---
# <a name="lttype_traitsgt-functions"></a>&lt;type_traits&gt; funkce

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_nothrow_swappable](#is_nothrow_swappable)|[is_nothrow_swappable_with](#is_nothrow_swappable_with)|
|[is_swappable](#is_swappable)|[is_swappable_with](#is_swappable_with)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|
|[is_trivially_move_assignable](#is_trivially_move_assignable)|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a><a name="is_assignable"></a>is_assignable

Testuje, zda lze hodnotu typu *Od* přiřadit typu *To.*

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parametry

*Chcete-li*\
Typ objektu, který přijímá přiřazení.

*Z*\
Typ objektu, který poskytuje hodnotu.

### <a name="remarks"></a>Poznámky

Nehodnocený `declval<To>() = declval<From>()` výraz musí být ve správném formátu. *Od* i *Do* musí být úplné typy, **void**nebo pole neznámé vázané.

## <a name="is_copy_assignable"></a><a name="is_copy_assignable"></a>is_copy_assignable

Testuje, zda typ má být zkopírován na přiřazení.

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>Parametry

*Ty (Ty)*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance typu predikátu platí, pokud typ *Ty* je třída, která má operátor přiřazení kopie, jinak obsahuje false. Odpovídá is_assignable\<Ty&, const Ty&>.

## <a name="is_copy_constructible"></a><a name="is_copy_constructible"></a>is_copy_constructible

Testy, pokud typ má konstruktor kopie.

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>Parametry

*Ty (Ty)*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance typu predikátu platí, pokud typ *Ty* je třída, která má konstruktor kopie, jinak obsahuje false.

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

## <a name="is_default_constructible"></a><a name="is_default_constructible"></a>is_default_constructible

Testy, pokud typ má výchozí konstruktor.

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>Parametry

*T*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance typu predikátu platí, pokud typ *T* je typ třídy, který má výchozí konstruktor, jinak obsahuje false. To odpovídá predikátu `is_constructible<T>`. Typ *T* musí být úplný typ, **void**nebo pole neznámé hospo-

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

## <a name="is_move_assignable"></a><a name="is_move_assignable"></a>is_move_assignable

Testuje, zda lze typ přesunout.

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>Parametry

*T*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Typ je přesunout přiřaditelný, pokud lze odkaz rvalue na typ přiřadit k odkazu na typ. Predikát typu je `is_assignable<T&, T&&>`ekvivalentní . Přesunout přiřaditelné typy zahrnují referenční skalární typy a typy tříd, které mají operátory přiřazení přesunutí generované kompilátorem nebo uživatelem definované.

## <a name="is_move_constructible"></a><a name="is_move_constructible"></a>is_move_constructible

Testuje, zda má typ konstruktor move.

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parametry

*T*\
Typ, který má být vyhodnocen

### <a name="remarks"></a>Poznámky

Typ predikátu, který vyhodnotí na true, pokud typ *T* lze sestavit pomocí operace přesunutí. Tento predikát `is_constructible<T, T&&>`je ekvivalentní .

## <a name="is_nothrow_move_assignable"></a><a name="is_nothrow_move_assignable"></a>is_nothrow_move_assignable

Testuje, zda má typ operátor přiřazení přesunutí **nothrow.**

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty (Ty)*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance typu predikátu platí, pokud typ *Ty* má operátor přiřazení nothrow move, jinak obsahuje false.

## <a name="is_nothrow_swappable"></a><a name="is_nothrow_swappable"></a>is_nothrow_swappable

```cpp
template <class T> struct is_nothrow_swappable;
```

## <a name="is_nothrow_swappable_with"></a><a name="is_nothrow_swappable_with"></a>is_nothrow_swappable_with

```cpp
template <class T, class U> struct is_nothrow_swappable_with;
```

## <a name="is_swappable"></a><a name="is_swappable"></a>is_swappable

```cpp
template <class T> struct is_swappable;
```

## <a name="is_swappable_with"></a><a name="is_swappable_with"></a>is_swappable_with

```cpp
template <class T, class U> struct is_swappable_with;
```

## <a name="is_trivially_copy_assignable"></a><a name="is_trivially_copy_assignable"></a>is_trivially_copy_assignable

Testuje, zda má typ operátor přiřazení trivial copy.

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parametry

*T*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance typu predikátu platí, pokud typ *T* je třída, která má operátor přiřazení trivial copy, jinak obsahuje false.

Konstruktor přiřazení pro třídu *T* je triviální, pokud je implicitně poskytnuta, třída *T* nemá žádné virtuální funkce, třída *T* nemá žádné virtuální základy, třídy všech nestatických datových členů typu třídy mají triviální operátory přiřazení a třídy všech nestatických datových členů typu třídy mají triviální operátory přiřazení.

## <a name="is_trivially_move_assignable"></a><a name="is_trivially_move_assignable"></a>is_trivially_move_assignable

Testuje, zda má typ triviální operátor přiřazení přesunutí.

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

*Ty (Ty)*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance typu predikátu platí, pokud typ *Ty* je třída, která má operátor přiřazení trivial move, jinak obsahuje false.

Operátor přiřazení přesunutí pro třídu *Ty* je triviální, pokud:

je implicitně poskytována

třída *Ty* nemá žádné virtuální funkce

třída *Ty* nemá žádné virtuální základny

třídy všech nestatických datových členů typu třídy mají triviální operátory přiřazení přesunutí

Třídy všech nestatických datových členů typového pole třídy mají triviální operátory přiřazení přesunutí

## <a name="is_trivially_move_constructible"></a><a name="is_trivially_move_constructible"></a>is_trivially_move_constructible

Testy, pokud má typ konstruktor trivial move.

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

*Ty (Ty)*\
Typ, na který chcete odeslat dotaz.

### <a name="remarks"></a>Poznámky

Instance typu predikátu platí, pokud typ *Ty* je třída, která má konstruktor trivial move, jinak obsahuje false.

Move konstruktor pro třídu *Ty* je triviální, pokud:

je implicitně deklarován

jeho typy parametrů jsou rovnocenné typům implicitní deklarace

třída *Ty* nemá žádné virtuální funkce

třída *Ty* nemá žádné virtuální základny

třída nemá žádné nevolatilní nestatické datové členy

všechny přímé základy třídy *Ty* mají triviální pohyb konstruktory

třídy všech nestatických datových členů typu třídy mají konstruktory triviální přesunout

třídy všech nestatických datových členů typového pole třídy mají konstruktory trivial move

## <a name="see-also"></a>Viz také

[<type_traits>](../standard-library/type-traits.md)
