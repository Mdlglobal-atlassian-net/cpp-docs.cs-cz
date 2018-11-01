---
title: cache_suballoc – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
ms.openlocfilehash: 06d0ef390e6ae1980b9ab20b8ceb67213837148b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438867"
---
# <a name="cachesuballoc-class"></a>cache_suballoc – třída

Definuje [blokovat allocator](../standard-library/allocators-header.md) , který přiděluje a zruší přidělení bloků paměti z jednoho velikost.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Sz*|Počet prvků v poli, které mají být přiděleny.|

## <a name="remarks"></a>Poznámky

Cache_suballoc – třída šablony ukládá uvolnění paměťových bloků v bezplatné seznam o délce bez vazby, pomocí `freelist<sizeof(Type), max_unbounded>`a suballocates bloky paměti z větších bloků dat, kterým je přiřazen výraz **operátor new** po seznamu zdarma prázdný.

Každý blok obsahuje `Sz * Nelts` bajtů použitelné paměti a data, která **operátor new** a **operátor delete** vyžadují. Přidělené bloky dat jsou nikdy uvolněna.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[cache_suballoc](#cache_suballoc)|Vytvoří objekt typu `cache_suballoc`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přiděluje blok paměti.|
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="allocate"></a>  cache_suballoc::allocate

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

## <a name="cache_suballoc"></a>  cache_suballoc::cache_suballoc

Vytvoří objekt typu `cache_suballoc`.

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Poznámky

## <a name="deallocate"></a>  cache_suballoc::deallocate

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
