---
title: allocator_traits – třída
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator_traits
- memory/std::allocator_traits::propagate_on_container_move_assignment
- memory/std::allocator_traits::const_pointer
- memory/std::allocator_traits::propagate_on_container_swap
- memory/std::allocator_traits::propagate_on_container_copy_assignment
- memory/std::allocator_traits::difference_type
- memory/std::allocator_traits::allocator_type
- memory/std::allocator_traits::value_type
- memory/std::allocator_traits::pointer
- memory/std::allocator_traits::size_type
- memory/std::allocator_traits::const_void_pointer
- memory/std::allocator_traits::void_pointer
- memory/std::allocator_traits::allocate
- memory/std::allocator_traits::construct
- memory/std::allocator_traits::deallocate
- memory/std::allocator_traits::destroy
- memory/std::allocator_traits::max_size
- memory/std::allocator_traits::select_on_container_copy_construction
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
helpviewer_keywords:
- std::allocator_traits [C++]
- std::allocator_traits [C++], propagate_on_container_move_assignment
- std::allocator_traits [C++], const_pointer
- std::allocator_traits [C++], propagate_on_container_swap
- std::allocator_traits [C++], propagate_on_container_copy_assignment
- std::allocator_traits [C++], difference_type
- std::allocator_traits [C++], allocator_type
- std::allocator_traits [C++], value_type
- std::allocator_traits [C++], pointer
- std::allocator_traits [C++], size_type
- std::allocator_traits [C++], const_void_pointer
- std::allocator_traits [C++], void_pointer
- std::allocator_traits [C++], allocate
- std::allocator_traits [C++], construct
- std::allocator_traits [C++], deallocate
- std::allocator_traits [C++], destroy
- std::allocator_traits [C++], max_size
- std::allocator_traits [C++], select_on_container_copy_construction
ms.openlocfilehash: 470b3086b4bdfa776558122eda9e496fa6c4bcdc
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690065"
---
# <a name="allocator_traits-class"></a>allocator_traits – třída

