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
ms.openlocfilehash: 065c0eaf936a438f48dbb8aa28704e0f53926a03
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451128"
---
# <a name="rtsalloc-class"></a>rts_alloc – třída

Třída šablony rts_alloc popisuje [Filtr](../standard-library/allocators-header.md) , který obsahuje pole instancí mezipaměti a určuje, která instance se má použít pro přidělení a zrušení přidělení za běhu místo v době kompilace.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Typ instancí mezipaměti obsažených v poli. Může se jednat o [třídu cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)nebo [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Poznámky

Tato třída šablony obsahuje více instancí přidělování bloků a určuje, která instance má být použita pro přidělení nebo zrušení přidělení za běhu místo v době kompilace. Používá se s kompilátory, které nemohou kompilovat opětovnou vazby.

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[uvolnit](#deallocate)|Uvolní zadaný počet objektů od úložiště, které začínají na zadané pozici.|
|[equals](#equals)|Porovná dvě mezipaměti pro rovnost.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> přidělování

**Obor názvů:** stdext

## <a name="allocate"></a>rts_alloc:: allocate

Přidělí blok paměti.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*výpočtu*|Počet prvků v poli, které mají být přiděleny.|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na přidělený objekt.

### <a name="remarks"></a>Poznámky

Vrátí `caches[_IDX].allocate(count)`členské funkce, kde je index `_IDX` určen podle požadovaného *počtu*velikost bloku nebo, pokud je *počet* příliš velký, vrátí `operator new(count)`. `cache`, který představuje objekt mezipaměti.

## <a name="deallocate"></a>rts_alloc::d eallocate

Uvolní zadaný počet objektů od úložiště, které začínají na zadané pozici.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na první objekt, který má být vrácen z úložiště.|
|*výpočtu*|Počet objektů, které se mají uvolnit z úložiště|

### <a name="remarks"></a>Poznámky

Členská funkce volá `caches[_IDX].deallocate(ptr, count)`, kde je index `_IDX` určen podle požadovaného *počtu*velikostí bloku, nebo pokud je *počet* příliš velký, vrátí `operator delete(ptr)`.

## <a name="equals"></a>rts_alloc:: Equals

Porovná dvě mezipaměti pro rovnost.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Cache*|Objekt mezipaměti přidružený k filtru.|
|*_Other*|Objekt mezipaměti, který se má porovnat s rovností.|

### <a name="remarks"></a>Poznámky

**true** , pokud výsledek `caches[0].equals(other.caches[0])`, v opačném případě **false**. `caches`představuje pole objektů mezipaměti.

## <a name="see-also"></a>Viz také:

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<allocators>](../standard-library/allocators-header.md)
