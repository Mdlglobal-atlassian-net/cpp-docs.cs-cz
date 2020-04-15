---
title: třída mutex (standardní knihovna Jazyka C++)| Dokumenty společnosti Microsoft
ms.date: 11/04/2016
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 84e6e3a46903a204444df9886556ae2c563304a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364849"
---
# <a name="mutex-class-c-standard-library"></a>třída mutex (standardní knihovna Jazyka C++)

Představuje *typ mutex*. Objekty tohoto typu lze použít k vynucení vzájemnévyloučení v rámci programu.

## <a name="syntax"></a>Syntaxe

```cpp
class mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Mutex](#mutex)|Vytvoří `mutex` objekt.|
|[mutex::~mutex Destructor](#dtormutex_destructor)|Uvolní všechny prostředky, které `mutex` byly použity objektem.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Zámek](#lock)|Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`rozhraní .|
|[native_handle](#native_handle)|Vrátí typ specifický pro implementaci, který představuje popisovač mutex.|
|[try_lock](#try_lock)|Pokusí se získat vlastnictví `mutex` bez blokování.|
|[Odemknout](#unlock)|Uvolní vlastnictví . `mutex`|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> mutex

**Obor názvů:** std

## <a name="mutexlock"></a><a name="lock"></a>mutex::zámek

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`rozhraní .

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , chování není definováno.

## <a name="mutexmutex-constructor"></a><a name="mutex"></a>mutex::konstruktor objektu mutex

Vytvoří `mutex` objekt, který není uzamčen.

```cpp
constexpr mutex() noexcept;
```

## <a name="mutexmutex-destructor"></a><a name="dtormutex_destructor"></a>mutex::~mutex Destructor

Uvolní všechny prostředky, které `mutex` jsou používány objektem.

```cpp
~mutex();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt uzamčen při spuštění destruktoru, chování není definováno.

## <a name="mutexnative_handle"></a><a name="native_handle"></a>mutex::native_handle

Vrátí typ specifický pro implementaci, který představuje popisovač mutex. Popisovač mutex lze použít v konkrétních způsobů implementace.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

`native_handle_type`je definována `Concurrency::critical_section *` jako, že `void *`je obsazení jako .

## <a name="mutextry_lock"></a><a name="try_lock"></a>mutex::try_lock

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud metoda úspěšně získá `mutex`vlastnictví ; jinak **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , chování není definováno.

## <a name="mutexunlock"></a><a name="unlock"></a>mutex::odemknutí

Uvolní vlastnictví . `mutex`

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno nevlastní `mutex`, chování není definováno.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
