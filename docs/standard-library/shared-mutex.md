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
ms.openlocfilehash: 5dfb0e858bb412daf159ee9efc7dcc13be690886
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336730"
---
# <a name="ltshared_mutex"></a>&lt;shared_mutex>

Záhlaví &lt;shared_mutex> poskytuje synchronizační primitiva pro ochranu sdílených dat, ke kterým lze přistupovat více vlákny. Kromě výhradní řízení přístupu poskytované mutex třídy sdílené mutex třídy také umožňují sdílené vlastnictví více vláken pro nevýhradní přístup. Sdílené objekty mutex lze použít k řízení prostředků, které lze číst v několika vláknech bez vyvolání spor, ale musí být zapsány výhradně jedním vláknem.

&lt;Záhlaví shared_mutex> definuje `shared_mutex` třídy a `shared_timed_mutex` `shared_lock`, šablonu `swap` třídy a funkci šablony pro podporu sdíleného objektu mutex.

|Třídy|Popis|
|-------------|-----------------|
|[shared_mutex třída](#class_shared_mutex)|Sdílený typ mutex, který může být uzamčen výhradně jedním agentem nebo sdílen nevýhradně více agenty.|
|[shared_timed_mutex třída](#class_shared_timed_mutex)|Sdílený časovaný typ mutex, který může být uzamčen výhradně jedním agentem nebo sdílen nevýhradně více agenty.|
|[shared_lock třída](#class_shared_lock)|Šablona třídy, která zabalí sdílený objekt mutex pro podporu operací uzamčení načasované hodu a nevýhradní sdílení více agenty.|

|Functions|Popis|
|---------------|-----------------|
|[Swap](#function_swap)|Zamění obsah sdílených objektů mutex, na které odkazují parametry funkce.|

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

Instance třídy `shared_mutex` je *sdílený typ mutex*, typ, který řídí sdílené vlastnictví mutex v rámci oboru. Sdílený typ mutex splňuje všechny požadavky typu mutex, stejně jako členy pro podporu sdíleného nevýhradního vlastnictví.

Sdílený typ mutex podporuje `lock_shared`další `unlock_shared`metody `try_lock_shared`, a :

- Metoda `lock_shared` blokuje volající vlákno, dokud vlákno získá sdílené vlastnictví mutex.

- Metoda `unlock_shared` uvolní sdílené vlastnictví mutex držené volající vlákno.

- Metoda `try_lock_shared` se pokusí získat sdílené vlastnictví mutex bez blokování. Jeho návratový typ je převoditelný na **bool** a **je true,** pokud metoda získá vlastnictví, ale je jinak **false**.

Třída `shared_timed_mutex` je *sdílený časovaný typ mutex*, typ, který splňuje požadavky typu sdílenému objektu mutex a časovanému mutexu.

Sdílený typ mutex s časem `try_lock_shared_for` `try_lock_shared_until`podporuje další metody a :

- Metoda `try_lock_shared_for` se pokusí získat sdílené vlastnictví mutex, dokud neuplyne doba trvání určená parametrem. Pokud doba trvání není kladná, `try_lock_shared`metoda je ekvivalentní . Metoda se nevrátí v rámci zadané doby trvání, pokud je získáno sdílené vlastnictví. Jeho vrácená hodnota je **true,** pokud metoda získá vlastnictví, ale je jinak **false**.

- Metoda `try_lock_shared_until` se pokusí získat sdílené vlastnictví mutex, dokud neuplyne zadaný absolutní čas. Pokud již uplynul zadaný čas, je `try_lock_shared`metoda ekvivalentní . Metoda nevrátí před čas emitovat, pokud sdílené vlastnictví je získán. Jeho vrácená hodnota je **true,** pokud metoda získá vlastnictví, ale je jinak **false**.

Šablona `shared_lock` třídy rozšiřuje podporu pro časované uzamčení a převod vlastnictví na sdílený objekt mutex. Vlastnictví mutexu lze získat při výstavbě nebo po ní `shared_lock` a může být převedeno na jiný objekt. Objekty `shared_lock` typu lze přesunout, ale ne kopírovat.

> [!WARNING]
> Počínaje Visual Studio 2015, C++ Standardní knihovna typy synchronizace jsou založeny na synchronizaci systému Windows primitiv a již používat ConcRT (s výjimkou případů, kdy cílová platforma je Windows XP). Typy definované &lt;v shared_mutex> by neměly být používány s žádnými typy nebo funkcemi ConcRT.

## <a name="classes"></a>Třídy

### <a name="shared_mutex-class"></a><a name="class_shared_mutex"></a>shared_mutex třída

Třída `shared_mutex` implementuje nerekurzivní objekt mutex se sémantikou sdíleného vlastnictví.

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

### <a name="shared_timed_mutex-class"></a><a name="class_shared_timed_mutex"></a>shared_timed_mutex třída

Třída `shared_timed_mutex` implementuje nerekurzivní objekt mutex se sémantikou sdíleného vlastnictví, která splňuje požadavky na časovaný typ mutex.

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

### <a name="shared_lock-class"></a><a name="class_shared_lock"></a>shared_lock třída

Šablona `shared_lock` třídy řídí sdílené vlastnictví sdíleného objektu mutex v rámci oboru. Parametr šablony musí být sdílený typ mutex.

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

## <a name="functions"></a>Functions

### <a name="swap"></a><a name="function_swap"></a>Swap

Zamění `shared_lock` objekty.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Vymění obsah `shared_lock` dvou objektů. Účinně stejné jako `x.swap(y)`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** &lt;shared_mutex>

**Obor názvů:** std

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[&lt;>mutex](../standard-library/mutex.md)
