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
ms.openlocfilehash: 035e5153b4e4c84743a64bcc9cec24920a6a0336
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688355"
---
# <a name="cache_chunklist-class"></a>cache_chunklist – třída

Definuje [přidělování bloků](../standard-library/allocators-header.md) , které přiděluje a odděluje bloky paměti s jednou velikostí.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*'S*|Počet prvků v poli, které mají být přiděleny.|

## <a name="remarks"></a>Poznámky

Tato šablona třídy používá **operátor New** pro přidělení bloků nezpracované paměti, přidělení bloků pro přidělení úložiště pro blok paměti v případě potřeby; ukládá navrácené bloky paměti do samostatného bezplatného seznamu pro každý blok a pomocí **operátoru delete** zruší přidělení bloku, když se nepoužívá žádný z jeho bloků paměti.

Každý blok paměti obsahuje hodnotu *SZ* bajtů použitelné paměti a ukazatel na blok, ke kterému patří. Každý blok obsahuje `Nelts` bloky paměti, tři ukazatele, int a data, která **operátor New** a **operátor delete** vyžaduje.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[cache_chunklist](#cache_chunklist)|Vytvoří objekt typu `cache_chunklist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[allocate](#allocate)|Přidělí blok paměti.|
|[uvolnit](#deallocate)|Uvolní zadaný počet objektů od úložiště, které začínají na zadané pozici.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<allocators >

**Obor názvů:** stdext

## <a name="allocate"></a>cache_chunklist:: allocate

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

## <a name="cache_chunklist"></a>cache_chunklist::cache_chunklist

Vytvoří objekt typu `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Poznámky

## <a name="deallocate"></a>cache_chunklist::d eallocate

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
