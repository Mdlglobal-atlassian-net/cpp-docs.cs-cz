---
title: recursive_mutex – třída
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: 9ab7a96a7c07582450ab41b140dcc5494a63661f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320210"
---
# <a name="recursive_mutex-class"></a>recursive_mutex – třída

Představuje *typ mutex*. Na rozdíl od [mutex](../standard-library/mutex-class-stl.md), chování volání uzamčení metody pro objekty, které jsou již uzamčeny je dobře definována.

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Vytvoří `recursive_mutex` objekt.|
|[~recursive_mutex Destruktor](#dtorrecursive_mutex_destructor)|Uvolní všechny prostředky, které `recursive_mutex` jsou používány objektem.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Zámek](#lock)|Blokuje volající vlákno, dokud vlákno nezíská vlastnictví objektu mutex.|
|[try_lock](#try_lock)|Pokusí se získat vlastnictví mutex bez blokování.|
|[Odemknout](#unlock)|Uvolní vlastnictví mutex.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> mutex

**Obor názvů:** std

## <a name="lock"></a><a name="lock"></a>Zámek

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`rozhraní .

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , metoda se vrátí okamžitě a předchozí zámek zůstane v platnosti.

## <a name="recursive_mutex"></a><a name="recursive_mutex"></a>recursive_mutex

Vytvoří `recursive_mutex` objekt, který není uzamčen.

```cpp
recursive_mutex();
```

## <a name="recursive_mutex"></a><a name="dtorrecursive_mutex_destructor"></a>~recursive_mutex

Uvolní všechny prostředky, které jsou používány objektem.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt uzamčen při spuštění destruktoru, chování není definováno.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true** pokud metoda úspěšně získá vlastnictví `mutex` nebo pokud volající vlákno `mutex**; otherwise, **false`již vlastní .

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , funkce okamžitě vrátí **hodnotu true**a předchozí zámek zůstane v platnosti.

## <a name="unlock"></a><a name="unlock"></a>Odemknout

Uvolní vlastnictví mutex.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Tato metoda uvolní vlastnictví `mutex` pouze poté, co je volána tolikrát, [kolikrát zámek](#lock) a [try_lock](#try_lock) byly úspěšně volány na objekt. `recursive_mutex`

Pokud volající vlákno nevlastní `mutex`, chování není definováno.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
