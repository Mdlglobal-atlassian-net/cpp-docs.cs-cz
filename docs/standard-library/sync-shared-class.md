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
ms.openlocfilehash: c368e99eb9f128963e90cdc1d39bdb9d4569efe9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483379"
---
# <a name="syncshared-class"></a>sync_shared – třída

Popisuje [filtr synchronizace](../standard-library/allocators-header.md) , který používá k řízení přístupu pro objekt z mezipaměti, jež jsou sdílena všechny alokátory mutex.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*mezipaměť*|Typ mezipaměti přidružené k filtru synchronizace. To může být [cache_chunklist –](../standard-library/cache-chunklist-class.md), [cache_freelist –](../standard-library/cache-freelist-class.md), nebo [cache_suballoc –](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přiděluje blok paměti.|
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.|
|[equals](#equals)|Porovná rovnost dvou mezipamětí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="allocate"></a>  sync_shared::allocate

Přiděluje blok paměti.

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

Členská funkce uzamkne mutex volání `cache.allocate(count)`odemkne vyloučený a vrátí výsledek předchozích volání `cache.allocate(count)`. `cache` představuje aktuální objekt mezipaměti.

## <a name="deallocate"></a>  sync_shared::deallocate

Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ptr*|Ukazatel na první objekt k zrušeno přidělení úložiště.|
|*Počet*|Počet objektů pro zrušeno přidělení úložiště.|

### <a name="remarks"></a>Poznámky

Tato členská funkce uzamkne mutex volání `cache.deallocate(ptr, count)`, kde `cache` představuje objekt mezipaměti a poté odemkne mutex.

## <a name="equals"></a>  sync_shared::Equals

Porovná rovnost dvou mezipamětí.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*mezipaměť*|Typ mezipaměti přidružené k filtru synchronizace.|
|*Jiné*|Mezipaměť pro porovnání rovnosti.|

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud výsledek `cache.equals(Other.cache)`, kde `cache` představuje objekt mezipaměti, je **true**; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)<br/>
