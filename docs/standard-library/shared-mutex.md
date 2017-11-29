---
title: '&lt;shared_mutex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
ms.assetid: 0b37a97d-ee5d-4050-b29f-09db9f76beb3
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cdca4861161a82521fab07a8d503d5d0dd84fbf9
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="ltsharedmutex"></a>&lt;shared_mutex >

&lt;Shared_mutex > záhlaví poskytuje synchronizace primitiv pro ochranu sdílených datech, která je přístupná více vláken. Kromě prvku výhradní přístup poskytované mutex třídy třídy sdílené mutex také povolení sdílené vlastnictví podle více vláken pro nikoli výhradní přístup. Sdílené objekty mutex můžete použít k řízení prostředky, které může číst několik vlákna, aniž by to způsobilo konflikt časování, ale musí být napsané výhradně funkcí jedno vlákno.

Záhlaví &lt;shared_mutex > definuje třídy `shared_mutex` a `shared_timed_mutex`, šablony třídy `shared_lock`a funkce šablony `swap` pro objekt mutex podpora sdílených.

|Třídy|Popis|
|-------------|-----------------|
|[shared_mutex – třída](../standard-library/shared-mutex.md#class_shared_mutex)|Sdílené mutex typ, který můžete zamčeny jednoho agenta nebo jiných výhradně sdílen více agenty.|
|[shared_timed_mutex – třída](../standard-library/shared-mutex.md#class_shared_timed_mutex)|Sdílené vypršel mutex typ, který můžete zamčeny jednoho agenta nebo jiných výhradně sdílen více agenty.|
|[shared_lock – třída](../standard-library/shared-mutex.md#class_shared_lock)|Třída šablony, která zabalí sdílené mutex pro podporu operací časově uzamknout a nikoli výhradní sdílení více agenty.|

|Funkce|Popis|
|---------------|-----------------|
|[swap](../standard-library/shared-mutex.md#function_swap)|Zamění obsah objektů sdílené mutex odkazuje parametry funkce.|

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

Instance třídy `shared_mutex` je *sdílené mutex typ*, typ, který řídí sdílené vlastnictví mutex v rámci oboru. Typ sdílené mutex splňuje všechny požadavky typu mutex, jakož i členy pro podporu sdílené nikoli výhradní vlastnictví.

Typ sdílené mutex podporuje další metody `lock_shared`, `unlock_shared`, a `try_lock_shared`:

- `lock_shared` Metoda blokuje volající vlákno, dokud vlákno získá sdílený vlastnictví mutex.

- `unlock_shared` Metoda uvolní sdílené vlastnictví mutex držené volající vlákno.

- `try_lock_shared` Metoda se pokusí získat sdílený vlastnictví mutex bez blokování. Její návratový typ je převést na `bool` a je `true` Pokud metoda získá vlastnictví, ale jinak `false`.

Třída `shared_timed_mutex` je *sdílené vypršel mutex typ*zadejte typ, který splňuje požadavky obou sdílené mutex a časově mutex zadejte.

Typ sdílené vypršel mutex podporuje další metody `try_lock_shared_for` a `try_lock_shared_until`:

- `try_lock_shared_for` Metoda se pokusí získat sdílený vlastnictví mutex až do doby trvání určený parametrem. Pokud doba trvání není kladná, je ekvivalentní metodě `try_lock_shared`. Metoda nevrátí v zadaném určit, pokud se získávají sdílené vlastnictví. Vrácená hodnota je `true` Pokud metoda získá vlastnictví, ale jinak `false`.

- `try_lock_shared_until` Metoda se pokusí získat sdílený vlastnictví mutex až do zadaného absolutním čase. Pokud již uplynutí zadané doby je ekvivalentem na metodu `try_lock_shared`. Metoda nevrátí předtím, než se získávají za dobu určenou Pokud sdílené vlastnictví. Vrácená hodnota je `true` Pokud metoda získá vlastnictví, ale jinak `false`.

`shared_lock` Šablony třídy rozšiřuje podporu pro vypršel časový limit zámku a přenos vlastnictví sdíleného mutex. Vlastnictví mutex lze získat v nebo po konstrukce a může přenést na jiný `shared_lock` objektu. Objekty typu `shared_lock` můžete přesunout, ale není zkopírovali.

> [!WARNING]
> Od verze sady Visual Studio 2015, typy synchronizace standardní knihovna C++ jsou založené na Windows synchronizace primitiv a nadále používat ConcRT (kromě případů, kdy cílové platformy systému Windows XP). Typy definované v &lt;shared_mutex > by se neměla používat s žádné ConcRT typů nebo funkcí.

## <a name="classes"></a>Třídy

###  <a name="class_shared_mutex"></a>shared_mutex – třída

Třída `shared_mutex` implementuje tohoto nerekurzivního mutex s sémantiku sdílené vlastnictví.

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

Třída `shared_timed_mutex` implementuje tohoto nerekurzivního mutex s sémantiku sdílené vlastnictví, který splňuje požadavky na vypršel mutex typu.

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

###  <a name="&lt;shared"></a>shared_lock – třída

Šablony třídy `shared_lock` řídí sdílené vlastnictví objekt mutex sdílené v rámci oboru. Parametr šablony musí být typu sdílené mutex.

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

###  <a name="function_swap"></a>swap

Umožňuje přepnout `shared_lock` objekty.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Výměny obsah dva `shared_lock` objekty. Efektivně stejný jako `x.swap(y)`.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** &lt;shared_mutex >

 **Namespace:** – std

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)  
[&lt;mutex >](../standard-library/mutex.md)