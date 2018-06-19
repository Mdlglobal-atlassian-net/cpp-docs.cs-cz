---
title: max_unbounded – třída | Microsoft Docs
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
ms.openlocfilehash: 679db380dabf15786776a6896c931f584ef46fce
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864096"
---
# <a name="maxunbounded-class"></a>max_unbounded – třída

Popisuje [maximálního počtu třída](../standard-library/allocators-header.md) objekt, který neomezuje maximální délku [freelist](../standard-library/freelist-class.md) objektu.

## <a name="syntax"></a>Syntaxe

```cpp
class max_unbounded
```

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

## <a name="allocated"></a>  max_unbounded::allocated

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

## <a name="deallocated"></a>  max_unbounded::deallocated

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

## <a name="full"></a>  max_unbounded::full

Vrátí hodnotu, která určuje, zda více bloky paměti by měla být přidán do seznamu volné.

```cpp
bool full();
```

### <a name="return-value"></a>Návratová hodnota

Členská funkce vždy vrátí hodnotu `false`.

### <a name="remarks"></a>Poznámky

Tento člen funkce volá `cache_freelist::deallocate`. Pokud se volání vrátí `true`, `deallocate` vloží bloku paměti v seznamu volné; Pokud vrátí hodnotu false, `deallocate` operátor volání `delete` se zrušit přidělení bloku.

## <a name="released"></a>  max_unbounded::released

Snižuje počet paměti bloků v seznamu volné.

```cpp
void released();
```

### <a name="remarks"></a>Poznámky

Tato funkce člen neprovede žádnou akci. `released` Je volána funkce člena třídy aktuální maximální `cache_freelist::allocate` vždy, když odebere blok paměti ze seznamu volné.

## <a name="saved"></a>  max_unbounded::saved

Zvýší počet bloky paměti v seznamu volné.

```cpp
void saved();
```

### <a name="remarks"></a>Poznámky

Tato funkce člen neprovede žádnou akci. Je volána metodou `cache_freelist::deallocate` vždy, když vloží blok paměti v seznamu volné.

## <a name="see-also"></a>Viz také

[\<alokátorů >](../standard-library/allocators-header.md)<br/>
