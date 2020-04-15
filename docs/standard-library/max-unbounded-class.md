---
title: max_unbounded – třída
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
ms.openlocfilehash: fbc4351297ab8a3cc90a2a77fa31c3b134f10eab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370998"
---
# <a name="max_unbounded-class"></a>max_unbounded – třída

Popisuje [objekt třídy max,](../standard-library/allocators-header.md) který neomezuje maximální délku [objektu freelist.](../standard-library/freelist-class.md)

## <a name="syntax"></a>Syntaxe

```cpp
class max_unbounded
```

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

## <a name="max_unboundedallocated"></a><a name="allocated"></a>max_unbounded::přiděleno

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

## <a name="max_unboundeddeallocated"></a><a name="deallocated"></a>max_unbounded::deallocated

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

## <a name="max_unboundedfull"></a><a name="full"></a>max_unbounded::plné

Vrátí hodnotu, která určuje, zda má být do seznamu volných položek přidáno více bloků paměti.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

Členská funkce vždy vrátí **false**.

### <a name="remarks"></a>Poznámky

Tato členská funkce `cache_freelist::deallocate`je volána společností . Pokud volání vrátí `deallocate` **hodnotu true**, umístí blok paměti na seznam volných; Pokud vrátí false, `deallocate` volání operátor **odstranit** navrátit blok.

## <a name="max_unboundedreleased"></a><a name="released"></a>max_unbounded::vydáno

Sníží počet bloků paměti na seznamu volných.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce neprovede žádné funkce. Členská `released` funkce aktuální třídy max `cache_freelist::allocate` je volána vždy, když odebere blok paměti ze seznamu volných.

## <a name="max_unboundedsaved"></a><a name="saved"></a>max_unbounded::uloženo

Zvýšení počtu bloků paměti na seznamu volných.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce neprovede žádné funkce. Je volána `cache_freelist::deallocate` vždy, když vloží blok paměti na seznamu volných.

## <a name="see-also"></a>Viz také

[\<alokátory>](../standard-library/allocators-header.md)
