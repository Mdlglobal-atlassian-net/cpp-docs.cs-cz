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
ms.openlocfilehash: 79e37d8c464a009e4a5196aeacc8d4a718e355b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370967"
---
# <a name="max_variable_size-class"></a>max_variable_size – třída

Popisuje [objekt třídy max,](../standard-library/allocators-header.md) který omezuje [objekt freelist](../standard-library/freelist-class.md) na maximální délku, která je zhruba úměrná počtu přidělených bloků paměti.

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
|[Přidělené](#allocated)|Zvýšení počtu bloků přidělené paměti.|
|[Navrácen](#deallocated)|Sníží počet přidělených bloků paměti.|
|[Plné](#full)|Vrátí hodnotu, která určuje, zda má být do seznamu volných položek přidáno více bloků paměti.|
|[Vydané](#released)|Sníží počet bloků paměti na seznamu volných.|
|[Uloženy](#saved)|Zvýšení počtu bloků paměti na seznamu volných.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátory>

**Obor názvů:** stdext

## <a name="max_variable_sizeallocated"></a><a name="allocated"></a>max_variable_size::přiděleno

Zvýšení počtu bloků přidělené paměti.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Hodnota přírůstku.|

### <a name="remarks"></a>Poznámky

Tato členská *_Nx* funkce přidává `_Nallocs`_Nx uloženou hodnotu . Tato členská funkce je volána po každém úspěšném volání operátorem `cache_freelist::allocate` **new**. Argument *_Nx* je počet bloků paměti v bloku dat přidělené **operátorem new**.

## <a name="max_variable_sizedeallocated"></a><a name="deallocated"></a>max_variable_size::deallocated

Sníží počet přidělených bloků paměti.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Hodnota přírůstku.|

### <a name="remarks"></a>Poznámky

Členská funkce odečte *_Nx* od `_Nallocs`uložené hodnoty . Tato členská funkce je `cache_freelist::deallocate` volána po každém volání operátorem **delete**. Argument *_Nx* je počet bloků paměti v bloku bloku, který je umístěn podle **odstranění**operátoru .

## <a name="max_variable_sizefull"></a><a name="full"></a>max_variable_size::plné

Vrátí hodnotu, která určuje, zda má být do seznamu volných položek přidáno více bloků paměti.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

**true** `_Nallocs / 16 + 16 <= _Nblocks`if .

### <a name="remarks"></a>Poznámky

Tato členská funkce `cache_freelist::deallocate`je volána společností . Pokud volání vrátí `deallocate` **hodnotu true**, umístí blok paměti na seznam volných; Pokud vrátí false, `deallocate` volání operátor **odstranit** navrátit blok.

## <a name="max_variable_sizemax_variable_size"></a><a name="max_variable_size"></a>max_variable_size::max_variable_size

Vytvoří objekt typu `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Poznámky

Konstruktor inicializuje uložené `_Nblocks` hodnoty `_Nallocs` a na nulu.

## <a name="max_variable_sizereleased"></a><a name="released"></a>max_variable_size::vydáno

Sníží počet bloků paměti na seznamu volných.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce sníží uloženou hodnotu `_Nblocks`. Členská `released` funkce aktuální třídy max `cache_freelist::allocate` je volána vždy, když odebere blok paměti ze seznamu volných.

## <a name="max_variable_sizesaved"></a><a name="saved"></a>max_variable_size::uloženo

Zvýšení počtu bloků paměti na seznamu volných.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce inkumuje uloženou hodnotu `_Nblocks`. Tato členská funkce `cache_freelist::deallocate` je volána vždy, když umístí blok paměti na seznam volných.

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
