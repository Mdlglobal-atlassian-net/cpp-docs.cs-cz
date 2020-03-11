---
title: funkce a proměnné &lt;mutex&gt;
ms.date: 11/04/2016
f1_keywords:
- mutex/std::adopt_lock
- mutex/std::call_once
- mutex/std::defer_lock
- mutex/std::lock
- mutex/std::try_to_lock
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
helpviewer_keywords:
- std::adopt_lock [C++]
- std::call_once [C++]
- std::defer_lock [C++]
- std::lock [C++]
- std::try_to_lock [C++]
ms.openlocfilehash: f6bd6a86e91c2d59fec2083dcf0ec6314d7c41ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856297"
---
# <a name="ltmutexgt-functions-and-variables"></a>funkce a proměnné &lt;mutex&gt;

## <a name="adopt_lock"></a>adopt_lock

Představuje objekt, který lze předat konstruktorům pro [lock_guard](../standard-library/lock-guard-class.md) a [unique_lock](../standard-library/unique-lock-class.md) k označení toho, že objekt mutex, který je také předán konstruktoru, je uzamčen.

```cpp
const adopt_lock_t adopt_lock;
```

## <a name="call_once"></a>call_once

Poskytuje mechanismus pro volání zadaného volajícího objektu přesně jednou při spuštění.

```cpp
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```

### <a name="parameters"></a>Parametry

*Příznak*\
Objekt [once_flag](../standard-library/once-flag-structure.md) , který zajišťuje, že se volatelné objekty budou volat pouze jednou.

\ *F*
Objekt, který se může volat.

*\*
Seznam argumentů.

### <a name="remarks"></a>Poznámky

Pokud *příznak* není platný, funkce vyvolá [system_error](../standard-library/system-error-class.md) , která má kód chyby `invalid_argument`. V opačném případě funkce šablony používá svůj argument *příznak* k zajištění toho, že volá `F(A...)` úspěšně přesně jednou, bez ohledu na to, kolikrát je funkce šablony volána. Pokud se `F(A...)` ukončí při vyvolání výjimky, volání nebylo úspěšné.

## <a name="defer_lock"></a>defer_lock

Představuje objekt, který lze předat konstruktoru pro [unique_lock](../standard-library/unique-lock-class.md). To znamená, že konstruktor by neměl uzamknout objekt mutex, který je také předán do něj.

```cpp
const defer_lock_t defer_lock;
```

## <a name="lock"></a>získáte

Pokusí se zamknout všechny argumenty bez zablokování.

```cpp
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```

### <a name="remarks"></a>Poznámky

Argumenty funkce šablony musí být *typy mutex*, s výjimkou toho, že volání `try_lock` mohou vyvolat výjimky.

Funkce zamkne všechny své argumenty bez zablokování voláním `lock`, `try_lock`a `unlock`. Pokud volání `lock` nebo `try_lock` vyvolá výjimku, funkce volá `unlock` na jakýkoli objekt mutex, který byl úspěšně uzamčen před opětovnou vyvoláním výjimky.

## <a name="swap"></a>adresu

```cpp
template <class Mutex>
void swap(unique_lock<Mutex>& x, unique_lock<Mutex>& y) noexcept;
```

## <a name="try_lock"></a>try_lock

```cpp
template <class L1, class L2, class... L3> int try_lock(L1&, L2&, L3&...);
```

## <a name="try_to_lock"></a>try_to_lock

Představuje objekt, který lze předat konstruktoru pro [unique_lock](../standard-library/unique-lock-class.md) pro indikaci, že by se měl konstruktor pokusit odemknout `mutex`, který je také předán bez blokování.

```cpp
const try_to_lock_t try_to_lock;
```
