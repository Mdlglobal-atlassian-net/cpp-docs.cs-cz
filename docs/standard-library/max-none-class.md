---
title: max_none – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 44981141be5bfb4f18cb278e724ab905aebcc5cf
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964168"
---
# <a name="maxnone-class"></a>max_none – třída

Popisuje [maximálního počtu tříd](../standard-library/allocators-header.md) objekt, který omezuje [freelist](../standard-library/freelist-class.md) objekt má maximální délku nula.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Max*|Maximální třídu, která určuje maximální počet prvků k ukládání `freelist`.|

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

## <a name="allocated"></a>  max_none::allocated

Zvýší počet přidělených paměťových bloků.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Přírůstková hodnota.|

### <a name="remarks"></a>Poznámky

Tato členská funkce nemá žádný účinek. Volá se po každé úspěšné volání podle `cache_freelist::allocate` operátoru **nové**. Argument *_Nx* je počet paměťových bloků v bloku dat přidělena pomocí operátoru **nové**.

## <a name="deallocated"></a>  max_none::deallocated

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

## <a name="full"></a>  max_none::full

Vrátí hodnotu, která určuje, zda by měl být další bloky paměti přidat do seznamu zdarma.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

Tato členská funkce vždy vrátí **true**.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `cache_freelist::deallocate`. Pokud volání vrátí **true**, `deallocate` vloží blok paměti v seznamu zdarma; Pokud vrátí hodnotu false, `deallocate` operátor volání **odstranit** se uvolnit bloku.

## <a name="released"></a>  max_none::released

Sníží počet paměti blokuje v seznamu zdarma.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce nemá žádný účinek. `released` Členské funkce třídy aktuální maximální volá `cache_freelist::allocate` vždy, když ji odebere blok paměti ze seznamu zdarma.

## <a name="saved"></a>  max_none::saved

Zvýší počet paměťových bloků v seznamu zdarma.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce nemá žádný účinek. Je volána metodou `cache_freelist::deallocate` vždy, když umístí blok paměti v seznamu zdarma.

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)<br/>
