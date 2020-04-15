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
ms.openlocfilehash: c49ceec72be62d8ff3125f04d97bbb6952501677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370977"
---
# <a name="max_none-class"></a>max_none – třída

Popisuje [objekt třídy max,](../standard-library/allocators-header.md) který omezuje objekt [freelist](../standard-library/freelist-class.md) na maximální délku nula.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Max*|Maximální třída, která určuje maximální počet prvků, `freelist`které mají být ukládány v rozhraní .|

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

## <a name="max_noneallocated"></a><a name="allocated"></a>max_none::přiděleno

Zvýšení počtu bloků přidělené paměti.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Hodnota přírůstku.|

### <a name="remarks"></a>Poznámky

Tato členská funkce neprovede žádné funkce. Je volána po každém `cache_freelist::allocate` úspěšném volání operátorem **new**. Argument *_Nx* je počet bloků paměti v bloku dat přidělené **operátorem new**.

## <a name="max_nonedeallocated"></a><a name="deallocated"></a>max_none::deallocated

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

## <a name="max_nonefull"></a><a name="full"></a>max_none::plné

Vrátí hodnotu, která určuje, zda má být do seznamu volných položek přidáno více bloků paměti.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

Tato členská funkce vždy vrátí **hodnotu true**.

### <a name="remarks"></a>Poznámky

Tato členská funkce `cache_freelist::deallocate`je volána společností . Pokud volání vrátí `deallocate` **hodnotu true**, umístí blok paměti na seznam volných; Pokud vrátí **false**false `deallocate` , volání operátor **odstranit** navrátit blok.

## <a name="max_nonereleased"></a><a name="released"></a>max_none::vydáno

Sníží počet bloků paměti na seznamu volných.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce neprovede žádné funkce. Členská `released` funkce aktuální třídy max `cache_freelist::allocate` je volána vždy, když odebere blok paměti ze seznamu volných.

## <a name="max_nonesaved"></a><a name="saved"></a>max_none::uloženo

Zvýšení počtu bloků paměti na seznamu volných.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce neprovede žádné funkce. Je volána `cache_freelist::deallocate` vždy, když vloží blok paměti na seznamu volných.

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
