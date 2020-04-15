---
title: sync_shared – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
ms.openlocfilehash: 029edea59f29534491232d5d99353ccb093447bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376525"
---
# <a name="sync_shared-class"></a>sync_shared – třída

Popisuje [filtr synchronizace,](../standard-library/allocators-header.md) který používá objekt mutex k řízení přístupu k objektu mezipaměti, který je sdílen všemi alokátory.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Typ mezipaměti přidružené k filtru synchronizace. To může být [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)nebo [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[Navrátit](#deallocate)|Uvolní zadaný počet objektů z úložiště začínající na zadané pozici.|
|[equals](#equals)|Porovná dvě mezipaměti pro rovnost.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="sync_sharedallocate"></a><a name="allocate"></a>sync_shared::přidělit

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

Členská funkce uzamkne `cache.allocate(count)`objekt mutex, zavolá , odemkne mutex a vrátí výsledek dřívějšího volání . `cache.allocate(count)` `cache`představuje aktuální objekt mezipaměti.

## <a name="sync_shareddeallocate"></a><a name="deallocate"></a>sync_shared::deallocate

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

Tato členská funkce uzamkne objekt mutex, zavolá `cache.deallocate(ptr, count)`, kde `cache` představuje objekt mezipaměti a poté odemkne objekt mutex.

## <a name="sync_sharedequals"></a><a name="equals"></a>sync_shared::rovná se

Porovná dvě mezipaměti pro rovnost.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Typ mezipaměti přidružené k filtru synchronizace.|
|*Další*|Mezipaměť porovnat rovnost.|

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `cache.equals(Other.cache)`je `cache` **splněn**výsledek písmene , kde představuje objekt mezipaměti ; jinak **false**.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
