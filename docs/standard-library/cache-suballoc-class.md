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
ms.openlocfilehash: 7a21f0c4f81277200ff069baf751fa013a3c0cea
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688348"
---
# <a name="cache_suballoc-class"></a>cache_suballoc – třída

Definuje [přidělování bloků](../standard-library/allocators-header.md) , které přiděluje a odděluje bloky paměti s jednou velikostí.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*'S*|Počet prvků v poli, které mají být přiděleny.|

## <a name="remarks"></a>Poznámky

Šablona třídy cache_suballoc ukládá nepřidělené bloky paměti do bezplatného seznamu s nevázanou délkou, používá `freelist<sizeof(Type), max_unbounded>` a rozděluje bloky paměti z většího bloku dat přiděleného **operátorem New** , pokud je seznam volných hodnot prázdný.

Každý blok dat uchovává `Sz * Nelts` bajtů použitelné paměti a data, která **operátor New** a **operátor delete** vyžaduje. Přidělené bloky dat nejsou nikdy uvolněny.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[cache_suballoc](#cache_suballoc)|Vytvoří objekt typu `cache_suballoc`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[uvolnit](#deallocate)|Uvolní zadaný počet objektů od úložiště, které začínají na zadané pozici.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<allocators >

**Obor názvů:** stdext

## <a name="allocate"></a>cache_suballoc:: allocate

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

## <a name="cache_suballoc"></a>cache_suballoc::cache_suballoc

Vytvoří objekt typu `cache_suballoc`.

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Poznámky

## <a name="deallocate"></a>cache_suballoc::d eallocate

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

[\<allocators >](../standard-library/allocators-header.md)
