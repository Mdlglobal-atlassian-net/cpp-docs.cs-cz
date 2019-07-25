---
title: max_none – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
ms.openlocfilehash: 0d409928de4bf66bcc6d6dda3008131f87e790c3
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460172"
---
# <a name="maxnone-class"></a>max_none – třída

Popisuje [maximální objekt třídy](../standard-library/allocators-header.md) , který omezuje objekt [freelist –](../standard-library/freelist-class.md) na maximální délku nula.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Max*|Maximální třída, která určuje maximální počet prvků, které mají být uloženy v `freelist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[přidělování](#allocated)|Zvýší počet přidělených bloků paměti.|
|[přidělení zrušeno](#deallocated)|Sníží počet přidělených bloků paměti.|
|[kompletní](#full)|Vrátí hodnotu, která určuje, zda mají být do bezplatného seznamu přidány další bloky paměti.|
|[vydané](#released)|Sníží počet bloků paměti v bezplatném seznamu.|
|[saved](#saved)|Zvýší počet bloků paměti v bezplatném seznamu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> přidělování

**Obor názvů:** stdext

## <a name="allocated"></a>max_none:: přiděleno

Zvýší počet přidělených bloků paměti.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Přírůstková hodnota.|

### <a name="remarks"></a>Poznámky

Tato členská funkce neprovede žádnou akci. Je volána po každém úspěšném volání metody `cache_freelist::allocate` operator **New**. Argument *_Nx* je počet paměťových bloků v bloku, který je přidělený operátorem **New**.

## <a name="deallocated"></a>max_none::d eallocated

Sníží počet přidělených bloků paměti.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Přírůstková hodnota.|

### <a name="remarks"></a>Poznámky

Členské funkce neprovádí žádnou akci. Tato členská funkce se volá po každém volání `cache_freelist::deallocate` operátoru **Delete**. Argument *_Nx* je počet bloků paměti v bloku, který byl odstraněn pomocí operátoru **Delete**.

## <a name="full"></a>max_none:: Full

Vrátí hodnotu, která určuje, zda mají být do bezplatného seznamu přidány další bloky paměti.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

Tato členská funkce vždy vrátí **hodnotu true**.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `cache_freelist::deallocate`nástrojem. Pokud volání vrátí **hodnotu true**, `deallocate` umístí blok paměti do bezplatného seznamu; Pokud vrátí hodnotu false, `deallocate` volá operátor **DELETE pro zrušení** přidělení bloku.

## <a name="released"></a>max_none:: vydáno

Sníží počet bloků paměti v bezplatném seznamu.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce neprovede žádnou akci. Členská funkce aktuální třídy maxima je `cache_freelist::allocate` volána při každém odebrání bloku paměti ze seznamu Free. `released`

## <a name="saved"></a>max_none:: Uloženo

Zvýší počet bloků paměti v bezplatném seznamu.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce neprovede žádnou akci. Je volána `cache_freelist::deallocate` při každém vložení bloku paměti do bezplatného seznamu.

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
