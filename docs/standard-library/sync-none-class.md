---
title: sync_none – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e27611b077a6a1ea4715f20e6524f394af3b48f5
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
|[Zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.|
|[equals](#equals)|Porovná dva mezipamětí rovnosti.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext –

## <a name="allocate"></a>  sync_none::allocate

Přiděluje blok paměti.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`count`|Počet prvků v poli, která bude přidělena.|

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu `cache.allocate(count)`, kde `cache` je objekt mezipaměti.

## <a name="deallocate"></a>  sync_none::deallocate

Uvolní zadaný počet objektů ze začátku úložiště na zadané pozici.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`ptr`|Ukazatel na první objekt, který má být navrácena z úložiště.|
|`count`|Počet objektů, které chcete být navrácena z úložiště.|

### <a name="remarks"></a>Poznámky

Volání členských funkcí `cache.deallocate(ptr, count)`, kde `cache` představuje objekt mezipaměti.

## <a name="equals"></a>  sync_none::Equals

Porovná dva mezipamětí rovnosti.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`Cache`|Objekt mezipaměti filtru synchronizace.|
|`Other`|Objekt mezipaměti pro porovnání rovnosti.|

### <a name="return-value"></a>Návratová hodnota

Členská funkce vždy vrátí hodnotu `true`.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[\<alokátorů >](../standard-library/allocators-header.md)<br/>
