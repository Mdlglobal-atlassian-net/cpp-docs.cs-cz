---
title: allocator_traits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
author: corob-msft
ms.author: corob
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
ms.workload:
- cplusplus
ms.openlocfilehash: fb00f7205dcb470785c9682335341ca07935aae5
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110435"
---
# <a name="allocatortraits-class"></a>allocator_traits – třída

Třída šablony popisuje objekt, který doplňuje *typ alokátoru*. Typ alokátoru, který je libovolný typ, který popisuje objekt alokátoru, který se používá pro správu přidělené úložiště. Konkrétně pro jakýkoli typ alokátoru `Alloc`, můžete použít `allocator_traits<Alloc>` určit všechny informace, které je potřeba v kontejneru povoleným přidělováním. Další informace najdete v tématu výchozí [Allocator – třída](../standard-library/allocator-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Alloc>
class allocator_traits;
```

### <a name="typedefs"></a>Typedefs

|Název|Popis|
|----------|-----------------|
|`allocator_traits::allocator_type`|Tento typ je synonymum pro parametr šablony `Alloc`.|
|`allocator_traits::const_pointer`|Tento typ je `Alloc::const_pointer`v případě, že typ je ve správném formátu; v opačném případě tento typ je `pointer_traits<pointer>::rebind<const value_type>`.|
|`allocator_traits::const_void_pointer`|Tento typ je `Alloc::const_void_pointer`v případě, že typ je ve správném formátu; v opačném případě tento typ je `pointer_traits<pointer>::rebind<const void>`.|
|`allocator_traits::difference_type`|Tento typ je `Alloc::difference_type`v případě, že typ je ve správném formátu; v opačném případě tento typ je `pointer_traits<pointer>::difference_type`.|
|`allocator_traits::pointer`|Tento typ je `Alloc::pointer`v případě, že typ je ve správném formátu; v opačném případě tento typ je `value_type *`.|
|`allocator_traits::propagate_on_container_copy_assignment`|Tento typ je `Alloc::propagate_on_container_copy_assignment`v případě, že typ je ve správném formátu; v opačném případě tento typ je `false_type`.|
|`allocator_traits::propagate_on_container_move_assignment`|Tento typ je `Alloc::propagate_on_container_move_assignment`v případě, že typ je ve správném formátu; v opačném případě tento typ je `false_type`. Pokud typ obsahuje hodnotu true, zkopíruje kontejnerem s povoleným přidělováním jeho uložené přidělování na přiřazení pro přesun.|
|`allocator_traits::propagate_on_container_swap`|Tento typ je `Alloc::propagate_on_container_swap`v případě, že typ je ve správném formátu; v opačném případě tento typ je `false_type`. Pokud typ obsahuje hodnotu true, kontejnerem s povoleným přidělováním Zamění jeho uložené přidělování na prohození.|
|`allocator_traits::size_type`|Tento typ je `Alloc::size_type`v případě, že typ je ve správném formátu; v opačném případě tento typ je `make_unsigned<difference_type>::type`.|
|`allocator_traits::value_type`|Tento typ je synonymum pro `Alloc::value_type`.|
|`allocator_traits::void_pointer`|Tento typ je `Alloc::void_pointer`v případě, že typ je ve správném formátu; v opačném případě tento typ je `pointer_traits<pointer>::rebind<void>`.|

### <a name="static-methods"></a>Statické metody

Následující statické metody odpovídající metodu volat parametr daného alokátoru.

|Název|Popis|
|----------|-----------------|
|[allocate](#allocate)|Statická metoda, která přiděluje paměť pomocí parametru dané alokátoru.|
|[Konstrukce](#construct)|Statická metoda, která používá alokátorem určeným pro vytvoření objektu.|
|[zrušit přidělení](#deallocate)|Statická metoda, která používá alokátorem určeným se uvolnit zadaný počet objektů.|
|[zrušení](#destroy)|Statická metoda, která používá alokátorem určeným pro volání destruktoru objektu bez rušení přidělení paměti.|
|[max_size](#max_size)|Statická metoda, která používá alokátorem určeným pro určení maximální počet objektů, které mohou být přiděleny.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Statická metoda, která volá `select_on_container_copy_construction` na zadaného alokátoru.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** std

## <a name="allocate"></a>  allocator_traits::allocate –

Statická metoda, která přiděluje paměť pomocí parametru dané alokátoru.

```cpp
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Objekt alokátoru.

*Počet*<br/>
Počet prvků, které mají přidělit.

*pomocný parametr*<br/>
A `const_pointer` objekt alokátoru, které může pomáhají při neodpovídajících žádosti o úložiště vyhledáním adresu přiděleného objektu před požadavku. Žádné pomocný parametr je považován za ukazatel s hodnotou null.

### <a name="return-value"></a>Návratová hodnota

Každá metoda vrací ukazatel na přidělený objekt.

Vrátí první statickou metodu `al.allocate(count)`.

Druhá metoda vrací `al.allocate(count, hint)`, pokud výraz je dobře vytvořen; v opačném případě vrátí `al.allocate(count)`.

## <a name="construct"></a>  allocator_traits::Construct

Statická metoda, která používá alokátorem určeným pro vytvoření objektu.

```cpp
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Objekt alokátoru.

*ptr*<br/>
Ukazatel na umístění, kde má být vytvořen objekt.

*argumenty*<br/>
Seznam argumentů, která je předána do konstruktoru objektu.

### <a name="remarks"></a>Poznámky

Volání funkce statický člen `al.construct(ptr, args...)`, pokud výraz je dobře vytvořen; v opačném případě je vyhodnocen jako `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)`.

## <a name="deallocate"></a>  allocator_traits::deallocate –

Statická metoda, která používá alokátorem určeným se uvolnit zadaný počet objektů.

```cpp
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Objekt alokátoru.

