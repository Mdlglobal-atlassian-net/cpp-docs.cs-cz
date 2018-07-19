---
title: '&lt;objekt mutex&gt; funkce a proměnné | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: df52b5bdf9b7054fd838b1892c4e641cdf9d4dcc
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962185"
---
# <a name="ltmutexgt-functions-and-variables"></a>&lt;objekt mutex&gt; funkce a proměnné

||||
|-|-|-|
|[adopt_lock](#adopt_lock)|[call_once](#call_once)|[defer_lock](#defer_lock)|
|[lock](#lock)|[try_to_lock](#try_to_lock)|

## <a name="adopt_lock"></a>  adopt_lock – proměnná

Představuje objekt, který může být předán konstruktory pro [lock_guard –](../standard-library/lock-guard-class.md) a [unique_lock –](../standard-library/unique-lock-class.md) k označení, že objekt mutex také předávaný do konstruktoru je uzamčen.

```cpp
const adopt_lock_t adopt_lock;
```

## <a name="call_once"></a>  call_once –

Poskytuje mechanismus pro volání zadané volatelný objekt právě jednou během provádění.

```cpp
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```

### <a name="parameters"></a>Parametry

*Příznak* A [once_flag –](../standard-library/once-flag-structure.md) objekt, který zajistí, že volatelný objekt je volat pouze jednou.

*F* volatelný objekt.

*A* seznam argumentů.

### <a name="remarks"></a>Poznámky

Pokud *příznak* není platný, funkce vyvolá [system_error](../standard-library/system-error-class.md) , který má kód chyby `invalid_argument`. V opačném případě funkce šablony používá jeho *příznak* argument k zajištění, že volá `F(A...)` úspěšně právě jednou, bez ohledu na to, kolikrát je volána funkce šablony. Pokud `F(A...)` ukončen vyvoláním výjimky, volání nebylo úspěšné.

## <a name="defer_lock"></a>  defer_lock – proměnná

Představuje objekt, který může být předán konstruktoru pro [unique_lock –](../standard-library/unique-lock-class.md). To znamená, že by neměl konstruktor zamknout objekt mutex také předávaný do něj.

```cpp
const defer_lock_t defer_lock;
```

## <a name="lock"></a>  Zámek

Se pokusí uzamknout všechny argumenty bez zablokování.

```cpp
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```

### <a name="remarks"></a>Poznámky

Argumenty funkce šablony musí být *mutex typy*, s výjimkou, která volá do `try_lock` může vyvolat výjimky.

Všechny argumenty bez zablokování funkci uzamkne voláním `lock`, `try_lock`, a `unlock`. Pokud je volání `lock` nebo `try_lock` vyvolá výjimku, volání funkce `unlock` na některý objekt mutex objekty, které byly úspěšně uzamčena před opětné vyvolání výjimky.

## <a name="try_to_lock"></a>  try_to_lock – proměnná

Představuje objekt, který může být předán konstruktoru pro [unique_lock –](../standard-library/unique-lock-class.md) k označení, že by měl konstruktoru pokusu o odemknutí `mutex` , který je také funkci ji bez blokování.

```cpp
const try_to_lock_t try_to_lock;
```

## <a name="see-also"></a>Viz také:

[\<mutex – >](../standard-library/mutex.md)<br/>
