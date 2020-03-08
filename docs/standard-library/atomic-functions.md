---
title: '&lt;atomické&gt; funkce'
ms.date: 07/11/2018
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
ms.openlocfilehash: 5314db43bed913e801846341309513c239216887
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78867077"
---
# <a name="ltatomicgt-functions"></a>&lt;atomické&gt; funkce

||||
|-|-|-|
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak)|
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit)|[atomic_exchange](#atomic_exchange)|[atomic_exchange_explicit](#atomic_exchange_explicit)|
|[atomic_fetch_add](#atomic_fetch_add)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit)|[atomic_fetch_and](#atomic_fetch_and)|
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit)|[atomic_fetch_or](#atomic_fetch_or)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit)|
|[atomic_fetch_sub](#atomic_fetch_sub)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit)|[atomic_fetch_xor](#atomic_fetch_xor)|
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit)|[atomic_flag_clear](#atomic_flag_clear)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit)|
|[atomic_flag_test_and_set](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit)|[atomic_init](#atomic_init)|
|[atomic_is_lock_free](#atomic_is_lock_free)|[atomic_load](#atomic_load)|[atomic_load_explicit](#atomic_load_explicit)|
|[atomic_signal_fence](#atomic_signal_fence)|[atomic_store](#atomic_store)|[atomic_store_explicit](#atomic_store_explicit)|
|[atomic_thread_fence](#atomic_thread_fence)|[kill_dependency](#kill_dependency)|

## <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

Provádí operaci atomické porovnání a výměny.

```cpp
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

\ *Atom*
Ukazatel na *atomický* objekt, který ukládá hodnotu typu `Ty`.

\ *exp*
Ukazatel na hodnotu typu `Ty`.

*Hodnota*\
Hodnota typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Tato metoda provádí operaci atomické porovnání a výměny pomocí implicitních `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumentů. Další informace najdete v tématu [atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

Provádí operaci *atomické porovnání a výměny* .

```cpp
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

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `Ty`.

\ *exp*
Ukazatel na hodnotu typu `Ty`.

*Hodnota*\
Hodnota typu `Ty`.

*Order1*\
První [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argument.

*Order2*\
Druhý argument `memory_order`. Hodnota *Order2* nemůže být `memory_order_release` ani `memory_order_acq_rel`, nemůže být silnější než hodnota *Order1*.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

*Atomická operace porovnání a výměny* porovnává hodnotu uloženou v objektu, na který odkazuje *Atom* na hodnotu, na kterou ukazuje *exp*. Pokud jsou hodnoty stejné, hodnota, která je uložena v objektu, na který ukazuje *Atom* , je nahrazena *hodnotou* pomocí operace `read-modify-write` a uplatněním omezení pořadí paměti, která jsou určena parametrem *Order1*. Pokud hodnoty nejsou stejné, operace nahradí hodnotu, na kterou ukazuje *exp* , hodnotou uloženou v objektu, na který ukazuje *Atom* , a použije omezení pořadí paměti, která jsou určena hodnotou *Order2*.

## <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

Provede *slabě atomická operace porovnání a výměny* .

```cpp
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

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `Ty`.

\ *exp*
Ukazatel na hodnotu typu `Ty`.

*Hodnota*\
Hodnota typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Tato metoda provádí *slabě atomická operace porovnání a výměny* , která má implicitní argumenty `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) . Další informace najdete v tématu [atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

Provede *slabě atomická operace porovnání a výměny* .

```cpp
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

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `Ty`.

\ *exp*
Ukazatel na hodnotu typu `Ty`.

*Hodnota*\
Hodnota typu `Ty`.

*Order1*\
První [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argument.

*Order2*\
Druhý argument `memory_order`. Hodnota *Order2* nemůže být `memory_order_release` ani `memory_order_acq_rel`, ani nemůže být silnější než hodnota *Order1*.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Silné a slabé charakter *atomické porovnání a operace Exchange* zaručují, že neukládají novou hodnotu, pokud se očekávané a aktuální hodnoty neshodují. Silný charakter zaručuje, že bude ukládat novou hodnotu, pokud se očekávané a aktuální hodnoty rovnají. Slabý charakter může někdy vracet **hodnotu false** a neuloží novou hodnotu, i když jsou aktuální a očekávané hodnoty stejné. Jinými slovy, funkce vrátí **hodnotu false**, ale pozdější vyhodnocení očekávané hodnoty může odhalit, že se nezmění, a proto by měla být porovnána jako shodná.

## <a name="atomic_exchange"></a>atomic_exchange

Používá *hodnotu* k nahrazení uložené hodnoty *Atom*.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `Ty`.

*Hodnota*\
Hodnota typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

Uložená hodnota *Atom* před výměnou.

### <a name="remarks"></a>Poznámky

Funkce `atomic_exchange` provádí operaci `read-modify-write` k výměně hodnoty, která je uložena v *Atom* s *hodnotou*pomocí [memory_order](../standard-library/atomic-enums.md#memory_order_enum)`memory_order_seq_cst`.

## <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

Nahradí uloženou hodnotu *Atom* *hodnotou*.

```cpp
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

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `Ty`.

*Hodnota*\
Hodnota typu `Ty`.

\ *objednávky*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Uložená hodnota *Atom* před výměnou.

### <a name="remarks"></a>Poznámky

Funkce `atomic_exchange_explicit` provádí operaci `read-modify-write` k výměně hodnoty, která je uložena v *Atom* s *hodnotou*v rámci omezení paměti, která jsou určena podle *pořadí*.

## <a name="atomic_fetch_add"></a>atomic_fetch_add

Přidá hodnotu do existující hodnoty, která je uložena v objektu `atomic`.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá ukazatel na typ `T`.

*Hodnota*\
Hodnota typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsažená v atomovém objektu bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_add` provádí operaci `read-modify-write` k atomické přidání *hodnoty* do uložené hodnoty v *atomu*pomocí omezení `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

Pokud je typ Atomic `atomic_address`, *hodnota* je typu `ptrdiff_t` a operace zpracovává uložený ukazatel jako `char *`.

Tato operace je také přetížena pro celočíselné typy:

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit

Přidá hodnotu do existující hodnoty, která je uložena v objektu `atomic`.

```cpp
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

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá ukazatel na typ `T`.

*Hodnota*\
Hodnota typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsažená v atomovém objektu bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_add_explicit` provádí operaci `read-modify-write` k atomické přidání *hodnoty* do uložené hodnoty v *atomu*v rámci omezení [memory_order](../standard-library/atomic-enums.md#memory_order_enum) , která jsou určena `Order`.

Pokud je typ Atomic `atomic_address`, `Value` je typu `ptrdiff_t` a operace zpracovává uložený ukazatel jako `char *`.

Tato operace je také přetížena pro celočíselné typy:

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

## <a name="atomic_fetch_and"></a>atomic_fetch_and

Provede bitovou `and` na hodnotu a existující hodnotu, která je uložena v objektu `atomic`.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `T`.

*Hodnota*\
Hodnota typu `T`.

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomovém objektu bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_and` provádí operaci `read-modify-write`, která nahradí uloženou hodnotu *Atom* s bitovým `and` *hodnotou* a aktuální hodnotou uloženou v *atomě*pomocí omezení `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

## <a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit

Provede bitovou `and` hodnoty a existující hodnotu, která je uložena v objektu `atomic`.

```cpp
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

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `T`.

*Hodnota*\
Hodnota typu `T`.

\ *objednávky*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomovém objektu bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_and_explicit` provádí operaci `read-modify-write`, která nahradí uloženou hodnotu *Atom* s bitovým `and` *hodnotou* a aktuální hodnotou uloženou v *atomě*v rámci omezení paměti, která jsou určena podle *pořadí*.

## <a name="atomic_fetch_or"></a>atomic_fetch_or

Provede bitovou `or` na hodnotu a existující hodnotu, která je uložena v objektu `atomic`.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `T`.

*Hodnota*\
Hodnota typu `T`.

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomovém objektu bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_or` provádí operaci `read-modify-write`, která nahradí uloženou hodnotu *Atom* pomocí bitového `or` *hodnoty* a aktuální hodnotou, která je uložena v *atomu*, pomocí [memory_order](../standard-library/atomic-enums.md#memory_order_enum)`memory_order_seq_cst`.

## <a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit

Provede bitovou `or` na hodnotu a existující hodnotu, která je uložena v objektu `atomic`.

```cpp
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

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `T`.

*Hodnota*\
Hodnota typu `T`.

\ *objednávky*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomovém objektu bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_or_explicit` provádí operaci `read-modify-write`, která nahradí uloženou hodnotu *Atom* s bitovým `or` *hodnotou* a aktuální hodnotou uloženou ve *atomě*v rámci [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení určených *pořadím*.

## <a name="atomic_fetch_sub"></a>atomic_fetch_sub

Odečte hodnotu od existující hodnoty, která je uložena v objektu `atomic`.

```cpp
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

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá ukazatel na typ `T`.

*Hodnota*\
Hodnota typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsažená v atomovém objektu bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_sub` provádí `read-modify-write` operace pro atomické odečtení *hodnoty* z uložené hodnoty v *atomě*pomocí omezení `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

Pokud je typ Atomic `atomic_address`, *hodnota* je typu `ptrdiff_t` a operace zpracovává uložený ukazatel jako `char *`.

Tato operace je také přetížena pro celočíselné typy:

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit

Odečte hodnotu od existující hodnoty, která je uložena v objektu `atomic`.

```cpp
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

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá ukazatel na typ `T`.

*Hodnota*\
Hodnota typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsažená v atomovém objektu bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_sub_explicit` provádí `read-modify-write` operace pro atomovou odchylku *hodnoty* z uložené hodnoty ve *atomě*v rámci omezení [memory_order](../standard-library/atomic-enums.md#memory_order_enum) , která jsou určena `Order`.

Pokud je typ Atomic `atomic_address`, *hodnota* je typu `ptrdiff_t` a operace zpracovává uložený ukazatel jako `char *`.

Tato operace je také přetížena pro celočíselné typy:

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

## <a name="atomic_fetch_xor"></a>atomic_fetch_xor

Provede bitovou `exclusive or` na hodnotu a existující hodnotu, která je uložena v objektu `atomic`.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `T`.

*Hodnota*\
Hodnota typu `T`.

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomovém objektu bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_xor` provádí operaci `read-modify-write`, která nahradí uloženou hodnotu *Atom* pomocí bitového `exclusive or` *hodnoty* a aktuální hodnotou, která je uložena v *atomu*, pomocí [memory_order](../standard-library/atomic-enums.md#memory_order_enum)`memory_order_seq_cst`.

## <a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit

Provede bitovou `exclusive or` na hodnotu a existující hodnotu, která je uložena v objektu `atomic`.

```cpp
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

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `T`.

*Hodnota*\
Hodnota typu `T`.

\ *objednávky*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomovém objektu bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_xor_explicit` provádí operaci `read-modify-write`, která nahradí uloženou hodnotu *Atom* s bitovým `exclusive or` *hodnotou* a aktuální hodnotou uloženou ve *atomě*v rámci [Memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení, která jsou určena podle *pořadí*.

## <a name="atomic_flag_clear"></a>atomic_flag_clear

Nastaví příznak **bool** v objektu [atomic_flag](../standard-library/atomic-flag-structure.md) na **hodnotu false**v rámci `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parametry

*Příznak*\
Ukazatel na objekt `atomic_flag`.

## <a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

Nastaví příznak **bool** v objektu [atomic_flag](../standard-library/atomic-flag-structure.md) na **hodnotu false**v rámci zadaného omezení [memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Příznak*\
Ukazatel na objekt `atomic_flag`.

\ *objednávky*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

Nastaví u objektu [atomic_flag](../standard-library/atomic-flag-structure.md) příznak **bool** na **hodnotu true**, a to v rámci omezení `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parametry

*Příznak*\
Ukazatel na objekt `atomic_flag`.

### <a name="return-value"></a>Návratová hodnota

Počáteční hodnota *příznaku*

## <a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

Nastaví příznak **bool** v objektu [atomic_flag](../standard-library/atomic-flag-structure.md) na **hodnotu true**v rámci zadaného omezení [memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Příznak*\
Ukazatel na objekt `atomic_flag`.

\ *objednávky*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Počáteční hodnota *příznaku*

## <a name="atomic_init"></a>atomic_init

Nastaví uloženou hodnotu v objektu `atomic`.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `Ty`.

*Hodnota*\
Hodnota typu `Ty`.

### <a name="remarks"></a>Poznámky

`atomic_init` není atomická operace. Není bezpečná pro přístup z více vláken.

## <a name="atomic_is_lock_free"></a>atomic_is_lock_free

Určuje, zda jsou atomické operace s objektem `atomic` *bez zámku*.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Ukazatel na objekt `atomic`, který ukládá hodnotu typu `T`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou atomické operace na *Atom* bez zámků; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Atomický typ je bez zámku, pokud žádné atomické operace na tomto typu nepoužívají zámky. Pokud tato funkce vrátí hodnotu true, je možné v obslužných rutinách signálu bezpečně použít typ.

## <a name="atomic_load"></a>atomic_load

Načte uloženou hodnotu v objektu `atomic`.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Ukazatel na objekt `atomic`, který obsahuje hodnotu typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

Načtená hodnota, která je uložena v *atomu*.

### <a name="remarks"></a>Poznámky

`atomic_load` implicitně používá [memory_order](../standard-library/atomic-enums.md#memory_order_enum)`memory_order_seq_cst`.

## <a name="atomic_load_explicit"></a>atomic_load_explicit

Načte uloženou hodnotu v objektu `atomic` v rámci zadaného [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Ukazatel na objekt `atomic`, který obsahuje hodnotu typu `Ty`.

\ *objednávky*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nepoužívejte `memory_order_release` ani `memory_order_acq_rel`.

### <a name="return-value"></a>Návratová hodnota

Načtená hodnota, která je uložena v *atomu*.

## <a name="atomic_signal_fence"></a>atomic_signal_fence

Funguje jako *plot*– což je primitiv synchronizace paměti, která vynutila řazení mezi operacemi načtení/uložení – mezi ostatními ploty ve volajícím vlákně, které mají obslužné rutiny signálu spouštěné ve stejném vlákně.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

\ *objednávky*
Omezení řazení paměti, které určuje typ plotu.

### <a name="remarks"></a>Poznámky

Argument *Order* určuje typ plotu.

|||
|-|-|
|`memory_order_relaxed`|Ochranné ohraničení nemá žádný vliv.|
|`memory_order_consume`|Plot je plot pro získání.|
|`memory_order_acquire`|Plot je plot pro získání.|
|`memory_order_release`|Plot je ochranná doba vydání.|
|`memory_order_acq_rel`|Plot je plot pro získání i ochranou verzí.|
|`memory_order_seq_cst`|Plot je plot pro získání i ochranou verzí a je sekvenční konzistentní.|

## <a name="atomic_store"></a>atomic_store

Atomicky ukládá hodnotu v atomovém objektu.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

\ *Atom*
Ukazatel na atomický objekt, který obsahuje hodnotu typu `Ty`.

*Hodnota*\
Hodnota typu `Ty`.

### <a name="remarks"></a>Poznámky

`atomic_store` ukládá *hodnotu* v objektu, na který ukazuje *Atom*, v rámci omezení `memory_order_seq_cst`[memory_order](../standard-library/atomic-enums.md#memory_order_enum) .

## <a name="atomic_store_explicit"></a>atomic_store_explicit

Atomicky ukládá hodnotu v atomovém objektu.

```cpp
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

\ *Atom*
Ukazatel na objekt `atomic`, který obsahuje hodnotu typu `Ty`.

*Hodnota*\
Hodnota typu `Ty`.

\ *objednávky*
[Memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nepoužívejte `memory_order_consume`, `memory_order_acquire`nebo `memory_order_acq_rel`.

### <a name="remarks"></a>Poznámky

`atomic_store` ukládá *hodnotu* v objektu, na který ukazuje *Atom*, v rámci `memory_order` určeném podle *pořadí*.

## <a name="atomic_thread_fence"></a>atomic_thread_fence

Funguje jako *plot*– což je primitivum synchronizace paměti, které vynutilo řazení mezi operacemi načtení/uložení – bez přidružené atomické operace.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

\ *objednávky*
Omezení řazení paměti, které určuje typ plotu.

### <a name="remarks"></a>Poznámky

Argument *Order* určuje typ plotu.

|||
|-|-|
|`memory_order_relaxed`|Ochranné ohraničení nemá žádný vliv.|
|`memory_order_consume`|Plot je plot pro získání.|
|`memory_order_acquire`|Plot je plot pro získání.|
|`memory_order_release`|Plot je ochranná doba vydání.|
|`memory_order_acq_rel`|Plot je plot pro získání i ochranou verzí.|
|`memory_order_seq_cst`|Plot je plot pro získání i ochranou verzí a je sekvenční konzistentní.|

## <a name="kill_dependency"></a>kill_dependency

Odebere závislost.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Parametry

*Arg* –\
Hodnota typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je *arg*. Vyhodnocení *arg* neprovádí závislost na volání funkce. Přerušením možného řetězu závislostí funkce může kompilátoru dovolit, aby vygeneroval efektivnější kód.

## <a name="see-also"></a>Viz také

[\<atomická >](../standard-library/atomic.md)
