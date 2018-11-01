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
ms.openlocfilehash: 8be17c8ab361272678c25326464261e153da6a49
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534404"
---
# <a name="recursivemutex-class"></a>recursive_mutex – třída

Představuje *typ mutex*. Rozdíl od [mutex](../standard-library/mutex-class-stl.md), je dobře definovaný chování volání uzamčení metod pro objekty, které jsou již uzamčena.

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Vytvoří `recursive_mutex` objektu.|
|[~recursive_mutex Destructor](#dtorrecursive_mutex_destructor)|Uvolní všechny prostředky, které jsou používány `recursive_mutex` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[lock](#lock)|Blokuje volající vlákno, dokud vlákno nezíská vlastnictví objektu mutex.|
|[try_lock](#try_lock)|Pokusy o získání vlastnictví mutex bez blokování.|
|[Odemknutí](#unlock)|Uvolní vlastnictví objektu mutex.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vzájemně vyloučeného přístupu >

**Namespace:** std

## <a name="lock"></a>  Zámek

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, metoda vrátí hodnotu okamžitě a uzamčení předchozího zůstává v platnosti.

## <a name="recursive_mutex"></a>  recursive_mutex –

Vytvoří `recursive_mutex` objektu, která není uzamčena.

```cpp
recursive_mutex();
```

## <a name="dtorrecursive_mutex_destructor"></a>  ~ recursive_mutex –

Uvolní všechny prostředky, které jsou používané tímto objektem.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt uzamčen při spuštění destruktoru, není chování definováno.

## <a name="try_lock"></a>  try_lock –

Pokusy o získání vlastnictví `mutex` bez blokování.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud metoda úspěšně nezíská vlastnictví `mutex` nebo pokud volající vlákno již vlastní `mutex**; otherwise, **false`.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, funkce vrátí okamžitě **true**, a uzamčení předchozího zůstává v platnosti.

## <a name="unlock"></a>  Odemknutí

Uvolní vlastnictví objektu mutex.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Tato metoda uvolní vlastnictví `mutex` až po je volána jako tolikrát, kolikrát [Zámek](#lock) a [try_lock –](#try_lock) byla úspěšně volána na `recursive_mutex` objektu.

Pokud volající vlákno není vlastníkem `mutex`, není chování definováno.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex – >](../standard-library/mutex.md)<br/>
