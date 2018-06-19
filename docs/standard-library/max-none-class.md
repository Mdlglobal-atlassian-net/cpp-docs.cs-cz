---
title: max_none – třída | Microsoft Docs
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
ms.openlocfilehash: 97cb713eda7a11874893bc9fc8a13b3b0784f29a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854025"
---
# <a name="maxnone-class"></a>max_none – třída

Popisuje [maximálního počtu třída](../standard-library/allocators-header.md) objekt, který omezuje [freelist](../standard-library/freelist-class.md) objekt, který má maximální délku nula.

## <a name="syntax"></a>Syntaxe

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`Max`|Maximální třídu, která určuje maximální počet elementů k uložení v `freelist`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Přidělené](#allocated)|Zvětší počet bloků přidělené paměti.|
|[Zrušeno](#deallocated)|Snižuje počet přidělené bloky paměti.|
|[Úplná](#full)|Vrátí hodnotu, která určuje, zda více bloky paměti by měla být přidán do seznamu volné.|
|[Vydání](#released)|Snižuje počet paměti bloků v seznamu volné.|
|[saved](#saved)|Zvýší počet bloky paměti v seznamu volné.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<alokátorů >

**Namespace:** stdext –

## <a name="allocated"></a>  max_none::allocated

Zvětší počet bloků přidělené paměti.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`_Nx`|Hodnota přírůstku.|

### <a name="remarks"></a>Poznámky

Tato funkce člen neprovede žádnou akci. Je volána po každém úspěšném volání pomocí `cache_freelist::allocate` operátor `new`. Argument `_Nx` je počet bloků paměti v bloku dat přidělené operátor `new`.

## <a name="deallocated"></a>  max_none::deallocated

Snižuje počet přidělené bloky paměti.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|`_Nx`|Hodnota přírůstku.|

### <a name="remarks"></a>Poznámky

Členská funkce neprovede žádnou akci. Tato funkce člen je volána po každé pro volání `cache_freelist::deallocate` operátor `delete`. Argument `_Nx` je počet bloků paměti v bloku dat navrácena operátorem `delete`.

## <a name="full"></a>  max_none::full

Vrátí hodnotu, která určuje, zda více bloky paměti by měla být přidán do seznamu volné.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

Členské funkce vždy vrátí hodnotu `true`.

### <a name="remarks"></a>Poznámky

Tento člen funkce volá `cache_freelist::deallocate`. Pokud se volání vrátí `true`, `deallocate` vloží bloku paměti v seznamu volné; Pokud vrátí hodnotu false, `deallocate` operátor volání `delete` se zrušit přidělení bloku.

## <a name="released"></a>  max_none::released

Snižuje počet paměti bloků v seznamu volné.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Tato funkce člen neprovede žádnou akci. `released` Je volána funkce člena třídy aktuální maximální `cache_freelist::allocate` vždy, když odebere blok paměti ze seznamu volné.

## <a name="saved"></a>  max_none::saved

Zvýší počet bloky paměti v seznamu volné.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato funkce člen neprovede žádnou akci. Je volána metodou `cache_freelist::deallocate` vždy, když vloží blok paměti v seznamu volné.

## <a name="see-also"></a>Viz také

[\<alokátorů >](../standard-library/allocators-header.md)<br/>
