---
title: '&lt;shared_mutex&gt;'
ms.date: 03/27/2019
f1_keywords:
- <shared_mutex>
- shared_mutex/std::swap
- shared_mutex/std::shared_lock
- shared_mutex/std::shared_lock::shared_lock
- shared_mutex/std::shared_lock::operator=
- shared_mutex/std::shared_lock::operator =
- shared_mutex/std::shared_lock::lock
- shared_mutex/std::shared_lock::try_lock
- shared_mutex/std::shared_lock::try_lock_for
- shared_mutex/std::shared_lock::try_lock_until
- shared_mutex/std::shared_lock::unlock
- shared_mutex/std::shared_lock::swap
- shared_mutex/std::shared_lock::release
- shared_mutex/std::shared_lock::owns_lock
- shared_mutex/std::shared_lock::operator bool
- shared_mutex/std::shared_lock::mutex
- shared_mutex/std::shared_mutex
- shared_mutex/std::shared_mutex::native_handle_type
- shared_mutex/std::shared_mutex::shared_mutex
- shared_mutex/std::shared_mutex::operator=
- shared_mutex/std::shared_mutex::operator =
- shared_mutex/std::shared_mutex::lock
- shared_mutex/std::shared_mutex::try_lock
- shared_mutex/std::shared_mutex::unlock
- shared_mutex/std::shared_mutex::lock_shared
- shared_mutex/std::shared_mutex::try_lock_shared
- shared_mutex/std::shared_mutex::unlock_shared
- shared_mutex/std::shared_mutex::native_handle
- shared_mutex/std::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::operator=
- shared_mutex/std::shared_timed_mutex::operator =
- shared_mutex/std::shared_timed_mutex::lock
- shared_mutex/std::shared_timed_mutex::try_lock
- shared_mutex/std::shared_timed_mutex::try_lock_for
- shared_mutex/std::shared_timed_mutex::try_lock_until
- shared_mutex/std::shared_timed_mutex::unlock
- shared_mutex/std::shared_timed_mutex::lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared_for
- shared_mutex/std::shared_timed_mutex::try_lock_shared_until
- shared_mutex/std::shared_timed_mutex::unlock_shared
ms.assetid: 0b37a97d-ee5d-4050-b29f-09db9f76beb3
ms.openlocfilehash: 97d77399357030feaa90228a1b0cdeb80d48034c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412563"
---
# <a name="ltsharedmutex"></a>&lt;shared_mutex>

&lt;Shared_mutex > záhlaví zajišťující ochranu sdílených dat, který je přístupný ve víc vláknech synchronizací primitiv. Kromě ovládacího prvku výhradní přístup poskytuje třídy vzájemně vyloučený přístup třídy sdílené vzájemně vyloučený přístup také povolí sdílené vlastnictví ve víc vláknech neexkluzivní přístup. Sdílené vzájemně vyloučené přístupy lze použít k řízení prostředků, které může číst několik vláken, aniž by to způsobilo konflikt časování, ale musí být napsaný výhradně jedno vlákno.

Záhlaví &lt;shared_mutex > definuje třídy `shared_mutex` a `shared_timed_mutex`, šablony třídy `shared_lock`a funkce šablon `swap` sdílené podporu vzájemně vyloučený přístup.

