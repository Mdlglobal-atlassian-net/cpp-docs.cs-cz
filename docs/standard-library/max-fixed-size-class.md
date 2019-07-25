---
title: max_fixed_size – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
ms.openlocfilehash: bbc39a169f9a4bbac3e78b208b3a1a31e4e30ff2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456368"
---
# <a name="maxfixedsize-class"></a>max_fixed_size – třída

Popisuje [maximální objekt třídy](../standard-library/allocators-header.md) , který omezuje objekt [freelist –](../standard-library/freelist-class.md) na pevnou maximální délku.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Max*|Maximální třída, která určuje maximální počet prvků, které mají být uloženy v `freelist`.|

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[max_fixed_size](#max_fixed_size)|Vytvoří objekt typu `max_fixed_size`.|

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

## <a name="allocated"></a>max_fixed_size:: přiděleno

Zvýší počet přidělených bloků paměti.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Přírůstková hodnota.|

### <a name="remarks"></a>Poznámky

Členské funkce neprovádí žádnou akci. Tato členská funkce se volá po každém úspěšném `cache_freelist::allocate` volání funkce operator **New**. Argument *_Nx* je počet paměťových bloků v bloku, který je přidělený operátorem **New**.

## <a name="deallocated"></a>max_fixed_size::d eallocated

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

## <a name="full"></a>max_fixed_size:: Full

Vrátí hodnotu, která určuje, zda mají být do bezplatného seznamu přidány další bloky paměti.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

**true** , `Max <= _Nblocks`Pokud; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `cache_freelist::deallocate`nástrojem. Pokud volání vrátí **hodnotu true**, `deallocate` umístí blok paměti do bezplatného seznamu; Pokud vrátí hodnotu false, `deallocate` volá operátor **DELETE pro zrušení** přidělení bloku.

## <a name="max_fixed_size"></a>max_fixed_size::max_fixed_size

Vytvoří objekt typu `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Poznámky

Tento konstruktor inicializuje uloženou hodnotu `_Nblocks` na nulu.

## <a name="released"></a>max_fixed_size:: vydáno

Sníží počet bloků paměti v bezplatném seznamu.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Sníží uloženou hodnotu `_Nblocks`. Členská funkce aktuální [třídy maxima](../standard-library/allocators-header.md) je volána `cache_freelist::allocate` při každém odebrání bloku paměti ze seznamu Free. `released`

## <a name="saved"></a>max_fixed_size:: Uloženo

Zvýší počet bloků paměti v bezplatném seznamu.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce zvýší uloženou hodnotu `_Nblocks`. Tato členská funkce je volána `cache_freelist::deallocate` vždy, když umístí blok paměti do bezplatného seznamu.

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
