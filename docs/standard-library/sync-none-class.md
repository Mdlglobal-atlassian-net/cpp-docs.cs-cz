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
ms.openlocfilehash: eba2c60e621df717f29c0b25c735df3fda285fa0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412173"
---
# <a name="syncnone-class"></a>sync_none – třída

Popisuje [filtr synchronizace](../standard-library/allocators-header.md) poskytující žádná synchronizace.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Cache>
class sync_none
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`Cache`|Typ mezipaměti přidružené k filtru synchronizace. To může být [cache_chunklist –](../standard-library/cache-chunklist-class.md), [cache_freelist –](../standard-library/cache-freelist-class.md), nebo [cache_suballoc –](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přiděluje blok paměti.|
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.|
|[equals](#equals)|Porovná rovnost dvou mezipamětí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="allocate"></a>  sync_none::allocate

Přiděluje blok paměti.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Počet*|Počet prvků v poli, které mají být přiděleny.|

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `cache.allocate(count)`, kde `cache` je objekt mezipaměti.

## <a name="deallocate"></a>  sync_none::deallocate

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

Volání členských funkcí `cache.deallocate(ptr, count)`, kde `cache` představuje objekt mezipaměti.

## <a name="equals"></a>  sync_none::Equals

Porovná rovnost dvou mezipamětí.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Mezipaměť*|Objekt mezipaměti filtr synchronizace.|
|*Jiné*|Mezipaměť objekt k porovnání rovnosti.|

### <a name="return-value"></a>Návratová hodnota

Členská funkce vždy vrátí **true**.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)<br/>
