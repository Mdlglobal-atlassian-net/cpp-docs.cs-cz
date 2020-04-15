---
title: sync_per_thread – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
ms.openlocfilehash: 2976cdc6671750f0da439e9eb42053518e4af8d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376544"
---
# <a name="sync_per_thread-class"></a>sync_per_thread – třída

Popisuje [filtr synchronizace,](../standard-library/allocators-header.md) který poskytuje samostatný objekt mezipaměti pro každé vlákno.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_per_thread
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Typ mezipaměti přidružené k filtru synchronizace. To může být [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)nebo [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Poznámky

Alokátory, které `sync_per_thread` používají můžete porovnat stejné i v případě, že bloky přidělené v jednom vlákně nelze deallocated z jiného vlákna. Při použití jednoho z těchto alokátorů paměti bloky přidělené v jednom vlákně by neměly být viditelné pro jiné podprocesy. V praxi to znamená, že kontejner, který používá jeden z těchto alokátorů by měl y přistupovat pouze jedním podprocesem.

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[Navrátit](#deallocate)|Uvolní zadaný počet objektů z úložiště začínající na zadané pozici.|
|[equals](#equals)|Porovná dvě mezipaměti pro rovnost.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="sync_per_threadallocate"></a><a name="allocate"></a>sync_per_thread::přidělit

Přidělí blok paměti.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Počet*|Počet prvků v poli, které mají být přiděleny.|

### <a name="remarks"></a>Poznámky

Členská funkce vrátí výsledek volání `cache::allocate(count)` na objekt mezipaměti, který patří k aktuálnímu vláknu. Pokud pro aktuální vlákno nebyl přidělen žádný objekt mezipaměti, nejprve jej přidělí.

## <a name="sync_per_threaddeallocate"></a><a name="deallocate"></a>sync_per_thread::deallocate

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

Členská funkce `deallocate` volá objekt mezipaměti patřící do aktuálního vlákna. Pokud pro aktuální vlákno nebyl přidělen žádný objekt mezipaměti, nejprve jej přidělí.

## <a name="sync_per_threadequals"></a><a name="equals"></a>sync_per_thread::rovná se

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

**false,** pokud žádný objekt mezipaměti byla přidělena pro tento objekt nebo pro *jiné* v aktuálním vlákně. V opačném případě vrátí `operator==` výsledek použití na dva objekty mezipaměti.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
