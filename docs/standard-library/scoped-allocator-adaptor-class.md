---
title: scoped_allocator_adaptor – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62bdeeddf0e81cf017c49eac51ca0e2eaaf046c1
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104064"
---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor – třída

Představuje vnořených alokátorů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Poznámky

Třída šablony zapouzdřuje vnoření z jednoho nebo více alokátorů. Každá tato třída má nejkrajnější alokátoru typu `outer_allocator_type`, synonymum pro `Outer`, což je veřejné základ `scoped_allocator_adaptor` objektu. `Outer` slouží k přidělení paměti pro kontejner. Odkaz na tento základní objekt alokátoru lze získat voláním `outer_allocator`.

Zbývající část přivítat má typ `inner_allocator_type`. Vnitřní alokátoru slouží k přidělení paměti pro elementům v kontejneru. Odkaz na uložený objekt tohoto typu lze získat voláním `inner_allocator`. Pokud `Inner...` není prázdná, `inner_allocator_type` má typ `scoped_allocator_adaptor<Inner...>`, a `inner_allocator` označí objekt člena. V opačném případě `inner_allocator_type` má typ `scoped_allocator_adaptor<Outer>`, a `inner_allocator` označí celý objekt.

Přivítat se chová jako v případě, že má libovolné hloubky replikaci jeho vnitřní zapouzdřený objekt alokátoru, podle potřeby.

Výpomoc s několika koncepty, které nejsou součástí rozhraní viditelné popisující chování této třídy šablony. *Nejkrajnější allocator* zprostředkovává všechna volání konstrukce a zničení metody. Rekurzivní funkci účinně definuje ho `OUTERMOST(X)`, kde `OUTERMOST(X)` je jedním z následujících akcí.

- Pokud `X.outer_allocator()` je ve správném, pak `OUTERMOST(X)` je `OUTERMOST(X.outer_allocator())`.

- V opačném případě `OUTERMOST(X)` je `X`.

Tři typy jsou definovány pro účely budeme:

|Typ|Popis|
|----------|-----------------|
|`Outermost`|Typ `OUTERMOST(*this)`.|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>Konstruktory

|Název|Popis|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|Vytvoří `scoped_allocator_adaptor` objektu.|

### <a name="typedefs"></a>Typedefs

|Název|Popis|
|----------|-----------------|
|`const_pointer`|Tento typ je synonymum pro `const_pointer` , který je přidružen alokátoru `Outer`.|
|`const_void_pointer`|Tento typ je synonymum pro `const_void_pointer` , který je přidružen alokátoru `Outer`.|
|`difference_type`|Tento typ je synonymum pro `difference_type` , který je přidružen alokátoru `Outer`.|
|`inner_allocator_type`|Tento typ je synonymum pro typ vnořeného adaptér `scoped_allocator_adaptor<Inner...>`.|
|`outer_allocator_type`|Tento typ je synonymum pro typ alokátoru základní `Outer`.|
|`pointer`|Tento typ je synonymum pro `pointer` přidružené alokátoru `Outer`.|
|`propagate_on_container_copy_assignment`|Typ obsahuje hodnotu true pouze v případě `Outer_traits::propagate_on_container_copy_assignment` platí nebo `inner_allocator_type::propagate_on_container_copy_assignment` platí.|
|`propagate_on_container_move_assignment`|Typ obsahuje hodnotu true pouze v případě `Outer_traits::propagate_on_container_move_assignment` platí nebo `inner_allocator_type::propagate_on_container_move_assignment` platí.|
|`propagate_on_container_swap`|Typ obsahuje hodnotu true pouze v případě `Outer_traits::propagate_on_container_swap` platí nebo `inner_allocator_type::propagate_on_container_swap` platí.|
|`size_type`|Tento typ je synonymum pro `size_type` přidružené alokátoru `Outer`.|
|`value_type`|Tento typ je synonymum pro `value_type` přidružené alokátoru `Outer`.|
|`void_pointer`|Tento typ je synonymum pro `void_pointer` přidružené alokátoru `Outer`.|

### <a name="structs"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[scoped_allocator_adaptor::rebind – struktura](#rebind_struct)|Definuje typ `Outer::rebind\<Other>::other` jako synonymum pro `scoped_allocator_adaptor\<Other, Inner...>`.|

### <a name="methods"></a>Metody

