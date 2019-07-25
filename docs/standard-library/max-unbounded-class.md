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
ms.openlocfilehash: cea2f09837e5efc6969e4ab305d106b9c9728412
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447203"
---
# <a name="maxunbounded-class"></a>max_unbounded – třída

Popisuje [maximální objekt třídy](../standard-library/allocators-header.md) , který neomezuje maximální délku objektu [freelist –](../standard-library/freelist-class.md) .

## <a name="syntax"></a>Syntaxe

```cpp
class max_unbounded
```

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

## <a name="allocated"></a>max_unbounded:: přiděleno

Zvýší počet přidělených bloků paměti.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*_Nx*|Přírůstková hodnota.|

### <a name="remarks"></a>Poznámky

Tato členská funkce neprovede žádnou akci. Je volána po každém úspěšném volání metody `cache_freelist::allocate` operator **New**. Argument *_Nx* je počet paměťových bloků v bloku, který je přidělený operátorem **New**.

## <a name="deallocated"></a>max_unbounded::d eallocated

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

## <a name="full"></a>max_unbounded:: Full

Vrátí hodnotu, která určuje, zda mají být do bezplatného seznamu přidány další bloky paměti.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

Členská funkce vždycky vrátí **hodnotu false**.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `cache_freelist::deallocate`nástrojem. Pokud volání vrátí **hodnotu true**, `deallocate` umístí blok paměti do bezplatného seznamu; Pokud vrátí hodnotu false, `deallocate` volá operátor **DELETE pro zrušení** přidělení bloku.

## <a name="released"></a>max_unbounded:: vydáno

Sníží počet bloků paměti v bezplatném seznamu.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce neprovede žádnou akci. Členská funkce aktuální třídy maxima je `cache_freelist::allocate` volána při každém odebrání bloku paměti ze seznamu Free. `released`

## <a name="saved"></a>max_unbounded:: Uloženo

Zvýší počet bloků paměti v bezplatném seznamu.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato členská funkce neprovede žádnou akci. Je volána `cache_freelist::deallocate` při každém vložení bloku paměti do bezplatného seznamu.

## <a name="see-also"></a>Viz také:

[\<allocators>](../standard-library/allocators-header.md)
