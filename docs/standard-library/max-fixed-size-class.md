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
ms.openlocfilehash: 08510ecc3b7469e8f88a61dcb0df28541e170892
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666450"
---
# <a name="maxfixedsize-class"></a>max_fixed_size – třída

Popisuje [maximálního počtu tříd](../standard-library/allocators-header.md) objekt, který omezuje [freelist](../standard-library/freelist-class.md) objektu na pevnou maximální délku.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Max*|Maximální třídu, která určuje maximální počet prvků k ukládání `freelist`.|

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[max_fixed_size](#max_fixed_size)|Vytvoří objekt typu `max_fixed_size`.|

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

## <a name="allocated"></a>  max_fixed_size::allocated

Zvýší počet přidělených paměťových bloků.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Přírůstková hodnota.|

### <a name="remarks"></a>Poznámky

Členská funkce nemá žádný účinek. Tato členská funkce je volána po úspěšné volání podle `cache_freelist::allocate` operátoru **nové**. Argument *_Nx* je počet paměťových bloků v bloku dat přidělena pomocí operátoru **nové**.

## <a name="deallocated"></a>  max_fixed_size::deallocated

Sníží počet přidělených paměťových bloků.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Přírůstková hodnota.|

### <a name="remarks"></a>Poznámky

Členská funkce nemá žádný účinek. Tato členská funkce je volána po každé volání podle `cache_freelist::deallocate` operátoru **odstranit**. Argument *_Nx* je počet paměťových bloků v bloku dat navrácena pomocí operátoru **odstranit**.

## <a name="full"></a>  max_fixed_size::full

Vrátí hodnotu, která určuje, zda by měl být další bloky paměti přidat do seznamu zdarma.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud `Max <= _Nblocks`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `cache_freelist::deallocate`. Pokud volání vrátí **true**, `deallocate` vloží blok paměti v seznamu zdarma; Pokud vrátí hodnotu false, `deallocate` operátor volání **odstranit** se uvolnit bloku.

## <a name="max_fixed_size"></a>  max_fixed_size::max_fixed_size

Vytvoří objekt typu `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Poznámky

Tento konstruktor inicializuje uložené hodnoty `_Nblocks` na nulu.

## <a name="released"></a>  max_fixed_size::released

Sníží počet paměti blokuje v seznamu zdarma.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Sníží uloženou hodnotu `_Nblocks`. `released` Členskou funkci aktuálního [maximálního počtu tříd](../standard-library/allocators-header.md) je volán `cache_freelist::allocate` vždy, když ji odebere blok paměti ze seznamu zdarma.

## <a name="saved"></a>  max_fixed_size::saved

Zvýší počet paměťových bloků v seznamu zdarma.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce zvýší uloženou hodnotu `_Nblocks`. Tato členská funkce je volána `cache_freelist::deallocate` vždy, když umístí blok paměti v seznamu zdarma.

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)<br/>
