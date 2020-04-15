---
title: scoped_allocator_adaptor – třída
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor::rebind Struct
- scoped_allocator/std::scoped_allocator_adaptor::allocate
- scoped_allocator/std::scoped_allocator_adaptor::construct
- scoped_allocator/std::scoped_allocator_adaptor::deallocate
- scoped_allocator/std::scoped_allocator_adaptor::destroy
- scoped_allocator/std::scoped_allocator_adaptor::inner_allocator
- scoped_allocator/std::scoped_allocator_adaptor::max_size
- scoped_allocator/std::scoped_allocator_adaptor::outer_allocator
- scoped_allocator/std::scoped_allocator_adaptor::select_on_container_copy_construction
helpviewer_keywords:
- std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor::allocate
- std::scoped_allocator_adaptor::construct
- std::scoped_allocator_adaptor::deallocate
- std::scoped_allocator_adaptor::destroy
- std::scoped_allocator_adaptor::inner_allocator
- std::scoped_allocator_adaptor::max_size
- std::scoped_allocator_adaptor::outer_allocator
- std::scoped_allocator_adaptor::select_on_container_copy_construction
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
ms.openlocfilehash: b08cf1858cb0f9bf4dc6201edc2502d48754ff77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373400"
---
# <a name="scoped_allocator_adaptor-class"></a>scoped_allocator_adaptor – třída

Představuje hnízdo alokátorů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Poznámky

Šablona třídy zapouzdřuje hnízdo jednoho nebo více alokátorů. Každá taková třída má nejkrajnější alokátor `outer_allocator_type`typu `Outer`, synonymum pro `scoped_allocator_adaptor` , což je veřejná základna objektu. `Outer`slouží k přidělení paměti, která má být použita kontejnerem. Můžete získat odkaz na tento alokátor základní `outer_allocator`objekt voláním .

Zbytek hnízda má `inner_allocator_type`typ . Vnitřní přidělování se používá k přidělení paměti pro prvky v rámci kontejneru. Můžete získat odkaz na uložený objekt tohoto `inner_allocator`typu voláním . Pokud `Inner...` není prázdný, `inner_allocator_type` `scoped_allocator_adaptor<Inner...>`má `inner_allocator` typ a označuje členský objekt. V `inner_allocator_type` opačném `scoped_allocator_adaptor<Outer>`případě `inner_allocator` má typ a označuje celý objekt.

Hnízdo se chová, jako by mělo libovolnou hloubku, a podle potřeby kopíruje svůj nejvnitřnější zapouzdřený alokátor.

Několik konceptů, které nejsou součástí viditelné rozhraní podpory při popisu chování této šablony třídy. *Nejvzdálenější přidělování* zprostředkovat všechna volání konstrukce a zničit metody. Je efektivně definován rekurzivní funkcí `OUTERMOST(X)`, `OUTERMOST(X)` kde je jedna z následujících.

- Pokud `X.outer_allocator()` je dobře `OUTERMOST(X)` tvarované, pak je `OUTERMOST(X.outer_allocator())`.

- V `OUTERMOST(X)` opačném `X`případě je .

Pro účely expozice jsou definovány tři typy:

|Typ|Popis|
|----------|-----------------|
|`Outermost`|Typ . `OUTERMOST(*this)`|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>Konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|Vytvoří `scoped_allocator_adaptor` objekt.|

### <a name="typedefs"></a>Typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`const_pointer`|Tento typ je synonymem `const_pointer` pro, který je `Outer`spojen s alokátorem .|
|`const_void_pointer`|Tento typ je synonymem `const_void_pointer` pro, který je `Outer`spojen s alokátorem .|
|`difference_type`|Tento typ je synonymem `difference_type` pro, který je `Outer`spojen s alokátorem .|
|`inner_allocator_type`|Tento typ je synonymem pro typ vnořeného adaptéru `scoped_allocator_adaptor<Inner...>`.|
|`outer_allocator_type`|Tento typ je synonymem pro typ základního `Outer`alokátoru .|
|`pointer`|Tento typ je synonymem pro `pointer` přidružené alokátoru . `Outer`|
|`propagate_on_container_copy_assignment`|Typ platí pouze `Outer_traits::propagate_on_container_copy_assignment` v případě, že platí nebo `inner_allocator_type::propagate_on_container_copy_assignment` platí.|
|`propagate_on_container_move_assignment`|Typ platí pouze `Outer_traits::propagate_on_container_move_assignment` v případě, že platí nebo `inner_allocator_type::propagate_on_container_move_assignment` platí.|
|`propagate_on_container_swap`|Typ platí pouze `Outer_traits::propagate_on_container_swap` v případě, že platí nebo `inner_allocator_type::propagate_on_container_swap` platí.|
|`size_type`|Tento typ je synonymem pro `size_type` přidružené alokátoru . `Outer`|
|`value_type`|Tento typ je synonymem pro `value_type` přidružené alokátoru . `Outer`|
|`void_pointer`|Tento typ je synonymem pro `void_pointer` přidružené alokátoru . `Outer`|

