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
ms.openlocfilehash: 7f75dd71caa3cfcfec19264b1da62c6d47a3e01d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371010"
---
# <a name="max_fixed_size-class"></a>max_fixed_size – třída

Popisuje objekt [třídy max,](../standard-library/allocators-header.md) který omezuje [objekt freelistu](../standard-library/freelist-class.md) na pevnou maximální délku.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Max*|Maximální třída, která určuje maximální počet prvků, `freelist`které mají být ukládány v rozhraní .|

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[max_fixed_size](#max_fixed_size)|Vytvoří objekt typu `max_fixed_size`.|

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

## <a name="max_fixed_sizeallocated"></a><a name="allocated"></a>max_fixed_size::přiděleno

Zvýšení počtu bloků přidělené paměti.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Hodnota přírůstku.|

### <a name="remarks"></a>Poznámky

Členská funkce neprovede žádné funkce. Tato členská funkce je volána po každém úspěšném volání operátorem `cache_freelist::allocate` **new**. Argument *_Nx* je počet bloků paměti v bloku dat přidělené **operátorem new**.

## <a name="max_fixed_sizedeallocated"></a><a name="deallocated"></a>max_fixed_size::deallocated

Sníží počet přidělených bloků paměti.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Hodnota přírůstku.|

### <a name="remarks"></a>Poznámky

Členská funkce neprovede žádné funkce. Tato členská funkce je `cache_freelist::deallocate` volána po každém volání operátorem **delete**. Argument *_Nx* je počet bloků paměti v bloku bloku, který je umístěn podle **odstranění**operátoru .

## <a name="max_fixed_sizefull"></a><a name="full"></a>max_fixed_size::plné

Vrátí hodnotu, která určuje, zda má být do seznamu volných položek přidáno více bloků paměti.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud `Max <= _Nblocks`; jinak **false**.

### <a name="remarks"></a>Poznámky

Tato členská funkce `cache_freelist::deallocate`je volána společností . Pokud volání vrátí `deallocate` **hodnotu true**, umístí blok paměti na seznam volných; Pokud vrátí false, `deallocate` volání operátor **odstranit** navrátit blok.

## <a name="max_fixed_sizemax_fixed_size"></a><a name="max_fixed_size"></a>max_fixed_size::max_fixed_size

Vytvoří objekt typu `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Poznámky

Tento konstruktor inicializuje `_Nblocks` uloženou hodnotu na nulu.

## <a name="max_fixed_sizereleased"></a><a name="released"></a>max_fixed_size::vydáno

Sníží počet bloků paměti na seznamu volných.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Sníží uloženou hodnotu `_Nblocks`. Členská `released` funkce aktuální [třídy max](../standard-library/allocators-header.md) je volána vždy, `cache_freelist::allocate` když odebere blok paměti ze seznamu volných.

## <a name="max_fixed_sizesaved"></a><a name="saved"></a>max_fixed_size::uloženo

Zvýšení počtu bloků paměti na seznamu volných.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce inkumuje uloženou hodnotu `_Nblocks`. Tato členská funkce `cache_freelist::deallocate` je volána vždy, když umístí blok paměti na seznam volných.

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
