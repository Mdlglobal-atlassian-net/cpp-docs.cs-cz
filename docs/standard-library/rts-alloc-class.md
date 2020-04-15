---
title: rts_alloc – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
ms.openlocfilehash: 6ed84d906944a09fa355e281640e9480f3173554
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373429"
---
# <a name="rts_alloc-class"></a>rts_alloc – třída

Šablona třídy rts_alloc popisuje [filtr,](../standard-library/allocators-header.md) který obsahuje pole instancí mezipaměti a určuje, kterou instanci použít pro přidělení a deallocation za běhu namísto v době kompilace.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Typ instancí mezipaměti obsažených v poli. Může cache_chunklist [třídy](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)nebo [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Poznámky

Tato šablona třídy obsahuje více instancí alokátoru bloku a určuje, kterou instanci použít pro přidělení nebo přidělení za běhu namísto v době kompilace. Používá se s kompilátory, které nelze zkompilovat rebind.

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[Navrátit](#deallocate)|Uvolní zadaný počet objektů z úložiště začínající na zadané pozici.|
|[equals](#equals)|Porovná dvě mezipaměti pro rovnost.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a>rts_alloc::přidělit

Přidělí blok paměti.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Počet*|Počet prvků v poli, které mají být přiděleny.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidělený objekt.

### <a name="remarks"></a>Poznámky

Členská funkce `caches[_IDX].allocate(count)`vrátí , `_IDX` kde je index určen požadovaným *počtem*velikostí bloku , `operator new(count)`nebo pokud je *počet* příliš velký, vrátí . `cache`, který představuje objekt mezipaměti.

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a>rts_alloc::deallocate

Uvolní zadaný počet objektů z úložiště začínající na zadané pozici.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Ptr*|Ukazatel na první objekt, který má být deallocated z úložiště.|
|*Počet*|Počet objektů, které mají být deallocated z úložiště.|

### <a name="remarks"></a>Poznámky

Členská funkce `caches[_IDX].deallocate(ptr, count)`volá , `_IDX` kde je index určen *požadovanýpočet*velikosti bloku , `operator delete(ptr)`nebo pokud *počet* je příliš velký, vrátí .

## <a name="rts_allocequals"></a><a name="equals"></a>rts_alloc::rovná se

Porovná dvě mezipaměti pro rovnost.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Cache*|Objekt mezipaměti přidružený k filtru.|
|*_Other*|Objekt mezipaměti porovnat rovnost.|

### <a name="remarks"></a>Poznámky

**true,** pokud `caches[0].equals(other.caches[0])`výsledek ; jinak **false**. `caches`představuje pole objektů mezipaměti.

## <a name="see-also"></a>Viz také

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<alokátory>](../standard-library/allocators-header.md)
