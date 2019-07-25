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
ms.openlocfilehash: 7dd72550bc8658158b399e88573526269202f8f4
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450426"
---
# <a name="ltsharedmutex"></a>&lt;shared_mutex>

Hlavička &lt;> shared_mutex poskytuje prvky synchronizace pro ochranu sdílených dat, ke kterým je možné přistupovat pomocí více vláken. Kromě výhradního řízení přístupu, které poskytuje třídy mutex, sdílené třídy Mutex také umožňují sdílení vlastnictví více vlákny pro nevýhradní přístup. Sdílené mutexy lze použít k řízení prostředků, které mohou být čteny několika vlákny, aniž by došlo ke konfliktu časování, ale musí být zapsány výhradně jediným vláknem.

> Hlaviček &lt;shared_mutex definuje třídy `shared_mutex` a `shared_timed_mutex`, třídu `shared_lock`šablony a funkci `swap` šablony pro sdílenou podporu mutex.

|Třídy|Popis|
|-------------|-----------------|
|[shared_mutex Class](#class_shared_mutex)|Sdílený typ mutex, který může být uzamčen výhradně jedním agentem nebo sdíleným neexkluzivně pomocí více agentů.|
|[shared_timed_mutex Class](#class_shared_timed_mutex)|Sdílený typ objektu mutex, který může být uzamčen výhradně jedním agentem nebo sdíleným neexkluzivně pomocí více agentů.|
|[shared_lock Class](#class_shared_lock)|Třída šablony, která obaluje sdílený mutex tak, aby podporovala operace s vypršenou zámkou a neexkluzivní sdílení více agentů.|

|Funkce|Popis|
|---------------|-----------------|
|[swap](#function_swap)|Zamění obsah sdílených objektů mutex, na které odkazují parametry funkce.|

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

Instance třídy `shared_mutex` je *sdílený typ mutex*, což je typ, který řídí sdílené vlastnictví mutex v rámci oboru. Sdílený typ mutex splňuje všechny požadavky typu mutex a také členy pro podporu sdíleného nevýhradního vlastnictví.

Sdílený typ mutex podporuje další metody `lock_shared`, `unlock_shared`a `try_lock_shared`:

- `lock_shared` Metoda blokuje volající vlákno, dokud vlákno nezíská sdílené vlastnictví mutexu.

- `unlock_shared` Metoda uvolní sdílené vlastnictví mutexu uloženého volajícím vláknem.

- `try_lock_shared` Metoda se pokusí získat sdílené vlastnictví mutexu bez blokování. Jeho návratový typ je převoditelný na **bool** a má **hodnotu true** , pokud metoda získá vlastnictví, ale je v opačném případě **false**.

Třída `shared_timed_mutex` je *sdílený typ nesdíleného objektu mutex*, typ, který splňuje požadavky sdíleného typu mutex i časovaného typu mutex.

Sdílený typ s časovým limitem mutex podporuje `try_lock_shared_for` další `try_lock_shared_until`metody a:

- `try_lock_shared_for` Metoda se pokusí získat sdílené vlastnictví mutexu, dokud neuplyne doba zadaná parametrem. Pokud doba trvání není kladná, je metoda ekvivalentní `try_lock_shared`. Metoda se nevrátí v zadané době trvání, pokud se nezíská sdílené vlastnictví. Vrácená hodnota je **true** , pokud metoda získá vlastnictví, ale je v opačném případě **false**.

- `try_lock_shared_until` Metoda se pokusí získat sdílené vlastnictví mutexu, dokud neuplyne zadaný absolutní čas. Pokud již zadaný čas uplynul, je metoda ekvivalentní `try_lock_shared`. Metoda se nevrátí před zadanou dobu, pokud se nezíská sdílené vlastnictví. Vrácená hodnota je **true** , pokud metoda získá vlastnictví, ale je v opačném případě **false**.

Třída `shared_lock` Template rozšiřuje podporu pro časované uzamykání a přenos vlastnictví na sdílený mutex. Vlastnictví mutexu lze získat na nebo po konstrukci a lze je přenést do jiného `shared_lock` objektu. Objekty typu `shared_lock` lze přesunout, ale nikoli kopírovat.

> [!WARNING]
> Počínaje verzí Visual Studio 2015 jsou C++ standardní typy synchronizace knihovny založené na prostředích synchronizace systému Windows a již nepoužívají ConcRT (s výjimkou případů, kdy je cílová platforma Windows XP). Typy definované v &lt;shared_mutex > by neměly být použity s žádnými ConcRT typy nebo funkcemi.

## <a name="classes"></a>Třídy

###  <a name="class_shared_mutex"></a>shared_mutex – třída

Třída `shared_mutex` implementuje nerekurzivní mutex se sémantikou sdíleného vlastnictví.

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

###  <a name="class_shared_timed_mutex"></a>shared_timed_mutex – třída

Třída `shared_timed_mutex` implementuje nerekurzivní mutex se sémantikou sdíleného vlastnictví, která splňuje požadavky typu časově omezená mutex.

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

###  <a name="class_shared_lock"></a>shared_lock – třída

Třída `shared_lock` šablony řídí sdílené vlastnictví sdíleného objektu mutex v rámci oboru. Parametr šablony musí být sdílený typ mutex.

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

###  <a name="function_swap"></a>adresu

Zamění `shared_lock` objekty.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Vyměňuje obsah dvou `shared_lock` objektů. Efektivně stejné jako `x.swap(y)`.

## <a name="requirements"></a>Požadavky

**Header:** &lt;shared_mutex>

**Obor názvů:** std

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[&lt;mutex>](../standard-library/mutex.md)
