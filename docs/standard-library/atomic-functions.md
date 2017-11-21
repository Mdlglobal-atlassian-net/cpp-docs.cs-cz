---
title: '&lt;Atomic&gt; funkce | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- atomic/std::atomic_compare_exchange_strong
- atomic/std::atomic_compare_exchange_strong_explicit
- atomic/std::atomic_compare_exchange_weak
- atomic/std::atomic_compare_exchange_weak_explicit
- atomic/std::atomic_exchange
- atomic/std::atomic_exchange_explicit
- atomic/std::atomic_fetch_add
- atomic/std::atomic_fetch_add_explicit
- atomic/std::atomic_fetch_and
- atomic/std::atomic_fetch_and_explicit
- atomic/std::atomic_fetch_or
- atomic/std::atomic_fetch_or_explicit
- atomic/std::atomic_fetch_sub
- atomic/std::atomic_fetch_sub_explicit
- atomic/std::atomic_fetch_xor
- atomic/std::atomic_fetch_xor_explicit
- atomic/std::atomic_flag_clear
- atomic/std::atomic_flag_clear_explicit
- atomic/std::atomic_flag_test_and_set
- atomic/std::atomic_flag_test_and_set_explicit
- atomic/std::atomic_init
- atomic/std::atomic_is_lock_free
- atomic/std::atomic_load
- atomic/std::atomic_load_explicit
- atomic/std::atomic_signal_fence
- atomic/std::atomic_store
- atomic/std::atomic_store_explicit
- atomic/std::atomic_thread_fence
- atomic/std::kill_dependency
ms.assetid: 5c53b4f8-6ff5-47d7-beb2-2d6ee3c6ea89
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
helpviewer_keywords:
- std::atomic_compare_exchange_strong [C++]
- std::atomic_compare_exchange_strong_explicit [C++]
- std::atomic_compare_exchange_weak [C++]
- std::atomic_compare_exchange_weak_explicit [C++]
- std::atomic_exchange [C++]
- std::atomic_exchange_explicit [C++]
- std::atomic_fetch_add [C++]
- std::atomic_fetch_add_explicit [C++]
- std::atomic_fetch_and [C++]
- std::atomic_fetch_and_explicit [C++]
- std::atomic_fetch_or [C++]
- std::atomic_fetch_or_explicit [C++]
- std::atomic_fetch_sub [C++]
- std::atomic_fetch_sub_explicit [C++]
- std::atomic_fetch_xor [C++]
- std::atomic_fetch_xor_explicit [C++]
- std::atomic_flag_clear [C++]
- std::atomic_flag_clear_explicit [C++]
- std::atomic_flag_test_and_set [C++]
- std::atomic_flag_test_and_set_explicit [C++]
- std::atomic_init [C++]
- std::atomic_is_lock_free [C++]
- std::atomic_load [C++]
- std::atomic_load_explicit [C++]
- std::atomic_signal_fence [C++]
- std::atomic_store [C++]
- std::atomic_store_explicit [C++]
- std::atomic_thread_fence [C++]
- std::kill_dependency [C++]
ms.openlocfilehash: 75dff27cd050ae1a218cb8d61abaffff05d38661
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltatomicgt-functions"></a>&lt;Atomic&gt; funkce
||||  
|-|-|-|  
|[atomic_compare_exchange_strong –](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit –](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak –](#atomic_compare_exchange_weak)|  
|[atomic_compare_exchange_weak_explicit –](#atomic_compare_exchange_weak_explicit)|[atomic_exchange –](#atomic_exchange)|[atomic_exchange_explicit –](#atomic_exchange_explicit)|  
|[atomic_fetch_add –](#atomic_fetch_add)|[atomic_fetch_add_explicit –](#atomic_fetch_add_explicit)|[atomic_fetch_and –](#atomic_fetch_and)|  
|[atomic_fetch_and_explicit –](#atomic_fetch_and_explicit)|[atomic_fetch_or –](#atomic_fetch_or)|[atomic_fetch_or_explicit –](#atomic_fetch_or_explicit)|  
|[atomic_fetch_sub –](#atomic_fetch_sub)|[atomic_fetch_sub_explicit –](#atomic_fetch_sub_explicit)|[atomic_fetch_xor –](#atomic_fetch_xor)|  
|[atomic_fetch_xor_explicit –](#atomic_fetch_xor_explicit)|[atomic_flag_clear –](#atomic_flag_clear)|[atomic_flag_clear_explicit –](#atomic_flag_clear_explicit)|  
|[atomic_flag_test_and_set –](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit –](#atomic_flag_test_and_set_explicit)|[atomic_init –](#atomic_init)|  
|[atomic_is_lock_free –](#atomic_is_lock_free)|[atomic_load –](#atomic_load)|[atomic_load_explicit –](#atomic_load_explicit)|  
|[atomic_signal_fence –](#atomic_signal_fence)|[atomic_store –](#atomic_store)|[atomic_store_explicit –](#atomic_store_explicit)|  
|[atomic_thread_fence –](#atomic_thread_fence)|[kill_dependency –](#kill_dependency)|  
  
##  <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong –  
 Provede atomická operace porovnání a serveru exchange.  
  
```
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `Ty`.  
  
 `Exp`  
 Ukazatel na hodnotu typu `Ty`.  
  
 `Value`  
 Hodnotu typu `Ty`.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `bool` určující výsledek porovnání hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda provádí atomická operace porovnání a exchange pomocí implicitní `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) argumenty. Další informace najdete v tématu [atomic_compare_exchange_strong_explicit –](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).  
  
##  <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit –  
 Provede *atomic porovnání a exchange* operaci.  
  
```
template <class T>
inline bool atomic_compare_exchange_strong_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `Ty`.  
  
 `Exp`  
 Ukazatel na hodnotu typu `Ty`.  
  
 `Value`  
 Hodnotu typu `Ty`.  
  
 `Order1`  
 První [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) argument.  
  
 `Order2`  
 Druhý `memory_order` argument. Hodnota `Order2` nemůže být `memory_order_release` nebo `memory_order_acq_rel`, nemůže být vyšší než hodnota `Order1`.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `bool` určující výsledek porovnání hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 *Atomické operace porovnání a exchange* porovnává hodnotu, která je uložená v objektu, která ukazuje `Atom` s hodnotou, která ukazuje `Exp`. Pokud jsou hodnoty stejné, hodnotou, která je uložená v objektu, která ukazuje `atom` se nahradí `Val` pomocí `read-modify-write` operace a použití paměti pořadí omezení, které jsou určené `Order1`. Pokud tyto hodnoty nebudou stejné, operace nahradí hodnotu, která ukazuje `Exp` s hodnotou, která je uložená v objektu, která ukazuje `Atom` a platí omezení paměti pořadí, které jsou určené `Order2`.  
  
##  <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak –  
 Provede *weak atomic porovnat a exchange* operaci.  
  
```
template <class Ty>
inline bool atomic_compare_exchange_strong(
    volatile atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_strong(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `Ty`.  
  
 `Exp`  
 Ukazatel na hodnotu typu `Ty`.  
  
 `Value`  
 Hodnotu typu `Ty`.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `bool` určující výsledek porovnání hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda provádí *weak atomic porovnat a exchange operaci* má implicitní `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) argumenty. Další informace najdete v tématu [atomic_compare_exchange_weak_explicit –](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).  
  
##  <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit –  
 Provede *weak atomic porovnat a exchange* operaci.  
  
```
template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    volatile atomic<Ty>* Atom,
    Ty* Exp, 
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;

template <class Ty>
inline bool atomic_compare_exchange_weak_explicit(
    atomic<Ty>* Atom,
    Ty* Exp,
    Ty Value,
    memory_order Order1,
    memory_order Order2) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `Ty`.  
  
 `Exp`  
 Ukazatel na hodnotu typu `Ty`.  
  
 `Value`  
 Hodnotu typu `Ty`.  
  
 `Order1`  
 První [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) argument.  
  
 `Order2`  
 Druhý `memory_order` argument. Hodnota `Order2` nemůže být `memory_order_release` nebo `memory_order_acq_rel`, ani může být vyšší než hodnota `Order1`.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `bool` určující výsledek porovnání hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 *Atomické operace porovnání a exchange* porovnává hodnotu, která je uložená v objektu, která ukazuje `Atom` s hodnotou, která ukazuje `Exp`. Pokud jsou hodnoty stejné, operace nahradí hodnotu, která je uložená v objektu, která ukazuje `Atom` s `Val` pomocí `read-modify-write` operace a použití omezení paměti pořadí, které jsou určené `Order1`. Pokud tyto hodnoty nebudou stejné, operace nahradí hodnotu, která ukazuje `Exp` s hodnotou, která je uložená v objektu, která ukazuje `Atom` a platí omezení paměti pořadí, které jsou určené `Order2`.  
  
 A *slabé* atomické operace porovnání a exchange provede exchange, pokud jsou porovnávané hodnoty rovny. Ale pokud tyto hodnoty nebudou stejné, není zaručena operaci provést exchange.  
  
##  <a name="atomic_exchange"></a>atomic_exchange –  
 Používá `Value` nahradit uložené hodnotu `Atom`.  
  
```
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `Ty`.  
  
 `Value`  
 Hodnotu typu `Ty`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Uložené hodnoty z `Atom` před exchange.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_exchange` Provádí funkce `read-modify-write` operaci Exchange hodnotou, která je uložená v `Atom` s `Value`pomocí `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit –  
 Nahradí hodnotu uložené `Atom` s `Value`.  
  
```
template <class Ty>
inline Ty atomic_exchange_explicit(
    volatile atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_exchange_explicit(
    atomic<Ty>* Atom,
    Ty Value,
    memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `Ty`.  
  
 `Value`  
 Hodnotu typu `Ty`.  
  
 `Order`  
 A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Návratová hodnota  
 Uložené hodnoty z `Atom` před exchange.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_exchange_explicit` Provádí funkce `read-modify-write` operaci Exchange hodnotou, která je uložená v `Atom` s `Value`, v rámci omezení paměti, které jsou určené `Order`.  
  
##  <a name="atomic_fetch_add"></a>atomic_fetch_add –  
 Přidá hodnotu do stávající hodnotu, která je uložená v `atomic` objektu.  
  
```
template <class T>  
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>  
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který ukládá ukazatel na typ `T`.  
  
 `Value`  
 Hodnotu typu `ptrdiff_t`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota ukazatele obsažených v atomic objektu bezprostředně před operace byla provedena.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_fetch_add` Provádí funkce `read-modify-write` operace atomicky přidání `Value` k hodnotě uložené v `Atom`pomocí `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení.  
  
 Pokud je typ atomic `atomic_address`, `Value` má typ `ptrdiff_t` a operace jsou považovány za uložené ukazatele `char *`.  
  
 Tato operace je přetížena také pro integrální typy:  
  
```
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```  
  
##  <a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit –  
 Přidá hodnotu do stávající hodnotu, která je uložená v `atomic` objektu.  
  
```
template <class T>  
T* atomic_fetch_add_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>  
T* atomic_fetch_add_explicit(
    atomic<T*>* Atom, 
    ptrdiff_t Value, 
    memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který ukládá ukazatel na typ `T`.  
  
 `Value`  
 Hodnotu typu `ptrdiff_t`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota ukazatele obsažených v atomic objektu bezprostředně před operace byla provedena.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_fetch_add_explicit` Provádí funkce `read-modify-write` operace atomicky přidání `Value` k hodnotě uložené v `Atom`, uvnitř [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení, které jsou určené `Order`.  
  
 Pokud je typ atomic `atomic_address`, `Value` má typ `ptrdiff_t` a operace jsou považovány za uložené ukazatele `char *`.  
  
 Tato operace je přetížena také pro integrální typy:  
  
```cpp  
integral atomic_fetch_add_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_add_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```  
  
##  <a name="atomic_fetch_and"></a>atomic_fetch_and –  
 Provede bitové `and` na hodnotu a stávající hodnotu, která je uložená v `atomic` objektu.  
  
```
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept; 
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept; 
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `T`.  
  
 `Value`  
 Hodnotu typu `T`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota obsažených v atomic objektu bezprostředně před operace byla provedena.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_fetch_and` Provádí funkce `read-modify-write` operace nahraďte uložené hodnotu `Atom` s bitové `and` z `Value` a aktuální hodnotu, která je uložená v `Atom`pomocí `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení.  
  
##  <a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit –  
 Provede bitové `and` hodnotu a stávající hodnotu, která je uložená v `atomic` objektu.  
  
```
template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom, 
    T Value,
    memory_order Order) noexcept;
    
template <class T>
inline T atomic_fetch_and_explicit(
    volatile atomic<T>* Atom, 
    T Value,
    memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `T`.  
  
 `Value`  
 Hodnotu typu `T`.  
  
 `Order`  
 A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota obsažených v atomic objektu bezprostředně před operace byla provedena.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_fetch_and_explicit` Provádí funkce `read-modify-write` operace nahraďte uložené hodnotu `Atom` s bitové `and` z `Value` a aktuální hodnotu, která je uložená v `Atom`, v rámci omezení paměti, které jsou specifikace `Order`.  
  
##  <a name="atomic_fetch_or"></a>atomic_fetch_or –  
 Provede bitové `or` na hodnotu a stávající hodnotu, která je uložená v `atomic` objektu.  
  
```
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `T`.  
  
 `Value`  
 Hodnotu typu `T`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota obsažených v atomic objektu bezprostředně před operace byla provedena.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_fetch_or` Provádí funkce `read-modify-write` operace nahraďte uložené hodnotu `Atom` s bitové `or` z `Value` a aktuální hodnotu, která je uložená v `Atom`pomocí `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit –  
 Provede bitové `or` na hodnotu a stávající hodnotu, která je uložená v `atomic` objektu.  
  
```
template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept; 
    
template <class T>
inline T atomic_fetch_or_explicit(
    volatile atomic<T>* Atom,
    T Value,
    memory_order Order) noexcept; 
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `T`.  
  
 `Value`  
 Hodnotu typu `T`.  
  
 `Order`  
 A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota obsažených v atomic objektu bezprostředně před operace byla provedena.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_fetch_or_explicit` Provádí funkce `read-modify-write` operace nahraďte uložené hodnotu `Atom` s bitové `or` z `Value` a aktuální hodnotu, která je uložená v `Atom`, uvnitř [memory_ pořadí](../standard-library/atomic-enums.md#memory_order_enum) omezení určeného `Order`.  
  
##  <a name="atomic_fetch_sub"></a>atomic_fetch_sub –  
 Odečte hodnotu od stávající hodnotu, která je uložená v `atomic` objektu.  
  
```
template <class T>  
T* atomic_fetch_sub(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;

template <class T>  
T* atomic_fetch_sub(
    atomic<T*>* Atom,
    ptrdiff_t Value) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který ukládá ukazatel na typ `T`.  
  
 `Value`  
 Hodnotu typu `ptrdiff_t`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota ukazatele obsažených v atomic objektu bezprostředně před operace byla provedena.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_fetch_sub` Provádí funkce `read-modify-write` operace atomicky odečtena `Value` z uložené hodnoty v `Atom`pomocí `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení.  
  
 Pokud je typ atomic `atomic_address`, `Value` má typ `ptrdiff_t` a operace jsou považovány za uložené ukazatele `char *`.  
  
 Tato operace je přetížena také pro integrální typy:  
  
```
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```  
  
##  <a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit –  
 Odečte hodnotu od stávající hodnotu, která je uložená v `atomic` objektu.  
  
```
template <class T>  
T* atomic_fetch_sub_explicit(
    volatile atomic<T*>* Atom,
    ptrdiff_t Value,
    memory_order Order) noexcept;

template <class T>  
T* atomic_fetch_sub_explicit(
    atomic<T*>* Atom,
    ptrdiff_t Value, memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který ukládá ukazatel na typ `T`.  
  
 `Value`  
 Hodnotu typu `ptrdiff_t`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota ukazatele obsažených v atomic objektu bezprostředně před operace byla provedena.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_fetch_sub_explicit` Provádí funkce `read-modify-write` operace atomicky odečtena `Value` z uložené hodnoty v `Atom`, uvnitř [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení, které jsou určené `Order`.  
  
 Pokud je typ atomic `atomic_address`, `Value` má typ `ptrdiff_t` a operace jsou považovány za uložené ukazatele `char *`.  
  
 Tato operace je přetížena také pro integrální typy:  
  
```cpp  
integral atomic_fetch_sub_explicit(
    volatile atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;

integral atomic_fetch_sub_explicit(
    atomic-integral* Atom,
    integral Value,
    memory_order Order) noexcept;
```  
  
##  <a name="atomic_fetch_xor"></a>atomic_fetch_xor –  
 Provede bitové `exclusive or` na hodnotu a stávající hodnotu, která je uložená v `atomic` objektu.  
  
```
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept; 

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `T`.  
  
 `Value`  
 Hodnotu typu `T`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota obsažených v atomic objektu bezprostředně před operace byla provedena.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_fetch_xor` Provádí funkce `read-modify-write` operace nahraďte uložené hodnotu `Atom` s bitové `exclusive or` z `Value` a aktuální hodnotu, která je uložená v `Atom`pomocí `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit –  
 Provede bitové `exclusive or` na hodnotu a stávající hodnotu, která je uložená v `atomic` objektu.  
  
```
template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom, 
    T Value,
    memory_order Order) noexcept; 
    
template <class T>
inline T atomic_fetch_xor_explicit(
    volatile atomic<T>* Atom, 
    T Value,
    memory_order Order) noexcept; 
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `T`.  
  
 `Value`  
 Hodnotu typu `T`.  
  
 `Order`  
 A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota obsažených v atomic objektu bezprostředně před operace byla provedena.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_fetch_xor_explicit` Provádí funkce `read-modify-write` operace nahraďte uložené hodnotu `Atom` s bitové `exclusive or` z `Value` a aktuální hodnotu, která je uložená v `Atom`, uvnitř [memory_ pořadí](../standard-library/atomic-enums.md#memory_order_enum) omezení, které jsou určené `Order`.  
  
##  <a name="atomic_flag_clear"></a>atomic_flag_clear –  
 Nastaví `bool` příznak v [atomic_flag –](../standard-library/atomic-flag-structure.md) do objektu `false`, uvnitř `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
```
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Flag`  
 Ukazatel na `atomic_flag` objektu.  
  
##  <a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit –  
 Nastaví `bool` příznak v [atomic_flag –](../standard-library/atomic-flag-structure.md) do objektu `false`, v rámci zadaného [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení.  
  
```
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Flag`  
 Ukazatel na `atomic_flag` objektu.  
  
 `Order`  
 A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set –  
 Nastaví `bool` příznak v [atomic_flag –](../standard-library/atomic-flag-structure.md) do objektu `true`, v rámci omezení `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
```
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Flag`  
 Ukazatel na `atomic_flag` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počáteční hodnota `Flag`.  
  
##  <a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit –  
 Nastaví `bool` příznak v [atomic_flag –](../standard-library/atomic-flag-structure.md) do objektu `true`, v rámci zadaného [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení.  
  
```
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Flag`  
 Ukazatel na `atomic_flag` objektu.  
  
 `Order`  
 A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
### <a name="return-value"></a>Návratová hodnota  
 Počáteční hodnota `Flag`.  
  
##  <a name="atomic_init"></a>atomic_init –  
 Nastaví hodnotu uloženou v `atomic` objektu.  
  
```
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `Ty`.  
  
 `Value`  
 Hodnotu typu `Ty`.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_init`není atomické operace. Není bezpečné pro přístup z více vláken.  
  
##  <a name="atomic_is_lock_free"></a>atomic_is_lock_free –  
 Určuje, zda atomické operací na `atomic` objekty *uvolnění zámku*.  
  
```
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který uchovává hodnotu typu `T`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud atomické operací na `Atom` jsou bez uzamčení, jinak hodnota `false`.  
  
### <a name="remarks"></a>Poznámky  
 Atomic typ zámku bez Pokud žádné atomické operací na daný typ používat zámky. Pokud funkce vrátí hodnotu true, typ je bezpečné pro použití v signál-obslužné rutiny.  
  
##  <a name="atomic_load"></a>atomic_load –  
 Načte hodnotu uloženou v `atomic` objektu.  
  
```
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který obsahuje hodnotu typu `Ty`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Načtené hodnoty, které jsou uloženy v `Atom`.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_load`implicitně používá `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
##  <a name="atomic_load_explicit"></a>atomic_load_explicit –  
 Načte hodnotu uloženou v `atomic` objekt, v rámci zadané [memory_order –](../standard-library/atomic-enums.md#memory_order_enum).  
  
```
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který obsahuje hodnotu typu `Ty`.  
  
 `Order`  
 A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum). Nepoužívejte `memory_order_release` nebo `memory_order_acq_rel`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Načtené hodnoty, které jsou uloženy v `Atom`.  
  
##  <a name="atomic_signal_fence"></a>atomic_signal_fence –  
 Funguje jako *ochranná*– tedy paměti synchronizaci primitivní který vynucuje řazení mezi operacemi zatížení nebo úložiště – mezi ostatní ochranné volající vlákno, které mají signál obslužné rutiny, které jsou spouštěny ve stejném vlákně.  
  
```
inline void atomic_signal_fence(memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Order`  
 Paměť, omezení, která určuje typ ochranná řazení.  
  
### <a name="remarks"></a>Poznámky  
 `Order` Argument určuje typ ohraničení.  
  
|||  
|-|-|  
|`memory_order_relaxed`|Ochranná nemá žádný vliv.|  
|`memory_order_consume`|Ochranná představuje ochranná získání.|  
|`memory_order_acquire`|Ochranná představuje ochranná získání.|  
|`memory_order_release`|Ochranná představuje ochranná verze.|  
|`memory_order_acq_rel`|Ochranná představuje získání ochranná a ochranná verze.|  
|`memory_order_seq_cst`|Ohraničení je získání ochranná i ochranná verze a postupně konzistentní.|  
  
##  <a name="atomic_store"></a>atomic_store –  
 Atomicky ukládá hodnotu v atomic objektu.  
  
```
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na atomic objekt, který obsahuje hodnotu typu `Ty`.  
  
 `Value`  
 Hodnotu typu `Ty`.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_store`ukládá `Value` v objektu, která ukazuje `Atom`, uvnitř `memory_order_seq_cst` [memory_order –](../standard-library/atomic-enums.md#memory_order_enum) omezení.  
  
##  <a name="atomic_store_explicit"></a>atomic_store_explicit –  
 Atomicky ukládá hodnotu v atomic objektu.  
  
```
template <class Ty>
inline Ty atomic_store_explicit(
    const volatile atomic<Ty>* Atom, 
    Ty Value, 
    memory_order Order) noexcept;

template <class Ty>
inline Ty atomic_store_explicit(
    const atomic<Ty>* Atom, 
    T Value, 
    memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Atom`  
 Ukazatel na `atomic` objekt, který obsahuje hodnotu typu `Ty`.  
  
 `Value`  
 Hodnotu typu `Ty`.  
  
 `Order`  
 A [memory_order –](../standard-library/atomic-enums.md#memory_order_enum). Nepoužívejte `memory_order_consume`, `memory_order_acquire`, nebo `memory_order_acq_rel`.  
  
### <a name="remarks"></a>Poznámky  
 `atomic_store`ukládá `Value` v objektu, která ukazuje `Atom`, uvnitř `memory_order` , který je určen podle `Order`.  
  
##  <a name="atomic_thread_fence"></a>atomic_thread_fence –  
 Funguje jako *ochranná*– tedy paměti synchronizaci primitivní který vynucuje řazení mezi operacemi zatížení nebo úložiště – bez přidružených atomické operace.  
  
```
inline void atomic_thread_fence(memory_order Order) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Order`  
 Paměť, omezení, která určuje typ ochranná řazení.  
  
### <a name="remarks"></a>Poznámky  
 `Order` Argument určuje typ ohraničení.  
  
|||  
|-|-|  
|`memory_order_relaxed`|Ochranná nemá žádný vliv.|  
|`memory_order_consume`|Ochranná představuje ochranná získání.|  
|`memory_order_acquire`|Ochranná představuje ochranná získání.|  
|`memory_order_release`|Ochranná představuje ochranná verze.|  
|`memory_order_acq_rel`|Ochranná představuje získání ochranná a ochranná verze.|  
|`memory_order_seq_cst`|Ohraničení je získání ochranná i ochranná verze a postupně konzistentní.|  
  
##  <a name="kill_dependency"></a>kill_dependency –  
 Odebere závislost.  
  
```
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```  
  
### <a name="parameters"></a>Parametry  
 `Arg`  
 Hodnotu typu `Ty`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je `Arg`. Vyhodnocení `Arg` neobsahuje závislost volání funkce. Porušením řetězec možných závislostí může povolit funkce kompilátoru pro generování kódu efektivnější.  
  
## <a name="see-also"></a>Viz také  
 [\<Atomic >](../standard-library/atomic.md)



