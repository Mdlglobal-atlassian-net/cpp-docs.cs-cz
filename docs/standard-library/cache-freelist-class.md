---
title: cache_freelist – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3d3902d900e0dad5ec3e335e9c3424d58ee2674
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960414"
---
# <a name="cachefreelist-class"></a>cache_freelist – třída

Definuje [blokovat allocator](../standard-library/allocators-header.md) , který přiděluje a zruší přidělení bloků paměti z jednoho velikost.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Sz*|Počet prvků v poli, které mají být přiděleny.|
|*Max*|Maximální počet Třída reprezentující maximální velikost seznamu zdarma. To může být [max_fixed_size –](../standard-library/max-fixed-size-class.md), [max_none –](../standard-library/max-none-class.md), [max_unbounded –](../standard-library/max-unbounded-class.md), nebo [max_variable_size –](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Poznámky

Cache_freelist – třída šablony udržuje seznam paměťových bloků velikosti volného *Sz*. Bezplatné seznamu je plná používá **operátor delete** k uvolnění paměti blokuje. Bezplatné seznam je prázdný používá **operátor new** přidělení nové bloky paměti. Maximální velikost seznamu zdarma určuje třídou maximální třídy předaný *maximální* parametru.

Každý blok paměti obsahuje *Sz* bajtů použitelné paměti a data, která **operátor new** a **operátor delete** vyžadují.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[cache_freelist](#cache_freelist)|Vytvoří objekt typu `cache_freelist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přiděluje blok paměti.|
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="allocate"></a>  cache_freelist::allocate

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

## <a name="cache_freelist"></a>  cache_freelist::cache_freelist

Vytvoří objekt typu `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Poznámky

## <a name="deallocate"></a>  cache_freelist::deallocate

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

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)<br/>
