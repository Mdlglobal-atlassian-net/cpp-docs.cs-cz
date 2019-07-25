---
title: Mutex – TřídaC++ (standardní knihovna) | Microsoft Docs
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
ms.openlocfilehash: 099cf17db7b99f9cd1d953a603db70f75c33358e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457058"
---
# <a name="mutex-class-c-standard-library"></a>Mutex – TřídaC++ (standardní knihovna)

Představuje *typ mutex*. Objekty tohoto typu lze použít k prosazování vzájemného vyloučení v rámci programu.

## <a name="syntax"></a>Syntaxe

```cpp
class mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[objekt](#mutex)|`mutex` Vytvoří objekt.|
|[mutex:: ~ mutex – destruktor](#dtormutex_destructor)|Uvolní všechny prostředky, které byly použity `mutex` objektem.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[lock](#lock)|Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`.|
|[native_handle](#native_handle)|Vrátí typ specifický pro implementaci, který reprezentuje popisovač mutex.|
|[try_lock](#try_lock)|Pokusí se získat vlastnictví `mutex` bez blokování.|
|[Uzamknout](#unlock)|Uvolňuje vlastnictví `mutex`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> mutex

**Obor názvů:** std

## <a name="lock"></a>mutex:: Lock

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, chování není definováno.

## <a name="mutex"></a>mutex:: mutex – konstruktor

`mutex` Vytvoří objekt, který není uzamčen.

```cpp
constexpr mutex() noexcept;
```

## <a name="dtormutex_destructor"></a>mutex:: ~ mutex – destruktor

Uvolní všechny prostředky, které jsou používány `mutex` objektem.

```cpp
~mutex();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt uzamčen při spuštění destruktoru, chování není definováno.

## <a name="native_handle"></a>mutex:: native_handle

Vrátí typ specifický pro implementaci, který reprezentuje popisovač mutex. Popisovač mutex lze použít v způsobech specifických pro implementaci.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

`native_handle_type`je definován jako `Concurrency::critical_section *` přetypování jako `void *`.

## <a name="try_lock"></a>mutex:: try_lock

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud metoda úspěšně získá vlastnictví `mutex`, v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, chování není definováno.

## <a name="unlock"></a>mutex:: Unlock

Uvolňuje vlastnictví `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno nevlastní `mutex`, chování není definováno.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