|Třídy|Popis|
|-------------|-----------------|
|[shared_mutex Class](#class_shared_mutex)|Typ sdíleného vzájemně vyloučený přístup, který může výhradně uzamčen jednoho agenta nebo jiných výhradně sdílí více agentů.|
|[shared_timed_mutex Class](#class_shared_timed_mutex)|Typ sdílené vypršel časový limit vzájemně vyloučený přístup, který může výhradně uzamčen jednoho agenta nebo jiných výhradně sdílí více agentů.|
|[shared_lock Class](#class_shared_lock)|Třída šablony, která obaluje sdílené vzájemně vyloučený přístup k podpoře neexkluzivní sdílení více agentů a operace vypršel časový limit zámku.|

|Funkce|Popis|
|---------------|-----------------|
|[swap](#function_swap)|Zamění obsah objektů sdílené mutex odkazuje parametry funkce.|

## <a name="syntax"></a>Syntaxe

```cpp
namespace std {
    class shared_mutex;
    class shared_timed_mutex;
    template <class Mutex>
class shared_lock;
    template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
}
```

## <a name="remarks"></a>Poznámky

Instance třídy `shared_mutex` je *sdílený typ mutex*, typ, který řídí sdílené vlastnictví objektu mutex v rámci oboru. Typ sdíleného mutex splňuje všechny požadavky typu vzájemně vyloučený přístup, a také členové pro podporu sdílené vlastnictví neexkluzivní.

Typ sdíleného mutex podporuje další metody `lock_shared`, `unlock_shared`, a `try_lock_shared`:

- `lock_shared` Metoda blokuje volající vlákno, dokud vlákno nezíská sdílené vlastnictví objektu mutex.

- `unlock_shared` Metoda uvolní sdílené vlastnictví objektu mutex drží volajícího vlákna.

- `try_lock_shared` Metoda se pokusí získat sdílené vlastnictví objektu mutex bez blokování. Její typ vrácené hodnoty je převést na **bool** a je **true** Pokud metoda získává vlastnictví, ale jinak **false**.

Třída `shared_timed_mutex` je *vypršel časový limit mutex typ sdíleného*, zadejte typ, který splňuje požadavky obou sdílené vzájemně vyloučený přístup a zadejte vypršel časový limit zámku.

Typ sdíleného vypršel časový limit mutex podporuje další metody `try_lock_shared_for` a `try_lock_shared_until`:

- `try_lock_shared_for` Metoda se pokusí získat sdílené vlastnictví objektu mutex, až do uplynutí doby trvání určené parametrem. Pokud doba trvání není kladná, metoda je ekvivalentní k `try_lock_shared`. Metoda nevrací v rámci doby trvání zadat, pokud se získá sdílené vlastnictví. Vrácená hodnota je **true** Pokud metoda získává vlastnictví, ale jinak **false**.

- `try_lock_shared_until` Metoda se pokusí získat sdílené vlastnictví objektu mutex, až do uplynutí zadaného absolutním čase. Pokud již uplynutí zadané doby, metoda je ekvivalentní k `try_lock_shared`. Metoda nevrací před získané za dobu určenou Pokud sdílené vlastnictví. Vrácená hodnota je **true** Pokud metoda získává vlastnictví, ale jinak **false**.

`shared_lock` Šablony třídy rozšiřuje podporu pro vypršel časový limit zámku a převod vlastnictví sdíleného vzájemně vyloučený přístup. Vlastnictví objektu mutex mohou být získány na nebo za vytváření a může být převedeno do jiného `shared_lock` objektu. Objekty typu `shared_lock` lze přesunout, ale ne zkopírovat.

> [!WARNING]
> Synchronizace typy standardní knihovny C++ od v sadě Visual Studio 2015, jsou založené na Windows synchronizací primitiv a již nebudete používat ConcRT (s výjimkou případu, kdy Cílová platforma Windows XP). Typy definované v &lt;shared_mutex > se nemá používat s všechny typy ConcRT nebo funkce.

## <a name="classes"></a>Třídy

###  <a name="class_shared_mutex"></a> shared_mutex třídy

Třída `shared_mutex` implementuje nerekurzivní mutex se sémantikou sdílené vlastnictví.

```cpp
class shared_mutex {
public:
   shared_mutex();
   ~shared_mutex();
   shared_mutex(const shared_mutex&) = delete;
   shared_mutex& operator=(const shared_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   void unlock_shared();
   // Getters
   typedef void** native_handle_type; // implementation defined
   native_handle_type native_handle();
   };
```

###  <a name="class_shared_timed_mutex"></a> shared_timed_mutex Class

Třída `shared_timed_mutex` implementuje nerekurzivní mutex se sémantikou sdílené vlastnictví, které splňuje požadavky na typ mutex vypršel časový limit.

```cpp
class shared_timed_mutex {
public:
   shared_timed_mutex();
   ~shared_timed_mutex();
   shared_timed_mutex(const shared_timed_mutex&) = delete;
   shared_timed_mutex& operator=(const shared_timed_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   template <class Rep, class Period>
   bool try_lock_shared_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_shared_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock_shared();
   };
```

###  <a name="class_shared_lock"></a> shared_lock třídy

Třída šablony `shared_lock` řídí sdílené vlastnictví objektu mutex sdílené v rámci oboru. Parametr šablony musí být typu sdílené vzájemně vyloučený přístup.

```cpp
class shared_lock {
public:
   typedef Mutex mutex_type;
   shared_lock() noexcept;
   explicit shared_lock(mutex_type& m);
   // blocking
   shared_lock(mutex_type& m, defer_lock_t) noexcept;
   shared_lock(mutex_type& m, try_to_lock_t);
   shared_lock(mutex_type& m, adopt_lock_t);
   template <class Clock, class Duration>
   shared_lock(mutex_type& m,
   const chrono::time_point<Clock, Duration>& abs_time);
   template <class Rep, class Period>
   shared_lock(mutex_type& m,
   const chrono::duration<Rep, Period>& rel_time);
   ~shared_lock();
   shared_lock(shared_lock const&) = delete;
   shared_lock& operator=(shared_lock const&) = delete;
   shared_lock(shared_lock&& u) noexcept;
   shared_lock& operator=(shared_lock&& u) noexcept;
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Setters
   void swap(shared_lock& u) noexcept;
   mutex_type* release() noexcept;
   // Getters
   bool owns_lock() const noexcept;
   explicit operator bool () const noexcept;
   mutex_type* mutex() const noexcept;
private:
   mutex_type* pm; // exposition only
   bool owns; // exposition only
   };
```

## <a name="functions"></a>Funkce

###  <a name="function_swap"></a> Prohození

Zamění `shared_lock` objekty.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Vymění obsahu dvou `shared_lock` objekty. Efektivně stejný jako `x.swap(y)`.

## <a name="requirements"></a>Požadavky

**Header:** &lt;shared_mutex>

**Namespace:** std

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[&lt;mutex>](../standard-library/mutex.md)
