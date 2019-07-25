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
ms.openlocfilehash: a08aa13aa46d5181e7c874b132b2bcbd5ec26dee
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450256"
---
# <a name="syncperthread-class"></a>sync_per_thread – třída

Popisuje [filtr synchronizace](../standard-library/allocators-header.md) , který poskytuje samostatný objekt mezipaměti pro každé vlákno.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_per_thread
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Typ mezipaměti přidružený k synchronizačnímu filtru. To může být [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)nebo [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Poznámky

Alokátory, které `sync_per_thread` používají, můžou porovnat stejně, i když bloky přidělené v jednom vlákně nejde uvolnit z jiného vlákna. Při použití jednoho z těchto bloků paměti přidělování, které jsou přiděleny v jednom vláknu, by neměly být viditelné pro ostatní vlákna. V praxi to znamená, že kontejner, který používá jedno z těchto přidělování, by měl být k dispozici pouze v jednom vlákně.

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[uvolnit](#deallocate)|Uvolní zadaný počet objektů od úložiště, které začínají na zadané pozici.|
|[equals](#equals)|Porovná dvě mezipaměti pro rovnost.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> přidělování

**Obor názvů:** stdext

## <a name="allocate"></a>sync_per_thread:: allocate

Přidělí blok paměti.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*výpočtu*|Počet prvků v poli, které mají být přiděleny.|

### <a name="remarks"></a>Poznámky

Členská funkce vrátí výsledek volání do `cache::allocate(count)` objektu Cache patřícího k aktuálnímu vláknu. Pokud není k dispozici žádný objekt mezipaměti pro aktuální vlákno, bude nejprve přiděleno.

## <a name="deallocate"></a>sync_per_thread::d eallocate

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

Členská funkce volá `deallocate` objekt mezipaměti patřící k aktuálnímu vláknu. Pokud není k dispozici žádný objekt mezipaměti pro aktuální vlákno, bude nejprve přiděleno.

## <a name="equals"></a>sync_per_thread:: Equals

Porovná dvě mezipaměti pro rovnost.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Objekt mezipaměti filtru synchronizace.|
|*Jiné*|Objekt mezipaměti, který se má porovnat s rovností.|

### <a name="return-value"></a>Návratová hodnota

**false** , pokud není pro tento objekt přidělen žádný objekt mezipaměti nebo pro *jiný* v aktuálním vlákně. V opačném případě vrátí výsledek použití `operator==` na dva objekty mezipaměti.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
