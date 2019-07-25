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
ms.openlocfilehash: 72ed21d3a0fb519bca2e19b7fbface05d5ac64ce
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450248"
---
# <a name="syncshared-class"></a>sync_shared – třída

Popisuje [filtr synchronizace](../standard-library/allocators-header.md) , který používá mutex k řízení přístupu k objektu mezipaměti, který je sdílen všemi přidělování.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Typ mezipaměti přidružený k synchronizačnímu filtru. To může být [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)nebo [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[uvolnit](#deallocate)|Uvolní zadaný počet objektů od úložiště, které začínají na zadané pozici.|
|[equals](#equals)|Porovná dvě mezipaměti pro rovnost.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> přidělování

**Obor názvů:** stdext

## <a name="allocate"></a>sync_shared:: allocate

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

Členská funkce zamkne mutex, volá `cache.allocate(count)`, odemkne mutex a vrátí výsledek předchozího `cache.allocate(count)`volání. `cache`představuje aktuální objekt mezipaměti.

## <a name="deallocate"></a>sync_shared::d eallocate

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

Tato členská funkce zamkne mutex, volání `cache.deallocate(ptr, count)`, kde `cache` představuje objekt mezipaměti, a potom odemkne mutex.

## <a name="equals"></a>sync_shared:: Equals

Porovná dvě mezipaměti pro rovnost.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Typ mezipaměti přidružený k synchronizačnímu filtru.|
|*Jiné*|Mezipaměť, která se má porovnat s rovností.|

### <a name="return-value"></a>Návratová hodnota

**true** , pokud `cache.equals(Other.cache)`výsledek, `cache` kde představuje objekt mezipaměti, je **true**; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