*ptr*<br/>
Ukazatel na počáteční umístění objekty, které chcete být navrácena.

*Počet*<br/>
Počet objektů, které chcete uvolnit.

### <a name="remarks"></a>Poznámky

Tato metoda volá `al.deallocate(ptr, count)`.

Tato metoda vyvolá žádnou akci.

## <a name="destroy"></a>  allocator_traits::Destroy –

Statická metoda, která používá alokátorem určeným pro volání destruktoru objektu bez rušení přidělení paměti.

```cpp
template <class Uty>
static void destroy(Alloc& al, Uty* ptr);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Objekt alokátoru.

*ptr*<br/>
Ukazatel na umístění objektu.

### <a name="remarks"></a>Poznámky

Tato metoda volá `al.destroy(ptr)`, pokud výraz je dobře vytvořen; v opačném případě je vyhodnocen jako `ptr->~Uty()`.

## <a name="max_size"></a>  allocator_traits::max_size –

Statická metoda, která používá alokátorem určeným pro určení maximální počet objektů, které mohou být přiděleny.

```cpp
static size_type max_size(const Alloc& al);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Objekt alokátoru.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí `al.max_size()`, pokud výraz je dobře vytvořen; v opačném případě vrátí `numeric_limits<size_type>::max()`.

## <a name="select_on_container_copy_construction"></a>  allocator_traits::select_on_container_copy_construction –

Statická metoda, která volá `select_on_container_copy_construction` na zadaného alokátoru.

```cpp
static Alloc select_on_container_copy_construction(const Alloc& al);
```

### <a name="parameters"></a>Parametry

*Al*<br/>
Objekt alokátoru.

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí `al.select_on_container_copy_construction()`, pokud se, že typ je dobře vytvořen; v opačném případě vrátí *al*.

### <a name="remarks"></a>Poznámky

Tato metoda se používá k určení přidělování při přiřazeným kontejnerem je vytvořena kopie.

## <a name="see-also"></a>Viz také:

[\<paměť >](../standard-library/memory.md)<br/>
[pointer_traits – struktura](../standard-library/pointer-traits-struct.md)<br/>
[scoped_allocator_adaptor – třída](../standard-library/scoped-allocator-adaptor-class.md)<br/>