|Název|Popis|
|----------|-----------------|
|[allocate](#allocate)|Přiděluje paměť pomocí `Outer` alokátoru.|
|[Konstrukce](#construct)|Vytvoří objekt.|
|[zrušit přidělení](#deallocate)|Zruší přidělení objektů pomocí vnější alokátoru.|
|[zrušení](#destroy)|Odstraní zadaný objekt.|
|[inner_allocator](#inner_allocator)|Získá odkaz na uložený objekt typu `inner_allocator_type`.|
|[max_size](#max_size)|Určuje maximální počet objektů, které mohou být přiděleny podle vnější alokátoru.|
|[outer_allocator](#outer_allocator)|Získá odkaz na uložený objekt typu `outer_allocator_type`.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Vytvoří novou `scoped_allocator_adaptor` objekt s každou uložený objekt alokátoru inicializován pomocí volání `select_on_container_copy_construction` pro každý odpovídající alokátoru.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<scoped_allocator – >

**Namespace:** std

## <a name="allocate"></a>  scoped_allocator_adaptor::allocate –

Přiděluje paměť pomocí `Outer` alokátoru.

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>Parametry

*Počet*<br/>
Počet elementů, u kterých má být přidělené dostatečné úložiště.

*pomocný parametr*<br/>
Ukazatel, který může pomoct objekt alokátoru, který vyhledává adresu objektu přidělena před žádost.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí `Outer_traits::allocate(outer_allocator(), count)`. Druhá členská funkce vrátí `Outer_traits::allocate(outer_allocator(), count, hint)`.

## <a name="construct"></a>  scoped_allocator_adaptor::Construct –

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

*ptr*<br/>
Ukazatel na umístění v paměti, kde má být vytvořen objekt.

*argumenty*<br/>
Seznam argumentů.

*první*<br/>
Objekt typu první v páru.

*Sekundy*<br/>
Objekt typu druhé v páru.

*doprava*<br/>
Existující objekt pro přesunutí nebo kopírování.

### <a name="remarks"></a>Poznámky

První metoda vytvoří objekt v *ptr* voláním `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`, kde `xargs...` je jedním z následujících akcí.

- Pokud `uses_allocator<Ty, inner_allocator_type>` obsahuje hodnotu false, pak `xargs...` je `args...`.

- Pokud `uses_allocator<Ty, inner_allocator_type>` platí, a `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` obsahuje hodnotu true, pak `xargs...` je `allocator_arg, inner_allocator(), args...`.

- Pokud `uses_allocator<Ty, inner_allocator_type>` platí, a `is_constructible<Ty, args..., inner_allocator()>` obsahuje hodnotu true, pak `xargs...` je `args..., inner_allocator()`.

Druhá metoda vytvoří objekt dvojice v *ptr* voláním `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`, kde `xargs...` je `first...` upravovat stejně jako v seznamu výše a `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`, kde `xargs...` je `second...` upravit stejně jako v seznamu výše.

Třetí metoda chová se stejně jako `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.

Čtvrtá metoda chová se stejně jako `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.

Pátý metoda chová se stejně jako `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.

Šestý metoda chová se stejně jako `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.

## <a name="deallocate"></a>  scoped_allocator_adaptor::deallocate –

Zruší přidělení objektů pomocí vnější alokátoru.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Ukazatel na počáteční umístění objekty, které chcete být navrácena.

*Počet*<br/>
Počet objektů, které chcete uvolnit.

## <a name="destroy"></a>  scoped_allocator_adaptor::Destroy –

Odstraní zadaný objekt.

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Ukazatel na objekt, který se má zničit.

### <a name="return-value"></a>Návratová hodnota

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="inner_allocator"></a>  scoped_allocator_adaptor::inner_allocator –

Získá odkaz na uložený objekt typu `inner_allocator_type`.

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na uložený objekt typu `inner_allocator_type`.

## <a name="max_size"></a>  scoped_allocator_adaptor::max_size –

Určuje maximální počet objektů, které mohou být přiděleny podle vnější alokátoru.

```cpp
size_type max_size();
```

### <a name="return-value"></a>Návratová hodnota

`Outer_traits::max_size(outer_allocator())`

## <a name="outer_allocator"></a>  scoped_allocator_adaptor::outer_allocator –

Získá odkaz na uložený objekt typu `outer_allocator_type`.

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Odkaz na uložený objekt typu `outer_allocator_type`.

## <a name="rebind_struct"></a>  scoped_allocator_adaptor::rebind – struktura

Definuje typ `Outer::rebind\<Other>::other` jako synonymum pro `scoped_allocator_adaptor\<Other, Inner...>`.

Struktura obnovení vazby {typedef Other_traits::rebind\<jiných > Other_alloc; scoped_allocator_adaptor – definice typedef\<Other_alloc, vnitřní... > ostatní;};

## <a name="scoped_allocator_adaptor"></a>  scoped_allocator_adaptor::scoped_allocator_adaptor – konstruktor

Vytvoří `scoped_allocator_adaptor` objektu.

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
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Existující `scoped_allocator_adaptor`.

*Al*<br/>
Existující alokátoru pro použití jako vnější alokátoru.

*REST*<br/>
Seznam alokátorů má být použit jako vnitřní alokátorů.

### <a name="remarks"></a>Poznámky

První výchozí konstruktor zkonstruuje jeho objekty uložené přidělování. Všechny následující tři konstruktory vytvoří její objekty uložené přidělování z odpovídajícími objekty ve *správné*. Poslední konstruktor vytvoří její objekty uložené přidělování z odpovídajícího argumenty v seznamu argumentů.

## <a name="select_on_container_copy_construction"></a>  scoped_allocator_adaptor::select_on_container_copy_construction –

Vytvoří novou `scoped_allocator_adaptor` objekt s každou uložený objekt alokátoru inicializován pomocí volání `select_on_container_copy_construction` pro každý odpovídající alokátoru.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí efektivně `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`. Výsledkem je nový `scoped_allocator_adaptor` objekt s každou uložený objekt alokátoru inicializován pomocí volání `al.select_on_container_copy_construction()` pro odpovídající allocator *al*.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
