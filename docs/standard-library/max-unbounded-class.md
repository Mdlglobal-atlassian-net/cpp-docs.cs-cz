---
title: max_unbounded – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3bf2d24ad916a9f7dba5a61ecb7745c3d86573c9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955796"
---
# <a name="maxunbounded-class"></a>max_unbounded – třída

Popisuje [maximálního počtu tříd](../standard-library/allocators-header.md) objekt, který neomezuje maximální délku [freelist](../standard-library/freelist-class.md) objektu.

## <a name="syntax"></a>Syntaxe

```cpp
class max_unbounded
```

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

## <a name="allocated"></a>  max_unbounded::allocated

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

## <a name="deallocated"></a>  max_unbounded::deallocated

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

## <a name="full"></a>  max_unbounded::full

Vrátí hodnotu, která určuje, zda by měl být další bloky paměti přidat do seznamu zdarma.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

Členská funkce vždy vrátí **false**.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `cache_freelist::deallocate`. Pokud volání vrátí **true**, `deallocate` vloží blok paměti v seznamu zdarma; Pokud vrátí hodnotu false, `deallocate` operátor volání **odstranit** se uvolnit bloku.

## <a name="released"></a>  max_unbounded::released

Sníží počet paměti blokuje v seznamu zdarma.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce nemá žádný účinek. `released` Členské funkce třídy aktuální maximální volá `cache_freelist::allocate` vždy, když ji odebere blok paměti ze seznamu zdarma.

## <a name="saved"></a>  max_unbounded::saved

Zvýší počet paměťových bloků v seznamu zdarma.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce nemá žádný účinek. Je volána metodou `cache_freelist::deallocate` vždy, když umístí blok paměti v seznamu zdarma.

## <a name="see-also"></a>Viz také:

[\<alokátory: >](../standard-library/allocators-header.md)<br/>