Šablona třídy popisuje objekt, který doplňuje *typ přidělování*. Typ přidělování je libovolný typ, který popisuje objekt přidělování, který se používá ke správě přiděleného úložiště. Konkrétně pro jakýkoli typ přidělování `Alloc` můžete pomocí `allocator_traits<Alloc>` určit všechny informace, které jsou vyžadovány kontejnerem s povoleným přidělováním. Další informace najdete v tématu výchozí [Třída přidělování](../standard-library/allocator-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Alloc>
    class allocator_traits;
```

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|`allocator_type`|Tento typ je synonymum pro parametr šablony `Alloc`.|
|`const_pointer`|Tento typ je `Alloc::const_pointer`, pokud je typ ve správném formátu; v opačném případě je tento typ `pointer_traits<pointer>::rebind<const value_type>`.|
|`const_void_pointer`|Tento typ je `Alloc::const_void_pointer`, pokud je typ ve správném formátu; v opačném případě je tento typ `pointer_traits<pointer>::rebind<const void>`.|
|`difference_type`|Tento typ je `Alloc::difference_type`, pokud je typ ve správném formátu; v opačném případě je tento typ `pointer_traits<pointer>::difference_type`.|
|`pointer`|Tento typ je `Alloc::pointer`, pokud je typ ve správném formátu; v opačném případě je tento typ `value_type *`.|
|`propagate_on_container_copy_assignment`|Tento typ je `Alloc::propagate_on_container_copy_assignment`, pokud je typ ve správném formátu; v opačném případě je tento typ `false_type`.|
|`propagate_on_container_move_assignment`|Tento typ je `Alloc::propagate_on_container_move_assignment`, pokud je typ ve správném formátu; v opačném případě je tento typ `false_type`. Pokud typ drží hodnotu true, kontejner s povoleným přidělováním zkopíruje svůj uložený Alokátor na přiřazení přesunutí.|
|`propagate_on_container_swap`|Tento typ je `Alloc::propagate_on_container_swap`, pokud je typ ve správném formátu; v opačném případě je tento typ `false_type`. Pokud typ drží hodnotu true, kontejner s povoleným přidělováním zahodí svůj uložený Alokátor na swap.|
|`size_type`|Tento typ je `Alloc::size_type`, pokud je typ ve správném formátu; v opačném případě je tento typ `make_unsigned<difference_type>::type`.|
|`value_type`|Tento typ je synonymem pro `Alloc::value_type`.|
|`void_pointer`|Tento typ je `Alloc::void_pointer`, pokud je typ ve správném formátu; v opačném případě je tento typ `pointer_traits<pointer>::rebind<void>`.|

### <a name="static-methods"></a>Statické metody

Následující statické metody volají odpovídající metodu pro daný parametr přidělování.

|||
|-|-|
|[allocate](#allocate)|Statická metoda, která přiděluje paměť pomocí zadaného parametru přidělování.|
|[Contains](#construct)|Statická metoda, která používá zadané přidělování k vytvoření objektu.|
|[uvolnit](#deallocate)|Statická metoda, která používá zadané přidělování k navrácení zadaného počtu objektů.|
|[způsobit](#destroy)|Statická metoda, která používá zadané přidělování pro volání destruktoru u objektu bez zrušení přidělení paměti.|
|[max_size](#max_size)|Statická metoda, která používá zadané přidělování k určení maximálního počtu objektů, které se dají přidělit.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Statická metoda, která volá `select_on_container_copy_construction` v zadaném přidělování.|

### <a name="allocate"></a>FISIM

Statická metoda, která přiděluje paměť pomocí zadaného parametru přidělování.

```cpp
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```

#### <a name="parameters"></a>Parametry

*al* \
Objekt přidělování.

*počet* \
Počet prvků, které mají být přiděleny.

\ *nápovědy*
@No__t_0, která může pomoci objektu přidělování v souladu s požadavkem na úložiště hledáním adresy přiděleného objektu před požadavkem. Ukazatel s hodnotou null je považován za nepoužitou nápovědu.

#### <a name="return-value"></a>Návratová hodnota

Každá metoda vrací ukazatel na přidělený objekt.

První statická metoda vrací `al.allocate(count)`.

Druhá metoda vrátí `al.allocate(count, hint)`, pokud je tento výraz dobře vytvořen; v opačném případě vrátí `al.allocate(count)`.

### <a name="construct"></a>Contains

Statická metoda, která používá zadané přidělování k vytvoření objektu.

```cpp
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```

#### <a name="parameters"></a>Parametry

*al* \
Objekt přidělování.

\ *PTR*
Ukazatel na umístění, kde má být objekt vytvořen.

\ *argumentů*
Seznam argumentů, které jsou předány konstruktoru objektu.

#### <a name="remarks"></a>Poznámky

Statická členská funkce volá `al.construct(ptr, args...)`, pokud je výraz dobře vytvořený; v opačném případě vyhodnocuje `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)`.

### <a name="deallocate"></a>uvolnit

Statická metoda, která používá zadané přidělování k navrácení zadaného počtu objektů.

```cpp
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```

#### <a name="parameters"></a>Parametry

*al* \
Objekt přidělování.

\ *PTR*
Ukazatel na počáteční umístění objektů, které mají být přiděleny.

*počet* \
Počet objektů, které mají být přiděleny.

#### <a name="remarks"></a>Poznámky

Tato metoda volá `al.deallocate(ptr, count)`.

Tato metoda nevyvolává nic.

### <a name="destroy"></a>způsobit

Statická metoda, která používá zadané přidělování pro volání destruktoru u objektu bez zrušení přidělení paměti.

```cpp
template <class Uty>
    static void destroy(Alloc& al, Uty* ptr);
```

#### <a name="parameters"></a>Parametry

*al* \
Objekt přidělování.

\ *PTR*
Ukazatel na umístění objektu.

#### <a name="remarks"></a>Poznámky

Tato metoda volá `al.destroy(ptr)`, pokud je tento výraz dobře vytvořen; v opačném případě vyhodnocuje `ptr->~Uty()`.

### <a name="max_size"></a>max_size

Statická metoda, která používá zadané přidělování k určení maximálního počtu objektů, které se dají přidělit.

```cpp
static size_type max_size(const Alloc& al);
```

#### <a name="parameters"></a>Parametry

*al* \
Objekt přidělování.

#### <a name="remarks"></a>Poznámky

Tato metoda vrací `al.max_size()`, pokud je tento výraz ve správném formátu; v opačném případě vrátí `numeric_limits<size_type>::max()`.

### <a name="select_on_container_copy_construction"></a>select_on_container_copy_construction

Statická metoda, která volá `select_on_container_copy_construction` v zadaném přidělování.

```cpp
static Alloc select_on_container_copy_construction(const Alloc& al);
```

#### <a name="parameters"></a>Parametry

*al* \
Objekt přidělování.

#### <a name="return-value"></a>Návratová hodnota

Tato metoda vrací `al.select_on_container_copy_construction()`, pokud je tento typ dobře vytvořen; v opačném případě vrátí *Al*.

#### <a name="remarks"></a>Poznámky

Tato metoda slouží k určení přidělování při sestavení přidruženého kontejneru.
