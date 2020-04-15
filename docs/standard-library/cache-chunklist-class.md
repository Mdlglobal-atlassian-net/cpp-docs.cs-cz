---
title: cache_chunklist – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
ms.openlocfilehash: d0dd6176a34bd625069511106c491225d1467d08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366760"
---
# <a name="cache_chunklist-class"></a>cache_chunklist – třída

Definuje [blok přidělování,](../standard-library/allocators-header.md) který přiděluje a navrací paměťové bloky jedné velikosti.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Sz*|Počet prvků v poli, které mají být přiděleny.|

## <a name="remarks"></a>Poznámky

Tato šablona třídy používá **operátor new** k přidělení bloků nezpracované paměti a v případě potřeby přiděluje bloky pro přidělení úložiště pro blok paměti. ukládá blokované paměťové bloky v samostatném seznamu volných pro každý blok a používá **operátor delete** k napřidělení bloku, pokud není používán žádný z jeho bloků paměti.

Každý blok paměti obsahuje *bajty Sz* použitelné paměti a ukazatel na blok, ke kterému patří. Každý blok `Nelts` obsahuje bloky paměti, tři ukazatele, int a data, která **vyžadují nový operátor** a odstranění **operátoru.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[cache_chunklist](#cache_chunklist)|Vytvoří objekt typu `cache_chunklist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[Navrátit](#deallocate)|Uvolní zadaný počet objektů z úložiště začínající na zadané pozici.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a>cache_chunklist::přidělit

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

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a>cache_chunklist::cache_chunklist

Vytvoří objekt typu `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Poznámky

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a>cache_chunklist::deallocate

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
