---
title: cache_freelist – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
ms.openlocfilehash: d757909d3e54fed35bf42b943b9f9740dffee115
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366735"
---
# <a name="cache_freelist-class"></a>cache_freelist – třída

Definuje [blok přidělování,](../standard-library/allocators-header.md) který přiděluje a navrací paměťové bloky jedné velikosti.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Sz*|Počet prvků v poli, které mají být přiděleny.|
|*Max*|Maximální třída představující maximální velikost seznamu volných položek. To může být [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md)nebo [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Poznámky

Šablona třídy cache_freelist udržuje volný seznam paměťových bloků velikosti *Sz*. Když je seznam volných položek plný, používá **odstranění operátoru** k navracení bloků paměti. Když je prázdný seznam prázdný, používá **operátor new** k přidělení nových bloků paměti. Maximální velikost volného seznamu je určena třídou max předanou v parametru *Max.*

Každý blok paměti obsahuje *bajty Sz* využitelné paměti a data, která **operátor nový** a **operátor odstranit** vyžadují.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[cache_freelist](#cache_freelist)|Vytvoří objekt typu `cache_freelist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[Navrátit](#deallocate)|Uvolní zadaný počet objektů z úložiště začínající na zadané pozici.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="cache_freelistallocate"></a><a name="allocate"></a>cache_freelist::přidělit

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

## <a name="cache_freelistcache_freelist"></a><a name="cache_freelist"></a>cache_freelist::cache_freelist

Vytvoří objekt typu `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Poznámky

## <a name="cache_freelistdeallocate"></a><a name="deallocate"></a>cache_freelist::deallocate

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

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
