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
ms.openlocfilehash: 1fb2842df50b0e803419e3cccdeb921c9b4fa591
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458014"
---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor – třída

Představuje vnoření přidělování.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Poznámky

Třída šablony zapouzdřuje vnoření jednoho nebo více přidělování. Každá taková třída má nejvzdálenější přidělující typ `outer_allocator_type`, synonymum pro `Outer`, což je veřejný základ `scoped_allocator_adaptor` objektu. `Outer`slouží k přidělení paměti, kterou má použít kontejner. Odkaz na tento objekt základu přidělování získáte voláním metody `outer_allocator`.

Zbytek vnořování má typ `inner_allocator_type`. Vnitřní Alokátor se používá k přidělení paměti pro prvky v rámci kontejneru. Můžete získat odkaz na uložený objekt tohoto typu voláním `inner_allocator`. Pokud `Inner...` není prázdné, `inner_allocator_type` má typ `scoped_allocator_adaptor<Inner...>`a `inner_allocator` určí členský objekt. Jinak má typ `scoped_allocator_adaptor<Outer>` a`inner_allocator` určí celý objekt. `inner_allocator_type`

Vnořování se chová, jako by měla libovolnou hloubku a replikuje své nejvnitřnější zapouzdřený přidělování podle potřeby.

Několik konceptů, které nejsou součástí podpory rozhraní Visible v popisu chování této třídy šablony. *Vnější přidělování* vypravuje všechna volání metod konstrukce a zničení. Je efektivně definováno rekurzivní funkcí `OUTERMOST(X)`, kde `OUTERMOST(X)` je jedna z následujících.

- Pokud `X.outer_allocator()` je ve správném formátu, `OUTERMOST(X)` pak `OUTERMOST(X.outer_allocator())`je.

- V opačném `X`případě je.`OUTERMOST(X)`

Tři typy jsou definovány pro Exposition v zájmu:

|type|Popis|
|----------|-----------------|
|`Outermost`|Typ `OUTERMOST(*this)`.|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>Konstruktory

|Name|Popis|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|`scoped_allocator_adaptor` Vytvoří objekt.|

### <a name="typedefs"></a>Typedefs

|Name|Popis|
|----------|-----------------|
|`const_pointer`|Tento typ je synonymem pro `const_pointer` , který je přidružen k přidělování. `Outer`|
|`const_void_pointer`|Tento typ je synonymem pro `const_void_pointer` , který je přidružen k přidělování. `Outer`|
|`difference_type`|Tento typ je synonymem pro `difference_type` , který je přidružen k přidělování. `Outer`|
|`inner_allocator_type`|Tento typ je synonymum pro typ vnořeného adaptéru `scoped_allocator_adaptor<Inner...>`.|
|`outer_allocator_type`|Tento typ je synonymum pro typ základního přidělování `Outer`.|
|`pointer`|Tento typ je synonymem `pointer` asociovaného s přidělováním. `Outer`|
|`propagate_on_container_copy_assignment`|Typ drží hodnotu true pouze v `Outer_traits::propagate_on_container_copy_assignment` případě, že `inner_allocator_type::propagate_on_container_copy_assignment` má hodnotu true nebo má hodnotu true.|
|`propagate_on_container_move_assignment`|Typ drží hodnotu true pouze v `Outer_traits::propagate_on_container_move_assignment` případě, že `inner_allocator_type::propagate_on_container_move_assignment` má hodnotu true nebo má hodnotu true.|
|`propagate_on_container_swap`|Typ drží hodnotu true pouze v `Outer_traits::propagate_on_container_swap` případě, že `inner_allocator_type::propagate_on_container_swap` má hodnotu true nebo má hodnotu true.|
|`size_type`|Tento typ je synonymem `size_type` asociovaného s přidělováním. `Outer`|
|`value_type`|Tento typ je synonymem `value_type` asociovaného s přidělováním. `Outer`|
|`void_pointer`|Tento typ je synonymem `void_pointer` asociovaného s přidělováním. `Outer`|

### <a name="structs"></a>Struktury