### <a name="structs"></a>Struktury

|Name (Název)|Popis|
|----------|-----------------|
|[scoped_allocator_adaptor::rebind Struct](#rebind_struct)|Definuje typ `Outer::rebind\<Other>::other` jako synonymum pro `scoped_allocator_adaptor\<Other, Inner...>`.|

### <a name="methods"></a>Metody

|Name (Název)|Popis|
|----------|-----------------|
|[allocate](#allocate)|Přiděluje paměť `Outer` pomocí alokátoru.|
|[Vytvořit](#construct)|Vytvoří objekt.|
|[Navrátit](#deallocate)|Zruší přidělení objektů pomocí vnějšího alokátoru.|
|[destroy](#destroy)|Zničí zadaný objekt.|
|[inner_allocator](#inner_allocator)|Načte odkaz na uložený `inner_allocator_type`objekt typu .|
|[max_size](#max_size)|Určuje maximální počet objektů, které mohou být přiděleny vnější přidělování.|
|[outer_allocator](#outer_allocator)|Načte odkaz na uložený `outer_allocator_type`objekt typu .|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Vytvoří nový `scoped_allocator_adaptor` objekt s každým uloženým objektem `select_on_container_copy_construction` přidělování inicializován voláním každého odpovídajícího alokátoru.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_as)||
|[operátor==](#op_eq_eq)||
|[operátor!=](#op_noeq)||

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<scoped_allocator>

**Obor názvů:** std

## <a name="scoped_allocator_adaptorallocate"></a><a name="allocate"></a>scoped_allocator_adaptor::přidělit

Přiděluje paměť `Outer` pomocí alokátoru.

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>Parametry

*Počet*\
Počet prvků, pro které má být přiděleno dostatečné úložiště.

*Nápovědy*\
Ukazatel, který může pomoci objektu přidělování vyhledáním adresy objektu přidělené před požadavkem.

### <a name="return-value"></a>Návratová hodnota

První členská `Outer_traits::allocate(outer_allocator(), count)`funkce vrátí . Druhá členská `Outer_traits::allocate(outer_allocator(), count, hint)`funkce vrátí .

## <a name="scoped_allocator_adaptorconstruct"></a><a name="construct"></a>scoped_allocator_adaptor::konstrukce

Vytvoří objekt.

```cpp
template <class Ty, class... Atypes>
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,
    tuple<Atypes1&&...>
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr,
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Ukazatel na umístění paměti, kde má být objekt vytvořen.

*Args*\
Seznam argumentů.

*První*\
Objekt prvního typu v páru.

*Druhé*\
Objekt druhého typu v páru.

*Právo*\
Existující objekt, který má být přesunut nebo zkopírován.

### <a name="remarks"></a>Poznámky

První metoda vytvoří objekt na *ptr* voláním `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`, kde `xargs...` je jeden z následujících.

- Pokud `uses_allocator<Ty, inner_allocator_type>` platí false, pak `xargs...` je `args...`.

- Pokud `uses_allocator<Ty, inner_allocator_type>` platí, `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` a platí, `xargs...` `allocator_arg, inner_allocator(), args...`pak je .

- Pokud `uses_allocator<Ty, inner_allocator_type>` platí, `is_constructible<Ty, args..., inner_allocator()>` a platí, `xargs...` `args..., inner_allocator()`pak je .

Druhá metoda vytvoří objekt dvojice na *ptr* `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)` `xargs...` voláním , kde `first...` je `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`upravena `xargs...` `second...` jako ve výše uvedeném seznamu a , kde je upravena jako ve výše uvedeném seznamu.

Třetí metoda se chová stejně jako `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.

Čtvrtá metoda se chová `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`stejně jako .

Pátá metoda se chová `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`stejně jako .

Šestá metoda se chová `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`stejně jako .

## <a name="scoped_allocator_adaptordeallocate"></a><a name="deallocate"></a>scoped_allocator_adaptor::deallocate

Zruší přidělení objektů pomocí vnějšího alokátoru.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Ukazatel na počáteční umístění objektů, které mají být přiděleny.

*Počet*\
Počet objektů navrátit.

## <a name="scoped_allocator_adaptordestroy"></a><a name="destroy"></a>scoped_allocator_adaptor::destroy

Zničí zadaný objekt.

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>Parametry

*Ptr*\
Ukazatel na objekt, který má být zničen.

### <a name="return-value"></a>Návratová hodnota

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="scoped_allocator_adaptorinner_allocator"></a><a name="inner_allocator"></a>scoped_allocator_adaptor::inner_allocator

Načte odkaz na uložený `inner_allocator_type`objekt typu .

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na uložený objekt `inner_allocator_type`typu .

## <a name="scoped_allocator_adaptormax_size"></a><a name="max_size"></a>scoped_allocator_adaptor::max_size

Určuje maximální počet objektů, které mohou být přiděleny vnější přidělování.

```cpp
size_type max_size();
```

### <a name="return-value"></a>Návratová hodnota

`Outer_traits::max_size(outer_allocator())`

## <a name="a-nameop_as--scoped_allocator_adaptoroperator"></a><a name="op_as">scoped_allocator_adaptor::operátor=

```cpp
scoped_allocator_adaptor& operator=(const scoped_allocator_adaptor&) = default;
scoped_allocator_adaptor& operator=(scoped_allocator_adaptor&&) = default;
```

## <a name="a-nameop_eq_eq--scoped_allocator_adaptoroperator"></a><a name="op_eq_eq">scoped_allocator_adaptor::operátor==

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator==(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="a-nameop_noeq--scoped_allocator_adaptoroperator"></a><a name="op_noeq">scoped_allocator_adaptor::operátor!=

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator!=(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="scoped_allocator_adaptorouter_allocator"></a><a name="outer_allocator"></a>scoped_allocator_adaptor::outer_allocator

Načte odkaz na uložený `outer_allocator_type`objekt typu .

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na uložený objekt `outer_allocator_type`typu .

## <a name="scoped_allocator_adaptorrebind-struct"></a><a name="rebind_struct"></a>scoped_allocator_adaptor::rebind Struct

Definuje typ `Outer::rebind\<Other>::other` jako synonymum pro `scoped_allocator_adaptor\<Other, Inner...>`.

strukturovat rebind{ typedef Other_traits::rebind\<Other>\<Other_alloc; typedef scoped_allocator_adaptor Other_alloc, Inner...> other; };

## <a name="scoped_allocator_adaptorscoped_allocator_adaptor-constructor"></a><a name="scoped_allocator_adaptor"></a>scoped_allocator_adaptor::scoped_allocator_adaptor konstruktor

Vytvoří `scoped_allocator_adaptor` objekt. Obsahuje také destruktor.

```cpp
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(Outer2&& al,
    const Inner&... rest) noexcept;

~scoped_allocator_adaptor();
```

### <a name="parameters"></a>Parametry

*Právo*\
Existující `scoped_allocator_adaptor`.

*Al*\
Existující přidělování, které má být použito jako vnější alokátor.

*Odpočinku*\
Seznam alokátorů, které mají být použity jako vnitřní alokátory.

### <a name="remarks"></a>Poznámky

První výchozí konstruktor vytvoří jeho uložené objekty přidělování. Každý z následujících tří konstruktorů vytvoří své uložené objekty alokátoru z odpovídajících objektů v *pravo*. Poslední konstruktor vytvoří jeho uložené objekty přidělování z odpovídající argumenty v seznamu argumentů.

## <a name="scoped_allocator_adaptorselect_on_container_copy_construction"></a><a name="select_on_container_copy_construction"></a>scoped_allocator_adaptor::select_on_container_copy_construction

Vytvoří nový `scoped_allocator_adaptor` objekt s každým uloženým objektem `select_on_container_copy_construction` přidělování inicializován voláním každého odpovídajícího alokátoru.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda efektivně `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`vrátí . Výsledkem je `scoped_allocator_adaptor` nový objekt s každým uloženým objektem `al.select_on_container_copy_construction()` přidělování inicializovaným voláním odpovídajícího alokátoru *al*.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)
