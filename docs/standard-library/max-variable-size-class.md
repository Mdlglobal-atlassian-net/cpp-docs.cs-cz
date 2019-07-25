---
title: max_variable_size – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
ms.openlocfilehash: f8b3c61676f784bf9369c22b5db97d7b251f7ac6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447284"
---
# <a name="maxvariablesize-class"></a>max_variable_size – třída

Popisuje objekt [maximální třídy](../standard-library/allocators-header.md) , který omezuje objekt [freelist –](../standard-library/freelist-class.md) na maximální délku, která je zhruba úměrná počtu přidělených bloků paměti.

## <a name="syntax"></a>Syntaxe

```cpp
class max_variable_size
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[max_variable_size](#max_variable_size)|Vytvoří objekt typu `max_variable_size`.|

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

## <a name="allocated"></a>max_variable_size:: přiděleno

Zvýší počet přidělených bloků paměti.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Přírůstková hodnota.|

### <a name="remarks"></a>Poznámky

Tato členská funkce přidá *_Nx* do uložené hodnoty `_Nallocs`. Tato členská funkce se volá po každém úspěšném `cache_freelist::allocate` volání funkce operator **New**. Argument *_Nx* je počet paměťových bloků v bloku, který je přidělený operátorem **New**.

## <a name="deallocated"></a>max_variable_size::d eallocated

Sníží počet přidělených bloků paměti.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Přírůstková hodnota.|

### <a name="remarks"></a>Poznámky

Členská funkce odečte *_Nx* od uložené hodnoty `_Nallocs`. Tato členská funkce se volá po každém volání `cache_freelist::deallocate` operátoru **Delete**. Argument *_Nx* je počet bloků paměti v bloku, který byl odstraněn pomocí operátoru **Delete**.

## <a name="full"></a>max_variable_size:: Full

Vrátí hodnotu, která určuje, zda mají být do bezplatného seznamu přidány další bloky paměti.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

**true** , `_Nallocs / 16 + 16 <= _Nblocks`Pokud.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `cache_freelist::deallocate`nástrojem. Pokud volání vrátí **hodnotu true**, `deallocate` umístí blok paměti do bezplatného seznamu; Pokud vrátí hodnotu false, `deallocate` volá operátor **DELETE pro zrušení** přidělení bloku.

## <a name="max_variable_size"></a>max_variable_size::max_variable_size

Vytvoří objekt typu `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Poznámky

Konstruktor inicializuje uložené hodnoty `_Nblocks` a `_Nallocs` na nulu.

## <a name="released"></a>max_variable_size:: vydáno

Sníží počet bloků paměti v bezplatném seznamu.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce sníží uloženou hodnotu `_Nblocks`. Členská funkce aktuální třídy maxima je `cache_freelist::allocate` volána při každém odebrání bloku paměti ze seznamu Free. `released`

## <a name="saved"></a>max_variable_size:: Uloženo

Zvýší počet bloků paměti v bezplatném seznamu.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce zvýší uloženou hodnotu `_Nblocks`. Tato členská funkce je volána `cache_freelist::deallocate` vždy, když umístí blok paměti do bezplatného seznamu.

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
