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
ms.openlocfilehash: 55860a65fc77f834ed699f3a5114768b7efdde6f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366723"
---
# <a name="cache_suballoc-class"></a>cache_suballoc – třída

Definuje [blok přidělování,](../standard-library/allocators-header.md) který přiděluje a navrací paměťové bloky jedné velikosti.

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

Šablona třídy cache_suballoc ukládá blokované paměťové bloky ve `freelist<sizeof(Type), max_unbounded>`volném seznamu s neohraničenou délkou, pomocí a přiděluje bloky paměti z většího bloku dat přiděleného **s operátorem new,** když je seznam volných položek prázdný.

Každý blok `Sz * Nelts` obsahuje bajty využitelné paměti a data, která **vyžadují nový operátor** a odstranění **operátoru.** Přidělené bloky jsou nikdy uvolněny.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[cache_suballoc](#cache_suballoc)|Vytvoří objekt typu `cache_suballoc`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[Navrátit](#deallocate)|Uvolní zadaný počet objektů z úložiště začínající na zadané pozici.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="cache_suballocallocate"></a><a name="allocate"></a>cache_suballoc::přidělit

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

## <a name="cache_suballoccache_suballoc"></a><a name="cache_suballoc"></a>cache_suballoc::cache_suballoc

Vytvoří objekt typu `cache_suballoc`.

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Poznámky

## <a name="cache_suballocdeallocate"></a><a name="deallocate"></a>cache_suballoc::deallocate

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