|Name|Popis|
|----------|-----------------|
|[scoped_allocator_adaptor:: Rebind – struktura](#rebind_struct)|Definuje typ `Outer::rebind\<Other>::other` jako synonymum pro `scoped_allocator_adaptor\<Other, Inner...>`.|

### <a name="methods"></a>Metody

|Name|Popis|
|----------|-----------------|
|[allocate](#allocate)|Přidělí paměť pomocí `Outer` přidělujícího modulu.|
|[Contains](#construct)|Vytvoří objekt.|
|[uvolnit](#deallocate)|Zruší přidělení objektů pomocí vnějšího přidělování.|
|[způsobit](#destroy)|Odstraní zadaný objekt.|
|[inner_allocator](#inner_allocator)|Načte odkaz na uložený objekt typu `inner_allocator_type`.|
|[max_size](#max_size)|Určuje maximální počet objektů, které mohou být přiděleny vnějším přidělováním.|
|[outer_allocator](#outer_allocator)|Načte odkaz na uložený objekt typu `outer_allocator_type`.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Vytvoří nový `scoped_allocator_adaptor` objekt s každým uloženým objektem přidělování inicializovaným `select_on_container_copy_construction` voláním pro každý odpovídající Alokátor.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_as)||
|[operator==](#op_eq_eq)||
|[operator!=](#op_noeq)||

## <a name="requirements"></a>Požadavky

**Hlavička:** \<scoped_allocator >

**Obor názvů:** std

## <a name="allocate"></a>scoped_allocator_adaptor:: allocate

Přidělí paměť pomocí `Outer` přidělujícího modulu.

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>Parametry

*výpočtu*\
Počet prvků, pro které má být přiděleno dostatečné úložiště.

*#c0*\
Ukazatel, který může pomoci objektu přidělování tím, že hledá adresu objektu přiděleného před požadavkem.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí `Outer_traits::allocate(outer_allocator(), count)`. Druhá členská funkce vrátí `Outer_traits::allocate(outer_allocator(), count, hint)`.

## <a name="construct"></a>scoped_allocator_adaptor:: Construct

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

*střed*\
Ukazatel na umístění paměti, kde má být objekt vytvořen.

*argumentů*\
Seznam argumentů.

*první*\
Objekt prvního typu v páru.

*první*\
Objekt druhého typu v páru.

*Kliknutím*\
Existující objekt k přesunutí nebo zkopírování.

### <a name="remarks"></a>Poznámky

První metoda vytvoří objekt na *PTR* voláním `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`, kde `xargs...` je jedna z následujících.

- Pokud `uses_allocator<Ty, inner_allocator_type>` má hodnotu false, `xargs...` pak `args...`je.

- Pokud `uses_allocator<Ty, inner_allocator_type>` drží hodnotu true a `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` má hodnotu true, `xargs...` pak `allocator_arg, inner_allocator(), args...`je.

- Pokud `uses_allocator<Ty, inner_allocator_type>` drží hodnotu true a `is_constructible<Ty, args..., inner_allocator()>` má hodnotu true, `xargs...` pak `args..., inner_allocator()`je.

Druhá metoda vytvoří dvojici objektu na *PTR* `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`voláním, kde `xargs...` `xargs...` je `first...` upravena jako v seznamu výše, a `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`tam, kde je `second...` upraven jako v seznamu výše.

Třetí metoda se chová stejně jako `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.

Čtvrtá metoda se chová stejně jako `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.

Pátá metoda se chová stejně jako `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.

Šestá metoda se chová stejně jako `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.

## <a name="deallocate"></a>scoped_allocator_adaptor::d eallocate

Zruší přidělení objektů pomocí vnějšího přidělování.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Parametry

*střed*\
Ukazatel na počáteční umístění objektů, které mají být přiděleny.

*výpočtu*\
Počet objektů, které mají být přiděleny.

## <a name="destroy"></a>scoped_allocator_adaptor::d estroy

Odstraní zadaný objekt.

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>Parametry

*střed*\
Ukazatel na objekt, který má být zničen.

### <a name="return-value"></a>Návratová hodnota

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="inner_allocator"></a>scoped_allocator_adaptor::inner_allocator

Načte odkaz na uložený objekt typu `inner_allocator_type`.

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na uložený objekt typu `inner_allocator_type`.

## <a name="max_size"></a>scoped_allocator_adaptor::max_size

Určuje maximální počet objektů, které mohou být přiděleny vnějším přidělováním.

```cpp
size_type max_size();
```

### <a name="return-value"></a>Návratová hodnota

`Outer_traits::max_size(outer_allocator())`

## <a name="a-nameopas--scopedallocatoradaptoroperator"></a><a name="op_as">scoped_allocator_adaptor:: operator =

```cpp
scoped_allocator_adaptor& operator=(const scoped_allocator_adaptor&) = default;
scoped_allocator_adaptor& operator=(scoped_allocator_adaptor&&) = default;
```

## <a name="a-nameopeqeq--scopedallocatoradaptoroperator"></a><a name="op_eq_eq">scoped_allocator_adaptor:: operator = = – operátor

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator==(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="a-nameopnoeq--scopedallocatoradaptoroperator"></a><a name="op_noeq">scoped_allocator_adaptor:: operator! =

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator!=(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="outer_allocator"></a>scoped_allocator_adaptor::outer_allocator

Načte odkaz na uložený objekt typu `outer_allocator_type`.

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na uložený objekt typu `outer_allocator_type`.

## <a name="rebind_struct"></a>scoped_allocator_adaptor:: Rebind – struktura

Definuje typ `Outer::rebind\<Other>::other` jako synonymum pro `scoped_allocator_adaptor\<Other, Inner...>`.

znovu navázání struktury {typedef Other_traits::\<Rebind jiné > Other_alloc;\<typedef scoped_allocator_adaptor Other_alloc, Inner... > jiné; };

## <a name="scoped_allocator_adaptor"></a>scoped_allocator_adaptor:: scoped_allocator_adaptor – konstruktor

`scoped_allocator_adaptor` Vytvoří objekt. Zahrnuje také destruktor.

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

*Kliknutím*\
Existující `scoped_allocator_adaptor`.

*VŠ*\
Existující Alokátor, který se má použít jako vnější přidělování.

*REST*\
Seznam přidělování, která se mají používat jako vnitřní přidělování.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří výchozí konstrukce svých uložených objektů přidělování. Každý z následujících tří konstruktorů sestaví své uložené objekty přidělování z odpovídajících objektů *vpravo*. Poslední konstruktor vytvoří své uložené objekty přidělování z odpovídajících argumentů v seznamu argumentů.

## <a name="select_on_container_copy_construction"></a>scoped_allocator_adaptor::select_on_container_copy_construction

Vytvoří nový `scoped_allocator_adaptor` objekt s každým uloženým objektem přidělování inicializovaným `select_on_container_copy_construction` voláním pro každý odpovídající Alokátor.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda efektivně vrátí `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`. Výsledkem je nový `scoped_allocator_adaptor` objekt s každým uloženým objektem přidělování inicializovaným voláním `al.select_on_container_copy_construction()` pro odpovídající modul přidělování *Al*.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
