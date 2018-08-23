---
title: '&lt;Atomic&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 07/11/2018
ms.topic: reference
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
author: mikeblome
ms.author: mblome
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
ms.workload:
- cplusplus
ms.openlocfilehash: b70f4df63b5a885403b91c1470c3066c33f5f123
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42465848"
---
# <a name="ltatomicgt-functions"></a>&lt;Atomic&gt; funkce

||||
|-|-|-|
|[atomic_compare_exchange_strong](#atomic_compare_exchange_strong)|[atomic_compare_exchange_strong_explicit](#atomic_compare_exchange_strong_explicit)|[atomic_compare_exchange_weak](#atomic_compare_exchange_weak)|
|[atomic_compare_exchange_weak_explicit](#atomic_compare_exchange_weak_explicit)|[atomic_exchange](#atomic_exchange)|[atomic_exchange_explicit](#atomic_exchange_explicit)|
|[atomic_fetch_add](#atomic_fetch_add)|[atomic_fetch_add_explicit](#atomic_fetch_add_explicit)|[atomic_fetch_and –](#atomic_fetch_and)|
|[atomic_fetch_and_explicit](#atomic_fetch_and_explicit)|[atomic_fetch_or](#atomic_fetch_or)|[atomic_fetch_or_explicit](#atomic_fetch_or_explicit)|
|[atomic_fetch_sub](#atomic_fetch_sub)|[atomic_fetch_sub_explicit](#atomic_fetch_sub_explicit)|[atomic_fetch_xor](#atomic_fetch_xor)|
|[atomic_fetch_xor_explicit](#atomic_fetch_xor_explicit)|[atomic_flag_clear](#atomic_flag_clear)|[atomic_flag_clear_explicit](#atomic_flag_clear_explicit)|
|[atomic_flag_test_and_set](#atomic_flag_test_and_set)|[atomic_flag_test_and_set_explicit](#atomic_flag_test_and_set_explicit)|[atomic_init](#atomic_init)|
|[atomic_is_lock_free](#atomic_is_lock_free)|[atomic_load –](#atomic_load)|[atomic_load_explicit](#atomic_load_explicit)|
|[atomic_signal_fence](#atomic_signal_fence)|[atomic_store](#atomic_store)|[atomic_store_explicit](#atomic_store_explicit)|
|[atomic_thread_fence –](#atomic_thread_fence)|[kill_dependency](#kill_dependency)|

## <a name="atomic_compare_exchange_strong"></a>  atomic_compare_exchange_strong –

Provádí operaci atomické porovnání a záměna.

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

*Atom* ukazatel *atomické* objekt, který ukládá hodnotu typu `Ty`.

*Exp* ukazatel na hodnotu typu `Ty`.

*Hodnota* hodnotu typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Tato metoda provádí operaci atomické porovnání a záměna použitím implicitních `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumenty. Další informace najdete v tématu [atomic_compare_exchange_strong_explicit –](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit).

## <a name="atomic_compare_exchange_strong_explicit"></a>  atomic_compare_exchange_strong_explicit

Provádí *atomické porovnání a záměna* operace.

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

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `Ty`.

*Exp* ukazatel na hodnotu typu `Ty`.

*Hodnota* hodnotu typu `Ty`.

*Order1* první [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argument.

*Order2* druhý `memory_order` argument. Hodnota *Order2* nemůže být `memory_order_release` nebo `memory_order_acq_rel`, nemůže být silnější než hodnota *Order1*.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

*Atomická operace porovnání a záměna* porovnává hodnotu uloženou v objektu, který ukazuje *Atom* oproti hodnotě, ukazuje *Exp*. Pokud jsou hodnoty rovny, hodnotu, která je uložena v objektu, který ukazuje *atom* nahradí *hodnotu* pomocí `read-modify-write` operace a použitím omezení pořadí paměti, které jsou určená *Order1*. Pokud nejsou hodnoty stejné, operace nahradí hodnotu, která ukazuje *Exp* s hodnotou, která je uložena v objektu, který ukazuje *Atom* a použije omezení pořadí paměti, které jsou určená *Order2*.

## <a name="atomic_compare_exchange_weak"></a>  atomic_compare_exchange_weak –

Provádí *slabé atomické porovnání a výměna* operace.

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

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `Ty`.

*Exp* ukazatel na hodnotu typu `Ty`.

*Hodnota* hodnotu typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Tato metoda provádí *slabé atomické porovnání a výměna operace* , která má implicitní `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argumenty. Další informace najdete v tématu [atomic_compare_exchange_weak_explicit –](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit).

## <a name="atomic_compare_exchange_weak_explicit"></a>  atomic_compare_exchange_weak_explicit

Provádí *slabé atomické porovnání a výměna* operace.

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

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `Ty`.

*Exp* ukazatel na hodnotu typu `Ty`.

*Hodnota* hodnotu typu `Ty`.

*Order1* první [memory_order](../standard-library/atomic-enums.md#memory_order_enum) argument.

*Order2* druhý `memory_order` argument. Hodnota *Order2* nemůže být `memory_order_release` nebo `memory_order_acq_rel`, ani nemůže být silnější než hodnota *Order1*.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou hodnoty stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Silné a slabé typy z *atomická operace porovnání a záměna* záruky, které jsou v nich uložené novou hodnotu, není-li očekávaným způsobem a je aktuální hodnoty nejsou shodné. Silné charakter zaručuje, že ho uloží novou hodnotu, když očekávaným způsobem a je aktuální hodnoty rovnají. Někdy může vrátit slabé flavor **false** a ukládat je nová hodnota i v případě, že aktuální a očekávané hodnoty jsou stejné. Jinými slovy, funkce vrátí **false**, ale pozdější prozkoumání očekávané hodnoty může odhalit, že nezměnil a proto by měl mít porovnání rovnají.

## <a name="atomic_exchange"></a>  atomic_exchange –

Používá *hodnotu* k nahrazení uložené hodnoty *Atom*.

```cpp
template <class T>
inline Ty atomic_exchange(volatile atomic<Ty>* _Atom, Ty Value) noexcept;

template <class Ty>
inline T atomic_exchange(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `Ty`.

*Hodnota* hodnotu typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

Uložené hodnoty *Atom* před výměnou.

### <a name="remarks"></a>Poznámky

`atomic_exchange` Funkce provádí `read-modify-write` operace k výměně hodnoty uložené v *Atom* s *hodnotu*, použije `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_exchange_explicit"></a>  atomic_exchange_explicit –

Nahradí uloženou hodnotu *Atom* s *hodnota*.

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

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `Ty`.

*Hodnota* hodnotu typu `Ty`.

*Pořadí* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Uložené hodnoty *Atom* před výměnou.

### <a name="remarks"></a>Poznámky

`atomic_exchange_explicit` Funkce provádí `read-modify-write` operace k výměně hodnoty uložené v *Atom* s *hodnotu*, v rámci omezení paměti, která jsou určena podle  *Pořadí*.

## <a name="atomic_fetch_add"></a>  atomic_fetch_add –

Přidá hodnotu do existující hodnotu, která je uložena v `atomic` objektu.

```cpp
template <class T>
T* atomic_fetch_add(volatile atomic<T*>* Atom, ptrdiff_t Value) noexcept;
template <class T>
T* atomic_fetch_add(atomic<T*>* Atom, ptrdiff_t Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* ukazatel `atomic` objekt, který uchovává ukazatel na typ `T`.

*Hodnota* hodnotu typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsažená v atomickém objektu těsně před spuštěním operace.

### <a name="remarks"></a>Poznámky

`atomic_fetch_add` Funkce provádí `read-modify-write` operace a přidává tak atomicky *hodnotu* k uložené hodnotě v *Atom*, použije `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum)omezení.

Pokud je Atomický typ `atomic_address`, *hodnotu* má typ `ptrdiff_t` a operace považují uložený ukazatel `char *`.

Tato operace je také přetížena pro integrální typy:

```cpp
integral atomic_fetch_add(volatile atomic-integral* Atom, integral Value) noexcept;

integral atomic_fetch_add(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_add_explicit"></a>  atomic_fetch_add_explicit –

Přidá hodnotu do existující hodnotu, která je uložena v `atomic` objektu.

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

*Atom* ukazatel `atomic` objekt, který uchovává ukazatel na typ `T`.

*Hodnota* hodnotu typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsažená v atomickém objektu těsně před spuštěním operace.

### <a name="remarks"></a>Poznámky

`atomic_fetch_add_explicit` Funkce provádí `read-modify-write` operace a přidává tak atomicky *hodnotu* do hodnoty uložené v proměnné *Atom*, v rámci [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení která jsou určena podle `Order`.

Pokud je Atomický typ `atomic_address`, `Value` má typ `ptrdiff_t` a operace považují uložený ukazatel `char *`.

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

## <a name="atomic_fetch_and"></a>  atomic_fetch_and –

Provádí logické bitové `and` na hodnotu a existující hodnotu, která je uložena v `atomic` objektu.

```cpp
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_and(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `T`.

*Hodnota* hodnotu typu `T`.

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomickém objektu těsně před spuštěním operace.

### <a name="remarks"></a>Poznámky

`atomic_fetch_and` Funkce provádí `read-modify-write` operace k nahrazení uložené hodnoty *Atom* logickou bitovou hodnotou `and` z *hodnota* a aktuální hodnotou, která je uložena v *Atom*, použije `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

## <a name="atomic_fetch_and_explicit"></a>  atomic_fetch_and_explicit –

Provádí logické bitové `and` hodnotu a existující hodnotu, která je uložena v `atomic` objektu.

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

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `T`.

*Hodnota* hodnotu typu `T`.

*Pořadí* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomickém objektu těsně před spuštěním operace.

### <a name="remarks"></a>Poznámky

`atomic_fetch_and_explicit` Funkce provádí `read-modify-write` operace k nahrazení uložené hodnoty *Atom* logickou bitovou hodnotou `and` z *hodnota* a aktuální hodnotou, která je uložena v *Atom*, v rámci omezení paměti, která jsou určena podle *pořadí*.

## <a name="atomic_fetch_or"></a>  atomic_fetch_or –

Provádí logické bitové `or` na hodnotu a existující hodnotu, která je uložena v `atomic` objektu.

```cpp
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
template <class T>
inline T atomic_fetch_or (volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `T`.

*Hodnota* hodnotu typu `T`.

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomickém objektu těsně před spuštěním operace.

### <a name="remarks"></a>Poznámky

`atomic_fetch_or` Funkce provádí `read-modify-write` operace k nahrazení uložené hodnoty *Atom* logickou bitovou hodnotou `or` z *hodnota* a aktuální hodnotou, která je uložena v *Atom*, použije `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_or_explicit"></a>  atomic_fetch_or_explicit –

Provádí logické bitové `or` na hodnotu a existující hodnotu, která je uložena v `atomic` objektu.

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

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `T`.

*Hodnota* hodnotu typu `T`.

*Pořadí* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomickém objektu těsně před spuštěním operace.

### <a name="remarks"></a>Poznámky

`atomic_fetch_or_explicit` Funkce provádí `read-modify-write` operace k nahrazení uložené hodnoty *Atom* logickou bitovou hodnotou `or` z *hodnota* a aktuální hodnotou, která je uložena v *Atom*, v rámci [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení určené *pořadí*.

## <a name="atomic_fetch_sub"></a>  atomic_fetch_sub –

Odečte hodnotu z existující hodnoty, která je uložena v `atomic` objektu.

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

*Atom* ukazatel `atomic` objekt, který uchovává ukazatel na typ `T`.

*Hodnota* hodnotu typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsažená v atomickém objektu těsně před spuštěním operace.

### <a name="remarks"></a>Poznámky

`atomic_fetch_sub` Funkce provádí `read-modify-write` operace a odebírá tak atomicky *hodnotu* z hodnoty uložené v proměnné *Atom*, použije `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

Pokud je Atomický typ `atomic_address`, *hodnotu* má typ `ptrdiff_t` a operace považují uložený ukazatel `char *`.

Tato operace je také přetížena pro integrální typy:

```cpp
integral atomic_fetch_sub(volatile atomic-integral* Atom, integral Value) noexcept;
integral atomic_fetch_sub(atomic-integral* Atom, integral Value) noexcept;
```

## <a name="atomic_fetch_sub_explicit"></a>  atomic_fetch_sub_explicit –

Odečte hodnotu z existující hodnoty, která je uložena v `atomic` objektu.

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

*Atom* ukazatel `atomic` objekt, který uchovává ukazatel na typ `T`.

*Hodnota* hodnotu typu `ptrdiff_t`.

### <a name="return-value"></a>Návratová hodnota

Hodnota ukazatele obsažená v atomickém objektu těsně před spuštěním operace.

### <a name="remarks"></a>Poznámky

`atomic_fetch_sub_explicit` Funkce provádí `read-modify-write` operace a odebírá tak atomicky *hodnotu* z hodnoty uložené v proměnné *Atom*, v rámci [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení, která jsou určena podle `Order`.

Pokud je Atomický typ `atomic_address`, *hodnotu* má typ `ptrdiff_t` a operace považují uložený ukazatel `char *`.

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

## <a name="atomic_fetch_xor"></a>  atomic_fetch_xor –

Provádí logické bitové `exclusive or` na hodnotu a existující hodnotu, která je uložena v `atomic` objektu.

```cpp
template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;

template <class T>
inline T atomic_fetch_xor(volatile atomic<T>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `T`.

*Hodnota* hodnotu typu `T`.

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomickém objektu těsně před spuštěním operace.

### <a name="remarks"></a>Poznámky

`atomic_fetch_xor` Funkce provádí `read-modify-write` operace k nahrazení uložené hodnoty *Atom* logickou bitovou hodnotou `exclusive or` z *hodnota* a aktuální hodnotou, která je uložena v *Atom*, použije `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_fetch_xor_explicit"></a>  atomic_fetch_xor_explicit –

Provádí logické bitové `exclusive or` na hodnotu a existující hodnotu, která je uložena v `atomic` objektu.

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

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `T`.

*Hodnota* hodnotu typu `T`.

*Pořadí* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Hodnota obsažená v atomickém objektu těsně před spuštěním operace.

### <a name="remarks"></a>Poznámky

`atomic_fetch_xor_explicit` Funkce provádí `read-modify-write` operace k nahrazení uložené hodnoty *Atom* logickou bitovou hodnotou `exclusive or` z *hodnota* a aktuální hodnotou, která je uložena v *Atom*, v rámci [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení, která jsou určena podle *pořadí*.

## <a name="atomic_flag_clear"></a>  atomic_flag_clear

Nastaví **bool** příznak v [atomic_flag](../standard-library/atomic-flag-structure.md) objektu **false**, v rámci `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline void atomic_flag_clear(volatile atomic_flag* Flag) noexcept;
inline void atomic_flag_clear(atomic_flag* Flag) noexcept;
```

### <a name="parameters"></a>Parametry

*Příznak* ukazatel `atomic_flag` objektu.

## <a name="atomic_flag_clear_explicit"></a>  atomic_flag_clear_explicit

Nastaví **bool** příznak v [atomic_flag](../standard-library/atomic-flag-structure.md) objektu **false**, v rámci zadaného [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

```cpp
inline void atomic_flag_clear_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline void atomic_flag_clear_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Příznak* ukazatel `atomic_flag` objektu.

*Pořadí* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flag_test_and_set"></a>  atomic_flag_test_and_set

Nastaví **bool** příznak v [atomic_flag](../standard-library/atomic-flag-structure.md) objektu **true**, v rámci omezení `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
inline bool atomic_flag_test_and_set(volatile atomic_flag* Flag,) noexcept;
inline bool atomic_flag_test_and_set(atomic_flag* Flag,) noexcept;
```

### <a name="parameters"></a>Parametry

*Příznak* ukazatel `atomic_flag` objektu.

### <a name="return-value"></a>Návratová hodnota

Počáteční hodnota *příznak*.

## <a name="atomic_flag_test_and_set_explicit"></a>  atomic_flag_test_and_set_explicit

Nastaví **bool** příznak v [atomic_flag](../standard-library/atomic-flag-structure.md) objektu **true**, v rámci zadaného [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

```cpp
inline bool atomic_flag_test_and_set_explicit(volatile atomic_flag* Flag, memory_order Order) noexcept;
inline bool atomic_flag_test_and_set_explicit(atomic_flag* Flag, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Příznak* ukazatel `atomic_flag` objektu.

*Pořadí* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Návratová hodnota

Počáteční hodnota *příznak*.

## <a name="atomic_init"></a>  atomic_init –

Nastaví hodnotu uloženou v `atomic` objektu.

```cpp
template <class Ty>
inline void atomic_init(volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline void atomic_init(atomic<Ty>* Atom, Ty Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `Ty`.

*Hodnota* hodnotu typu `Ty`.

### <a name="remarks"></a>Poznámky

`atomic_init` není atomická operace. Není bezpečné pro vlákna.

## <a name="atomic_is_lock_free"></a>  atomic_is_lock_free –

Určuje, zda atomické operace na `atomic` objektu jsou *bez zámku*.

```cpp
template <class T>
inline bool atomic_is_lock_free(const volatile atomic<T>* Atom) noexcept;
template <class T>
inline bool atomic_is_lock_free(const atomic<T>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* ukazatel `atomic` objekt, který ukládá hodnotu typu `T`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud atomické operace na *Atom* jsou bez zámku; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Atomický typ je bez Pokud žádné atomické operace na daném typu nepoužívají zámky zámku. Pokud tato funkce vrací hodnotu true, typ je bezpečný pro použití v obslužných rutinách signálu.

## <a name="atomic_load"></a>  atomic_load –

Načte uloženou hodnotu do `atomic` objektu.

```cpp
template <class Ty>
inline Ty atomic_load(const volatile atomic<Ty>* Atom) noexcept;
template <class Ty>
inline Ty atomic_load(const atomic<Ty>* Atom) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* ukazatel `atomic` objekt, který obsahuje hodnotu typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

Načtená hodnota, která je uložena v *Atom*.

### <a name="remarks"></a>Poznámky

`atomic_load` implicitně používá `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_load_explicit"></a>  atomic_load_explicit –

Načte uloženou hodnotu do `atomic` objekt v rámci určeného [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

```cpp
template <class Ty>
inline Ty atomic_load_explicit(const volatile atomic<Ty>* Atom, memory_order Order) noexcept;
template <class Ty>
inline Ty atomic_load_explicit(const atomic<Ty>* Atom, memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* ukazatel `atomic` objekt, který obsahuje hodnotu typu `Ty`.

*Pořadí* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nepoužívejte `memory_order_release` nebo `memory_order_acq_rel`.

### <a name="return-value"></a>Návratová hodnota

Načtená hodnota, která je uložena v *Atom*.

## <a name="atomic_signal_fence"></a>  atomic_signal_fence –

Funguje jako *ohrazení*– což je primitiv synchronizace paměti vynucující řazení mezi operacemi načtení/uložení – mezi jinými ohrazeními ve volajícím vláknu, které mají obslužné rutiny signálu spouštěné ve stejném vlákně.

```cpp
inline void atomic_signal_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Pořadí* omezení, která určuje typ plotu řazení paměti.

### <a name="remarks"></a>Poznámky

*Pořadí* argument určuje typ plotu.

|||
|-|-|
|`memory_order_relaxed`|Ohrazení nemá žádný vliv.|
|`memory_order_consume`|Plot je plot získání.|
|`memory_order_acquire`|Plot je plot získání.|
|`memory_order_release`|Plot je plot uvolňování.|
|`memory_order_acq_rel`|Plot je plot získání i plot uvolnění.|
|`memory_order_seq_cst`|Plot je plot získání i plot uvolnění a je sekvenčně konzistentní.|

## <a name="atomic_store"></a>  atomic_store –

Atomicky ukládá hodnotu v atomickém objektu.

```cpp
template <class Ty>
inline Ty atomic_store_explicit(const volatile atomic<Ty>* Atom, Ty Value) noexcept;
template <class Ty>
inline Ty atomic_store_explicit(const atomic<Ty>* Atom, T Value) noexcept;
```

### <a name="parameters"></a>Parametry

*Atom* ukazatel na Atomický objekt, který obsahuje hodnotu typu `Ty`.

*Hodnota* hodnotu typu `Ty`.

### <a name="remarks"></a>Poznámky

`atomic_store` ukládá *hodnotu* v objektu, který ukazuje *Atom*, v rámci `memory_order_seq_cst` [memory_order](../standard-library/atomic-enums.md#memory_order_enum) omezení.

## <a name="atomic_store_explicit"></a>  atomic_store_explicit –

Atomicky ukládá hodnotu v atomickém objektu.

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

*Atom* ukazatel `atomic` objekt, který obsahuje hodnotu typu `Ty`.

*Hodnota* hodnotu typu `Ty`.

*Pořadí* A [memory_order](../standard-library/atomic-enums.md#memory_order_enum). Nepoužívejte `memory_order_consume`, `memory_order_acquire`, nebo `memory_order_acq_rel`.

### <a name="remarks"></a>Poznámky

`atomic_store` ukládá *hodnotu* v objektu, který ukazuje *Atom*, v rámci `memory_order` určené *pořadí*.

## <a name="atomic_thread_fence"></a>  atomic_thread_fence –

Funguje jako *ohrazení*– což je primitiv synchronizace paměti vynucující řazení mezi operacemi načtení/uložení – bez přidružené atomické operace.

```cpp
inline void atomic_thread_fence(memory_order Order) noexcept;
```

### <a name="parameters"></a>Parametry

*Pořadí* omezení, která určuje typ plotu řazení paměti.

### <a name="remarks"></a>Poznámky

*Pořadí* argument určuje typ plotu.

|||
|-|-|
|`memory_order_relaxed`|Ohrazení nemá žádný vliv.|
|`memory_order_consume`|Plot je plot získání.|
|`memory_order_acquire`|Plot je plot získání.|
|`memory_order_release`|Plot je plot uvolňování.|
|`memory_order_acq_rel`|Plot je plot získání i plot uvolnění.|
|`memory_order_seq_cst`|Plot je plot získání i plot uvolnění a je sekvenčně konzistentní.|

## <a name="kill_dependency"></a>  kill_dependency –

Odebere závislost.

```cpp
template <class Ty>
Ty kill_dependency(Ty Arg) noexcept;
```

### <a name="parameters"></a>Parametry

*Arg* hodnotu typu `Ty`.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je *Arg*. Vyhodnocení *Arg* neobsahuje závislosti pro volání funkce. Tím, že rozkládají řetěz závislostí je to možné, může povolit funkci kompilátor generuje kód efektivnější.

## <a name="see-also"></a>Viz také:

[\<Atomic >](../standard-library/atomic.md)<br/>
