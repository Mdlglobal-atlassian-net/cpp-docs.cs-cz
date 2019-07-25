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
ms.openlocfilehash: 05260d6800597b64908ff0aeffac47b09fed9a0e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449690"
---
# <a name="cachefreelist-class"></a>cache_freelist – třída

Definuje [přidělování bloků](../standard-library/allocators-header.md) , které přiděluje a odděluje bloky paměti s jednou velikostí.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Sz*|Počet prvků v poli, které mají být přiděleny.|
|*Max*|Maximální třída představující maximální velikost volného seznamu. To může být [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md)nebo [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Poznámky

Třída šablony cache_freelist udržuje volný seznam bloků paměti velikosti *SZ*. Když je bezplatný seznam plný, používá **operátor delete** k navrácení bloků paměti. Když je seznam free prázdný, používá **operátor New** k přidělení nových paměťových bloků. Maximální velikost volného seznamu je určena třídou Max třídy předanou v parametru *Max* .

Každý blok paměti obsahuje z paměti *SZ až SZ* bajtů a data, která **operátor New** a **operátor delete** vyžadují.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[cache_freelist](#cache_freelist)|Vytvoří objekt typu `cache_freelist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[uvolnit](#deallocate)|Uvolní zadaný počet objektů od úložiště, které začínají na zadané pozici.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> přidělování

**Obor názvů:** stdext

## <a name="allocate"></a>cache_freelist:: allocate

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

## <a name="cache_freelist"></a>cache_freelist::cache_freelist

Vytvoří objekt typu `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Poznámky

## <a name="deallocate"></a>cache_freelist::d eallocate

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

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
