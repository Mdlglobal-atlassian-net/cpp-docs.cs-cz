---
title: sync_none – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
ms.openlocfilehash: 046cbca30b6cdef2dc4e7dbbe2791d52384d9f25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376575"
---
# <a name="sync_none-class"></a>sync_none – třída

Popisuje [filtr synchronizace,](../standard-library/allocators-header.md) který neposkytuje žádnou synchronizaci.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_none
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`Cache`|Typ mezipaměti přidružené k filtru synchronizace. To může být [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)nebo [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[Navrátit](#deallocate)|Uvolní zadaný počet objektů z úložiště začínající na zadané pozici.|
|[equals](#equals)|Porovná dvě mezipaměti pro rovnost.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="sync_noneallocate"></a><a name="allocate"></a>sync_none::přidělit

Přidělí blok paměti.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Počet*|Počet prvků v poli, které mají být přiděleny.|

### <a name="remarks"></a>Poznámky

Členská funkce `cache.allocate(count)`vrátí `cache` , kde je objekt mezipaměti.

## <a name="sync_nonedeallocate"></a><a name="deallocate"></a>sync_none::deallocate

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

Členská funkce `cache.deallocate(ptr, count)`volá `cache` , kde představuje objekt mezipaměti.

## <a name="sync_noneequals"></a><a name="equals"></a>sync_none::rovná se

Porovná dvě mezipaměti pro rovnost.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Objekt mezipaměti filtru synchronizace.|
|*Další*|Objekt mezipaměti porovnat rovnost.|

### <a name="return-value"></a>Návratová hodnota

Členská funkce vždy vrátí **hodnotu true**.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
