---
title: '&lt;atomové&gt; funkce'
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
ms.openlocfilehash: b6d03da446e4a3bae02f662e5b106bd5de534d0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376889"
---
# <a name="ltatomicgt-functions"></a>&lt;atomové&gt; funkce

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

## <a name="atomic_compare_exchange_strong"></a><a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

Provádí atomické porovnání a výměnu operace.

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

*Atom*\
Ukazatel na *atomický* objekt, který `Ty`ukládá hodnotu typu .

*Exp*\
Ukazatel na hodnotu `Ty`typu .

*Hodnotu*\
Hodnota typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Tato metoda provádí operaci atomic compare `memory_order_seq_cst`a exchange pomocí implicitní [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumenty. Další informace naleznete [v tématu atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a><a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

Provádí *atomické porovnání a výměnu* operace.

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

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `Ty`hodnotu typu .

*Exp*\
Ukazatel na hodnotu `Ty`typu .

*Hodnotu*\
Hodnota typu `Ty`.

*Pořadí1*\
První [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argument.

*Pořadí2*\
Druhý `memory_order` argument. Hodnota *Order2* nemůže `memory_order_release` být `memory_order_acq_rel`nebo , nemůže být silnější než hodnota *Order1*.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Atomic *compare and exchange operation* porovná hodnotu, která je uložena v objektu, na který *atom ukazuje,* s hodnotou, na kterou se vztahuje *exp*. Pokud jsou hodnoty stejné, hodnota, která je uložena v objektu, na který `read-modify-write` je odkazováno *atom,* je nahrazena *hodnotou* pomocí operace a použitím omezení pořadí paměti, které jsou určeny *order1*. Pokud hodnoty nejsou stejné, operace nahradí hodnotu, která je uvedena *Exp* s hodnotou, která je uložena v objektu, který je odkazován *Atom* a použije omezení pořadí paměti, které jsou určeny *Order2*.

## <a name="atomic_compare_exchange_weak"></a><a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

Provádí *slabé atomické porovnání a výměnu* operace.

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

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `Ty`hodnotu typu .

*Exp*\
Ukazatel na hodnotu `Ty`typu .

*Hodnotu*\
Hodnota typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Tato metoda provádí *slabé atomické porovnání a výměnu operace,* která má implicitní `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumenty. Další informace naleznete [v tématu atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a><a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

Provádí *slabé atomické porovnání a výměnu* operace.

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

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `Ty`hodnotu typu .

*Exp*\
Ukazatel na hodnotu `Ty`typu .

*Hodnotu*\
Hodnota typu `Ty`.

*Pořadí1*\
První [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argument.

*Pořadí2*\
Druhý `memory_order` argument. Hodnota *Order2* nemůže `memory_order_release` být `memory_order_acq_rel`nebo , ani nemůže být silnější než hodnota *Order1*.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Silné a slabé varianty *atomové operace porovnání a výměny* zaručují, že neukládají novou hodnotu, pokud očekávané a aktuální hodnoty nejsou stejné. Silná chuť zaručuje, že bude ukládat novou hodnotu, pokud očekávané a aktuální hodnoty jsou stejné. Slabé flavor může někdy vrátit **false** a není uložit novou hodnotu i v případě, že aktuální a očekávané hodnoty jsou stejné. Jinými slovy funkce vrátí **false**, ale pozdější zkoumání očekávané hodnoty může odhalit, že se nezměnila, a proto by měla být porovnána jako stejná.

## <a name="atomic_exchange"></a><a name="atomic_exchange"></a>atomic_exchange

Použije *hodnotu* k nahrazení uložené hodnoty *Atom*.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `Ty`hodnotu typu .

*Hodnotu*\
Hodnota typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

Uložená hodnota *Atom* před výměnou.

### <a name="remarks"></a>Poznámky

Funkce `atomic_exchange` provede `read-modify-write` operaci k výměně hodnoty, která je uložena `memory_order_seq_cst`v *Atomu* s *Hodnotou*, pomocí [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a><a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

Nahradí uloženou hodnotu *Atomu* *hodnotou Hodnotu*.

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

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `Ty`hodnotu typu .

*Hodnotu*\
Hodnota typu `Ty`.

*Objednávky*\
Memory_order [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Uložená hodnota *Atom* před výměnou.

### <a name="remarks"></a>Poznámky

Funkce `atomic_exchange_explicit` provede `read-modify-write` operaci k výměně hodnoty, která je uložena v *Atom* s *Value*, v rámci omezení paměti, které jsou určeny *Order*.

## <a name="atomic_fetch_add"></a><a name="atomic_fetch_add"></a>atomic_fetch_add

Přidá hodnotu k existující hodnotě, `atomic` která je uložena v objektu.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `T`ukazatel na text .

*Hodnotu*\
Hodnota typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsaženého atomovým objektem bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_add` provede `read-modify-write` operaci atomicky přidat *Hodnotu* na uloženou hodnotu v *Atom*, pomocí `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

Pokud je `atomic_address`atomický typ `ptrdiff_t` , *Value* má typ a `char *`operace zachází s uloženým ukazatelem jako .

Tato operace je také přetížena pro integrální typy:

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a><a name="atomic_fetch_add_explicit"></a>atomic_fetch_add_explicit

Přidá hodnotu k existující hodnotě, `atomic` která je uložena v objektu.

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

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `T`ukazatel na text .

*Hodnotu*\
Hodnota typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsaženého atomovým objektem bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_add_explicit` provede `read-modify-write` operaci atomicky přidat *Hodnotu* na uloženou hodnotu v *Atom* `Order`, v rámci [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení, které jsou určeny .

Pokud `atomic_address`je atomický typ , `Value` má typ `ptrdiff_t` a `char *`operace zachází s uloženým ukazatelem jako .

Tato operace je také přetížena pro integrální typy:

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

## <a name="atomic_fetch_and"></a><a name="atomic_fetch_and"></a>atomic_fetch_and

Provádí bitové `and` na hodnotu a existující hodnotu, která je uložena v objektu. `atomic`

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `T`hodnotu typu .

*Hodnotu*\
Hodnota typu `T`.

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená atomickým objektem bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_and` provede `read-modify-write` operaci nahradit uloženou hodnotu *Atom* `and` s bitové *hodnoty* a aktuální hodnota, která `memory_order_seq_cst`je uložena v *Atom*, pomocí [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

## <a name="atomic_fetch_and_explicit"></a><a name="atomic_fetch_and_explicit"></a>atomic_fetch_and_explicit

Provádí bitové `and` hodnoty a existující hodnotu, která `atomic` je uložena v objektu.

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

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `T`hodnotu typu .

*Hodnotu*\
Hodnota typu `T`.

*Objednávky*\
Memory_order [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená atomickým objektem bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_and_explicit` provede `read-modify-write` operaci nahradit uloženou hodnotu *Atom* `and` s bitové *hodnoty* a aktuální hodnota, která je uložena v *Atom*, v rámci omezení paměti, které jsou určeny *Order*.

## <a name="atomic_fetch_or"></a><a name="atomic_fetch_or"></a>atomic_fetch_or

Provádí bitové `or` na hodnotu a existující hodnotu, která je uložena v objektu. `atomic`

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `T`hodnotu typu .

*Hodnotu*\
Hodnota typu `T`.

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená atomickým objektem bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_or` provede `read-modify-write` operaci, která nahradí uloženou hodnotu `or` *Atomu* bitovou hodnotou *Value* a aktuální `memory_order_seq_cst`hodnotou uloženou v *Atomu*pomocí [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_or_explicit"></a><a name="atomic_fetch_or_explicit"></a>atomic_fetch_or_explicit

Provádí bitové `or` na hodnotu a existující hodnotu, která je uložena v objektu. `atomic`

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

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `T`hodnotu typu .

*Hodnotu*\
Hodnota typu `T`.

*Objednávky*\
Memory_order [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená atomickým objektem bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_or_explicit` provede `read-modify-write` operaci, která nahradí uloženou hodnotu `or` *Atomu* bitovou hodnotou *Value* a aktuální hodnotou uloženou v *Atomu*v rámci [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení zadaná *order*.

## <a name="atomic_fetch_sub"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub

Odečte hodnotu od existující hodnoty, která `atomic` je uložena v objektu.

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

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `T`ukazatel na text .

*Hodnotu*\
Hodnota typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsaženého atomovým objektem bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_sub` provede `read-modify-write` operaci atomicky odečíst *Value* od uložené hodnoty v `memory_order_seq_cst` *Atom*, pomocí [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

Pokud je `atomic_address`atomický typ `ptrdiff_t` , *Value* má typ a `char *`operace zachází s uloženým ukazatelem jako .

Tato operace je také přetížena pro integrální typy:

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a><a name="atomic_fetch_sub_explicit"></a>atomic_fetch_sub_explicit

Odečte hodnotu od existující hodnoty, která `atomic` je uložena v objektu.

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

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `T`ukazatel na text .

*Hodnotu*\
Hodnota typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsaženého atomovým objektem bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_sub_explicit` provede `read-modify-write` operaci atomicky odečíst *Hodnotu* od uložené hodnoty v *Atom*, `Order`v rámci [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení, které jsou určeny .

Pokud je `atomic_address`atomický typ `ptrdiff_t` , *Value* má typ a `char *`operace zachází s uloženým ukazatelem jako .

Tato operace je také přetížena pro integrální typy:

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

## <a name="atomic_fetch_xor"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor

Provádí bitové `exclusive or` na hodnotu a existující hodnotu, která je uložena v objektu. `atomic`

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `T`hodnotu typu .

*Hodnotu*\
Hodnota typu `T`.

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená atomickým objektem bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_xor` provede `read-modify-write` operaci, která nahradí uloženou hodnotu `exclusive or` *Atomu* bitovou hodnotou *Value* a aktuální `memory_order_seq_cst`hodnotou uloženou v *Atomu*pomocí [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_xor_explicit"></a><a name="atomic_fetch_xor_explicit"></a>atomic_fetch_xor_explicit

Provádí bitové `exclusive or` na hodnotu a existující hodnotu, která je uložena v objektu. `atomic`

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

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `T`hodnotu typu .

*Hodnotu*\
Hodnota typu `T`.

*Objednávky*\
Memory_order [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená atomickým objektem bezprostředně před provedením operace.

### <a name="remarks"></a>Poznámky

Funkce `atomic_fetch_xor_explicit` provede `read-modify-write` operaci, která nahradí uloženou hodnotu `exclusive or` *Atomu* bitovou hodnotou *Value* a aktuální hodnotou uloženou v *Atomu*v rámci [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení, která jsou určena *order*.

## <a name="atomic_flag_clear"></a><a name="atomic_flag_clear"></a>atomic_flag_clear

Nastaví příznak **bool** v [objektu](../standard-library/atomic-flag-structure.md) atomic_flag `memory_order_seq_cst`na **hodnotu false**v rámci [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parametry

*Vlajky*\
Ukazatel na `atomic_flag` objekt.

## <a name="atomic_flag_clear_explicit"></a><a name="atomic_flag_clear_explicit"></a>atomic_flag_clear_explicit

Nastaví příznak **bool** v [atomic_flag](../standard-library/atomic-flag-structure.md) objektu na **false**, v rámci zadaných [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Vlajky*\
Ukazatel na `atomic_flag` objekt.

*Objednávky*\
Memory_order [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a><a name="atomic_flag_test_and_set"></a>atomic_flag_test_and_set

Nastaví příznak **bool** v [atomic_flag](../standard-library/atomic-flag-structure.md) objektu na **hodnotu true**v rámci omezení `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parametry

*Vlajky*\
Ukazatel na `atomic_flag` objekt.

### <a name="return-value"></a>Návratová hodnota

Počáteční hodnota *Flag*.

## <a name="atomic_flag_test_and_set_explicit"></a><a name="atomic_flag_test_and_set_explicit"></a>atomic_flag_test_and_set_explicit

Nastaví příznak **bool** v [atomic_flag](../standard-library/atomic-flag-structure.md) objektu na **hodnotu true**v rámci zadaných [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Vlajky*\
Ukazatel na `atomic_flag` objekt.

*Objednávky*\
Memory_order [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Počáteční hodnota *Flag*.

## <a name="atomic_init"></a><a name="atomic_init"></a>atomic_init

Nastaví uloženou `atomic` hodnotu v objektu.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `Ty`hodnotu typu .

*Hodnotu*\
Hodnota typu `Ty`.

### <a name="remarks"></a>Poznámky

`atomic_init`není atomovou operací. Není bezpečný pro přístup z více vláken.

## <a name="atomic_is_lock_free"></a><a name="atomic_is_lock_free"></a>atomic_is_lock_free

Určuje, zda jsou `atomic` atomické operace s objektem *bez zámku*.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Ukazatel na `atomic` objekt, který ukládá `T`hodnotu typu .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou atomické operace na *Atomu* bez zámku; jinak **false**.

### <a name="remarks"></a>Poznámky

Atomický typ je bez zámku, pokud žádné atomické operace na tomto typu použít zámky. Pokud tato funkce vrátí hodnotu true, je typ bezpečný pro použití v obslužných rutinách signálu.

## <a name="atomic_load"></a><a name="atomic_load"></a>atomic_load

Načte uloženou hodnotu v objektu. `atomic`

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Ukazatel na `atomic` objekt, který obsahuje `Ty`hodnotu typu .

### <a name="return-value"></a>Návratová hodnota

Načtená hodnota, která je uložena v *Atom*.

### <a name="remarks"></a>Poznámky

`atomic_load`implicitně používá `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_load_explicit"></a><a name="atomic_load_explicit"></a>atomic_load_explicit

Načte uloženou hodnotu v objektu `atomic` v rámci zadané ho [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Ukazatel na `atomic` objekt, který obsahuje `Ty`hodnotu typu .

*Objednávky*\
Memory_order [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nepoužívejte `memory_order_release` ani `memory_order_acq_rel`.

### <a name="return-value"></a>Návratová hodnota

Načtená hodnota, která je uložena v *Atom*.

## <a name="atomic_signal_fence"></a><a name="atomic_signal_fence"></a>atomic_signal_fence

Funguje jako *plot*– což je primitivní synchronizace paměti, která vynucuje řazení mezi operacemi zatížení a ukládání – mezi jinými ploty v volajícím vlákně, které mají obslužné rutiny signálu, které jsou spuštěny ve stejném vlákně.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Objednávky*\
Omezení řazení paměti, které určuje typ plotu.

### <a name="remarks"></a>Poznámky

Argument *Pořadí* určuje typ plotu.

|||
|-|-|
|`memory_order_relaxed`|Plot nemá žádný účinek.|
|`memory_order_consume`|Plot je získat plot.|
|`memory_order_acquire`|Plot je získat plot.|
|`memory_order_release`|Plot je propouštěcí plot.|
|`memory_order_acq_rel`|Plot je jak získat plot a uvolnění plotu.|
|`memory_order_seq_cst`|Plot je jak získat plot a uvolnění plot, a je postupně konzistentní.|

## <a name="atomic_store"></a><a name="atomic_store"></a>atomic_store

Atomicky ukládá hodnotu v atomické objektu.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom*\
Ukazatel na atomový objekt, který `Ty`obsahuje hodnotu typu .

*Hodnotu*\
Hodnota typu `Ty`.

### <a name="remarks"></a>Poznámky

`atomic_store`ukládá *Value* v objektu, na který je `memory_order_seq_cst`odkazováno *Atom*, v rámci omezení [memory_order.](../standard-library/atomic-enums.md#memory_order_enum)

## <a name="atomic_store_explicit"></a><a name="atomic_store_explicit"></a>atomic_store_explicit

Atomicky ukládá hodnotu v atomické objektu.

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

*Atom*\
Ukazatel na `atomic` objekt, který obsahuje `Ty`hodnotu typu .

*Hodnotu*\
Hodnota typu `Ty`.

*Objednávky*\
Memory_order [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nepoužívejte `memory_order_consume`, `memory_order_acquire`, `memory_order_acq_rel`nebo .

### <a name="remarks"></a>Poznámky

`atomic_store`ukládá *Hodnotu* v objektu, na který `memory_order` je odkazováno *atomem*, v rámci objektu, který je určen *příkazem .*

## <a name="atomic_thread_fence"></a><a name="atomic_thread_fence"></a>atomic_thread_fence

Funguje jako *plot*– což je primitivní synchronizace paměti, která vynucuje řazení mezi operacemi zatížení nebo úložiště – bez přidružené atomické operace.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Objednávky*\
Omezení řazení paměti, které určuje typ plotu.

### <a name="remarks"></a>Poznámky

Argument *Pořadí* určuje typ plotu.

|||
|-|-|
|`memory_order_relaxed`|Plot nemá žádný účinek.|
|`memory_order_consume`|Plot je získat plot.|
|`memory_order_acquire`|Plot je získat plot.|
|`memory_order_release`|Plot je propouštěcí plot.|
|`memory_order_acq_rel`|Plot je jak získat plot a uvolnění plotu.|
|`memory_order_seq_cst`|Plot je jak získat plot a uvolnění plot, a je postupně konzistentní.|

## <a name="kill_dependency"></a><a name="kill_dependency"></a>kill_dependency

Odebere závislost.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Parametry

*Arg*\
Hodnota typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je *Arg*. Hodnocení *Arg* nenese závislost na volání funkce. Porušením možného řetězu závislostí funkce může povolit kompilátoru generovat efektivnější kód.

## <a name="see-also"></a>Viz také

[\<atomové>](../standard-library/atomic.md)
