---
title: mutex – třída (standardní knihovna C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
dev_langs:
- C++
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: 84a6b685501927d9fbd79fa7c82a90c5671f70b2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958942"
---
# <a name="mutex-class-c-standard-library"></a>mutex – třída (standardní knihovna C++)

Představuje *typ mutex*. Objekty tohoto typu lze použít k zajištění vzájemného vyloučení v rámci programu.

## <a name="syntax"></a>Syntaxe

```cpp
class mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[objekt mutex](#mutex)|Vytvoří `mutex` objektu.|
|[mutex:: ~ mutex – destruktor](#dtormutex_destructor)|Uvolní všechny prostředky, které byly používány `mutex` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[lock](#lock)|Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`.|
|[native_handle –](#native_handle)|Vrátí typ specifický pro implementaci představující popisovač mutex.|
|[try_lock](#try_lock)|Pokusy o získání vlastnictví `mutex` bez blokování.|
|[Odemknutí](#unlock)|Uvolní vlastnictví objektu `mutex`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vzájemně vyloučeného přístupu >

**Namespace:** std

## <a name="lock"></a>  mutex::LOCK –

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, není chování definováno.

## <a name="mutex"></a>  mutex::mutex – konstruktor

Vytvoří `mutex` objektu, která není uzamčena.

```cpp
constexpr mutex() noexcept;
```

## <a name="dtormutex_destructor"></a>  mutex:: ~ mutex – destruktor

Uvolní všechny prostředky, které jsou používány `mutex` objektu.

```cpp
~mutex();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt uzamčen při spuštění destruktoru, není chování definováno.

## <a name="native_handle"></a>  mutex::native_handle –

Vrátí typ specifický pro implementaci představující popisovač mutex. Popisovač mutex je možné způsoby specifický pro implementaci.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

`native_handle_type` je definován jako `Concurrency::critical_section *` , který je typovaná jako `void *`.

## <a name="try_lock"></a>  mutex::try_lock –

Pokusy o získání vlastnictví `mutex` bez blokování.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud metoda úspěšně nezíská vlastnictví `mutex`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, není chování definováno.

## <a name="unlock"></a>  mutex::Unlock –

Uvolní vlastnictví objektu `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno není vlastníkem `mutex`, není chování definováno.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex – >](../standard-library/mutex.md)<br/>
