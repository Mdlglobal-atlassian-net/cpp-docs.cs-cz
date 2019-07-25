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
ms.openlocfilehash: 448b4d03e4d38dc45621cddab7d8f5d03b805968
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451675"
---
# <a name="recursivemutex-class"></a>recursive_mutex – třída

Představuje *typ mutex*. Na rozdíl od [mutex](../standard-library/mutex-class-stl.md)je chování volání metody zamykání pro objekty, které jsou již uzamčeny, jasně definovány.

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|`recursive_mutex` Vytvoří objekt.|
|[~recursive_mutex Destructor](#dtorrecursive_mutex_destructor)|Uvolní všechny prostředky, které jsou používány `recursive_mutex` objektem.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[lock](#lock)|Blokuje volající vlákno, dokud vlákno nezíská vlastnictví mutexu.|
|[try_lock](#try_lock)|Pokusy o získání vlastnictví mutexu bez blokování.|
|[Uzamknout](#unlock)|Uvolňuje vlastnictví mutexu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> mutex

**Obor názvů:** std

## <a name="lock"></a>získáte

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, metoda se vrátí okamžitě a předchozí zámek zůstane v platnosti.

## <a name="recursive_mutex"></a>recursive_mutex

`recursive_mutex` Vytvoří objekt, který není uzamčen.

```cpp
recursive_mutex();
```

## <a name="dtorrecursive_mutex_destructor"></a>~ recursive_mutex

Uvolní všechny prostředky, které jsou používány objektem.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt uzamčen při spuštění destruktoru, chování není definováno.

## <a name="try_lock"></a>try_lock

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud metoda úspěšně získá vlastnictví `mutex` nebo v případě, že `mutex**; otherwise, **false`volající vlákno již vlastní.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, funkce okamžitě vrátí **hodnotu true**a předchozí zámek zůstane v platnosti.

## <a name="unlock"></a>Uzamknout

Uvolňuje vlastnictví mutexu.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Tato metoda `mutex` uvolní vlastnictví pouze poté, co je volána, kolikrát bylo volání metody [Lock](#lock) a [try_lock](#try_lock) v `recursive_mutex` objektu úspěšné.

Pokud volající vlákno nevlastní `mutex`, chování není definováno.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
