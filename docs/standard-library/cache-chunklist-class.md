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
ms.openlocfilehash: 94ae4dfc8f5f9073c0a39f315adfbed3e5c14daf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380167"
---
# <a name="cachechunklist-class"></a>cache_chunklist – třída

Definuje [blokovat allocator](../standard-library/allocators-header.md) , který přiděluje a zruší přidělení bloků paměti z jednoho velikost.

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

Pomocí této třídy šablony **operátor new** přidělení bloků paměti nezpracovaná suballocating blokuje k přidělení úložiště pro blok paměti v případě potřeby; ukládá uvolnění paměťových bloků v samostatných bezplatné seznamu pro každý blok a používá **operátor delete** se uvolnit blok, pokud žádná z jeho bloky paměti není používán.

Každý blok paměti obsahuje *Sz* bajtů použitelné paměti a ukazatelem na blok dat, který patří do. Každý blok obsahuje `Nelts` paměťových bloků, tří ukazatelů, int a data, která **operátor new** a **operátor delete** vyžadují.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[cache_chunklist](#cache_chunklist)|Vytvoří objekt typu `cache_chunklist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přiděluje blok paměti.|
|[zrušit přidělení](#deallocate)|Uvolní zadaný počet objektů z úložiště počínaje na určené pozici.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="allocate"></a>  cache_chunklist::allocate

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

## <a name="cache_chunklist"></a>  cache_chunklist::cache_chunklist

Vytvoří objekt typu `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Poznámky

## <a name="deallocate"></a>  cache_chunklist::deallocate

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

[\<allocators>](../standard-library/allocators-header.md)<br/>
