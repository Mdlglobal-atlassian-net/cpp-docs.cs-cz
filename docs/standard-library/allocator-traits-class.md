---
title: allocator_traits – třída | Microsoft Docs
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
ms.openlocfilehash: be3b8fc232c6d692dd6e4f80018ab571e4e0cb34
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="allocatortraits-class"></a>allocator_traits – třída

Šablony třídy popisuje objekt, který nahrazuje *allocator typu*. Typ přidělení je žádný typ, který popisuje allocator objekt, který se používá pro správu, přidělit úložiště. Konkrétně pro jakýkoli typ allocator `Alloc`, můžete použít `allocator_traits<Alloc>` k určení veškeré informace, které je potřeba kontejner allocator povolena. Další informace najdete v tématu výchozí [allocator – třída](../standard-library/allocator-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class Alloc>
class allocator_traits;
```

### <a name="typedefs"></a>Typedefs

|Název|Popis|
|----------|-----------------|
|`allocator_traits::allocator_type`|Tento typ je synonymum pro parametr šablony `Alloc`.|
|`allocator_traits::const_pointer`|Tento typ je `Alloc::const_pointer`v případě, že typ je ve správném formátu; jinak, tento typ je `pointer_traits<pointer>::rebind<const value_type>`.|
|`allocator_traits::const_void_pointer`|Tento typ je `Alloc::const_void_pointer`v případě, že typ je ve správném formátu; jinak, tento typ je `pointer_traits<pointer>::rebind<const void>`.|
|`allocator_traits::difference_type`|Tento typ je `Alloc::difference_type`v případě, že typ je ve správném formátu; jinak, tento typ je `pointer_traits<pointer>::difference_type`.|
|`allocator_traits::pointer`|Tento typ je `Alloc::pointer`v případě, že typ je ve správném formátu; jinak, tento typ je `value_type *`.|
|`allocator_traits::propagate_on_container_copy_assignment`|Tento typ je `Alloc::propagate_on_container_copy_assignment`v případě, že typ je ve správném formátu; jinak, tento typ je `false_type`.|
|`allocator_traits::propagate_on_container_move_assignment`|Tento typ je `Alloc::propagate_on_container_move_assignment`v případě, že typ je ve správném formátu; jinak, tento typ je `false_type`. Pokud typ obsahuje hodnotu true, kontejner povoleno allocator zkopíruje jeho uložené allocator na přesun přiřazení.|
|`allocator_traits::propagate_on_container_swap`|Tento typ je `Alloc::propagate_on_container_swap`v případě, že typ je ve správném formátu; jinak, tento typ je `false_type`. Pokud typ obsahuje hodnotu true, kontejner povoleno allocator prohození jeho uložené allocator na prohození.|
|`allocator_traits::size_type`|Tento typ je `Alloc::size_type`v případě, že typ je ve správném formátu; jinak, tento typ je `make_unsigned<difference_type>::type`.|
|`allocator_traits::value_type`|Tento typ se jedná o synonymum `Alloc::value_type`.|
|`allocator_traits::void_pointer`|Tento typ je `Alloc::void_pointer`v případě, že typ je ve správném formátu; jinak, tento typ je `pointer_traits<pointer>::rebind<void>`.|

### <a name="static-methods"></a>Statické metody

Následující statických metod volat odpovídající metodu pro danou allocator parametr.

|Název|Popis|
|----------|-----------------|
|[allocate](#allocate)|Statickou metodu, pomocí parametru daného allocator přidělí paměť.|
|[konstrukce](#construct)|Statickou metodu, který používá zadaný allocator k vytvoření objektu.|
|[Zrušit přidělení](#deallocate)|Statickou metodu, která používá zadaný allocator se zrušit přidělení zadaný počet objektů.|
|[Destroy –](#destroy)|Statickou metodu, která používá zadaný allocator volání destruktoru objektu bez rušení přidělení paměti.|
|[max_size](#max_size)|Statickou metodu, který používá zadaný allocator můžete určit maximální počet objektů, které mohou být přiděleny.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Statickou metodu, která volá `select_on_container_copy_construction` na zadaný přidělení.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<paměti >

**Namespace:** – std

## <a name="allocate"></a>  allocator_traits::allocate –

Statickou metodu, pomocí parametru daného allocator přidělí paměť.

```cpp
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```

### <a name="parameters"></a>Parametry

`al` Objekt přidělení.

`count` Počet elementů přidělit.

`hint` A `const_pointer` který může pomoct objekt allocator neodpovídajících požadavku pro úložiště tím, že se adresy přidělené objektu před žádosti. Ukazatel s hodnotou null je považována za bez pomocného parametru.

### <a name="return-value"></a>Návratová hodnota

Každá metoda vrátí objekt přidělené ukazatel.

Vrátí první statickou metodu `al.allocate(count)`.

Druhá metoda vrátí `al.allocate(count, hint)`v případě, že výraz je dobře vytvořen; v opačném případě vrátí `al.allocate(count)`.

## <a name="construct"></a>  allocator_traits::Construct –

Statickou metodu, který používá zadaný allocator k vytvoření objektu.

```cpp
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```

### <a name="parameters"></a>Parametry

`al` Objekt přidělení.

`ptr` Ukazatel na umístění, kde je objekt zkonstruovat.

`args` Seznam argumentů, který je předaný do konstruktoru objektu.

### <a name="remarks"></a>Poznámky

Volání funkce statický člen `al.construct(ptr, args...)`, pokud; v opačném případě vyhodnotí výraz je dobře vytvořen `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)`.

## <a name="deallocate"></a>  allocator_traits::deallocate –

Statickou metodu, která používá zadaný allocator se zrušit přidělení zadaný počet objektů.

```cpp
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```

### <a name="parameters"></a>Parametry

`al` Objekt přidělení.

`ptr` Ukazatel na počáteční umístění objekty, které chcete být navrácena.

`count` Počet objektů se zrušit přidělení.

### <a name="remarks"></a>Poznámky

Tato metoda volá `al.deallocate(ptr, count)`.

Tato metoda vyvolá nic.

## <a name="destroy"></a>  allocator_traits::Destroy –

Statickou metodu, která používá zadaný allocator volání destruktoru objektu bez rušení přidělení paměti.

```cpp
template <class Uty>
static void destroy(Alloc& al, Uty* ptr);
```

### <a name="parameters"></a>Parametry

`al` Objekt přidělení.

`ptr` Ukazatel na umístění objektu.

### <a name="remarks"></a>Poznámky

Tato metoda volá `al.destroy(ptr)`, pokud; v opačném případě vyhodnotí výraz je dobře vytvořen `ptr->~Uty()`.

## <a name="max_size"></a>  allocator_traits::max_size –

Statickou metodu, který používá zadaný allocator můžete určit maximální počet objektů, které mohou být přiděleny.

```cpp
static size_type max_size(const Alloc& al);
```

### <a name="parameters"></a>Parametry

`al` Objekt přidělení.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu `al.max_size()`v případě, že výraz je dobře vytvořen; v opačném případě vrátí `numeric_limits<size_type>::max()`.

## <a name="select_on_container_copy_construction"></a>  allocator_traits::select_on_container_copy_construction –

Statickou metodu, která volá `select_on_container_copy_construction` na zadaný přidělení.

```cpp
static Alloc select_on_container_copy_construction(const Alloc& al);
```

### <a name="parameters"></a>Parametry

`al` Objekt přidělení.

### <a name="return-value"></a>Návratová hodnota

Tato metoda vrátí hodnotu `al.select_on_container_copy_construction()`v případě, že typ je dobře vytvořen; v opačném případě vrátí `al`.

### <a name="remarks"></a>Poznámky

Tato metoda se používá k určení přidělení při přidružené kontejneru je vytvořená kopie.

## <a name="see-also"></a>Viz také

[\<paměť >](../standard-library/memory.md)<br/>
[pointer_traits – struktura](../standard-library/pointer-traits-struct.md)<br/>
[scoped_allocator_adaptor – třída](../standard-library/scoped-allocator-adaptor-class.md)<br/>
