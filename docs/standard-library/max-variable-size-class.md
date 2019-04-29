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
ms.openlocfilehash: a7fde40352a878575ddce8b48b4c97093ae7a960
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412927"
---
# <a name="maxvariablesize-class"></a>max_variable_size – třída

Popisuje [maximálního počtu tříd](../standard-library/allocators-header.md) objekt, který omezuje [freelist](../standard-library/freelist-class.md) objekt má maximální délku, která je přibližně úměrný počtu přidělených paměťových bloků.

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
|[přidělené](#allocated)|Zvýší počet přidělených paměťových bloků.|
|[přidělení](#deallocated)|Sníží počet přidělených paměťových bloků.|
|[Úplné](#full)|Vrátí hodnotu, která určuje, zda by měl být další bloky paměti přidat do seznamu zdarma.|
|[Všeobecně dostupné](#released)|Sníží počet paměti blokuje v seznamu zdarma.|
|[saved](#saved)|Zvýší počet paměťových bloků v seznamu zdarma.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext

## <a name="allocated"></a>  max_variable_size::allocated

Zvýší počet přidělených paměťových bloků.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Přírůstková hodnota.|

### <a name="remarks"></a>Poznámky

Tato členská funkce přidá *_Nx* k uložené hodnotě `_Nallocs`. Tato členská funkce je volána po úspěšné volání podle `cache_freelist::allocate` operátoru **nové**. Argument *_Nx* je počet paměťových bloků v bloku dat přidělena pomocí operátoru **nové**.

## <a name="deallocated"></a>  max_variable_size::deallocated

Sníží počet přidělených paměťových bloků.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Přírůstková hodnota.|

### <a name="remarks"></a>Poznámky

Členská funkce odečte *_Nx* od uložené hodnoty `_Nallocs`. Tato členská funkce je volána po každé volání podle `cache_freelist::deallocate` operátoru **odstranit**. Argument *_Nx* je počet paměťových bloků v bloku dat navrácena pomocí operátoru **odstranit**.

## <a name="full"></a>  max_variable_size::full

Vrátí hodnotu, která určuje, zda by měl být další bloky paměti přidat do seznamu zdarma.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `_Nallocs / 16 + 16 <= _Nblocks`.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `cache_freelist::deallocate`. Pokud volání vrátí **true**, `deallocate` vloží blok paměti v seznamu zdarma; Pokud vrátí hodnotu false, `deallocate` operátor volání **odstranit** se uvolnit bloku.

## <a name="max_variable_size"></a>  max_variable_size::max_variable_size

Vytvoří objekt typu `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Poznámky

Konstruktor inicializuje uložené hodnoty `_Nblocks` a `_Nallocs` na nulu.

## <a name="released"></a>  max_variable_size::released

Sníží počet paměti blokuje v seznamu zdarma.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Tento člen funkce sníží uloženou hodnotu `_Nblocks`. `released` Členské funkce třídy aktuální maximální volá `cache_freelist::allocate` vždy, když ji odebere blok paměti ze seznamu zdarma.

## <a name="saved"></a>  max_variable_size::saved

Zvýší počet paměťových bloků v seznamu zdarma.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce zvýší uloženou hodnotu `_Nblocks`. Tato členská funkce je volána `cache_freelist::deallocate` vždy, když umístí blok paměti v seznamu zdarma.

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)<br/>
