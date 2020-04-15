---
title: packaged_task – třída
ms.date: 11/04/2016
f1_keywords:
- future/std::packaged_task
- future/std::packaged_task::packaged_task
- future/std::packaged_task::get_future
- future/std::packaged_task::make_ready_at_thread_exit
- future/std::packaged_task::reset
- future/std::packaged_task::swap
- future/std::packaged_task::valid
- future/std::packaged_task::operator()
- future/std::packaged_task::operator bool
ms.assetid: 0a72cbe3-f22a-4bfe-8e50-dcb268c98780
helpviewer_keywords:
- std::packaged_task [C++]
- std::packaged_task [C++], packaged_task
- std::packaged_task [C++], get_future
- std::packaged_task [C++], make_ready_at_thread_exit
- std::packaged_task [C++], reset
- std::packaged_task [C++], swap
- std::packaged_task [C++], valid
ms.openlocfilehash: eb171e09451e16e89716dfdc44ed6c611e2d2280
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372127"
---
# <a name="packaged_task-class"></a>packaged_task – třída

Popisuje *asynchronního zprostředkovatele,* který je obálkou `Ty(ArgTypes...)`volání, jejíž podpis volání je . Jeho *přidružený asynchronní stav* obsahuje kopii jeho volatelný objekt kromě potenciální výsledek.

## <a name="syntax"></a>Syntaxe

```cpp
template <class>
class packaged_task;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[packaged_task](#packaged_task)|Vytvoří `packaged_task` objekt.|
|[packaged_task::~packaged_task destruktor](#dtorpackaged_task_destructor)|Zničí `packaged_task` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[get_future](#get_future)|Vrátí [budoucí](../standard-library/future-class.md) objekt, který má stejný přidružený asynchronní stav.|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Volá volatelný objekt, který je uložen v přidruženém asynchronním stavu a atomicky ukládá vrácenou hodnotu.|
|[Obnovit](#reset)|Nahradí přidružený asynchronní stav.|
|[Swap](#swap)|Vyměňuje přidružený asynchronní stav s přidruženým asynchronním stavem zadaného objektu.|
|[Platný](#valid)|Určuje, zda má objekt přidružený asynchronní stav.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[packaged_task::operátor=](#op_eq)|Přenese přidružený asynchronní stav ze zadaného objektu.|
|[packaged_task::operátor()](#op_call)|Volá volatelný objekt, který je uložen v přidruženém asynchronním stavu, atomicky ukládá vrácenou hodnotu a nastaví stav na *připraven*.|
|[packaged_task::operátor bool](#op_bool)|Určuje, zda má objekt přidružený asynchronní stav.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<budoucí>

**Obor názvů:** std

## <a name="packaged_taskget_future"></a><a name="get_future"></a>packaged_task::get_future

Vrátí objekt typu, `future<Ty>` který má stejný přidružený *asynchronní stav*.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Poznámky

Pokud `packaged_task` objekt nemá přidružený asynchronní stav, tato metoda vyvolá [future_error,](../standard-library/future-error-class.md) který `no_state`má kód chyby .

Pokud tato metoda již byla `packaged_task` volána pro objekt, který má stejný přidružený `future_error` asynchronní stav, `future_already_retrieved`metoda vyvolá, který má kód chyby .

## <a name="packaged_taskmake_ready_at_thread_exit"></a><a name="make_ready_at_thread_exit"></a>packaged_task::make_ready_at_thread_exit

Volá volatelný objekt, který je uložen v *přidruženém asynchronním stavu* a atomicky ukládá vrácenou hodnotu.

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>Poznámky

Pokud `packaged_task` objekt nemá přidružený asynchronní stav, tato metoda vyvolá [future_error,](../standard-library/future-error-class.md) který má `no_state`kód chyby .

Pokud tato metoda nebo [make_ready_at_thread_exit](#make_ready_at_thread_exit) již `packaged_task` byla volána pro objekt, který má stejný `future_error` přidružený asynchronní `promise_already_satisfied`stav, metoda vyvolá, který má kód chyby .

Jinak tento operátor `INVOKE(fn, args..., Ty)`volá , kde *fn* je volatelný objekt, který je uložen v přidruženém asynchronním stavu. Všechny vrácené hodnoty je uložen atomicky jako vrácený výsledek přidruženého asynchronního stavu.

Na rozdíl od [packaged_task::operator()](#op_call)není přidružený asynchronní `ready` stav nastaven na hodnotu až poté, co byly zničeny všechny místní objekty v podprocesu. Obvykle vlákna, které jsou blokovány v přidruženém asynchronním stavu nejsou odblokovány, dokud volající vlákno ukončí.

## <a name="packaged_taskoperator"></a><a name="op_eq"></a>packaged_task::operátor=

Přenese *přidružený asynchronní stav* ze zadaného objektu.

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt. `packaged_task`

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Po operaci *Right* již nemá přidružený asynchronní stav.

## <a name="packaged_taskoperator"></a><a name="op_call"></a>packaged_task::operátor()

Volá objekt, který je uložen v *přidruženém asynchronním stavu*, atomicky ukládá vrácenou hodnotu a nastaví stav na *připraven*.

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>Poznámky

Pokud `packaged_task` objekt nemá přidružený asynchronní stav, tato metoda vyvolá [future_error,](../standard-library/future-error-class.md) který má `no_state`kód chyby .

Pokud tato metoda nebo [make_ready_at_thread_exit](#make_ready_at_thread_exit) již `packaged_task` byla volána pro objekt, který má stejný `future_error` přidružený asynchronní `promise_already_satisfied`stav, metoda vyvolá, který má kód chyby .

Jinak tento operátor `INVOKE(fn, args..., Ty)`volá , kde *fn* je volatelný objekt, který je uložen v přidruženém asynchronním stavu. Všechny vrácené hodnoty je uložen atomicky jako vrácený výsledek přidruženého asynchronního stavu a stav je nastaven na připraven. V důsledku toho budou odblokována všechna vlákna, která jsou blokována v přidruženém asynchronním stavu.

## <a name="packaged_taskoperator-bool"></a><a name="op_bool"></a>packaged_task::operátor bool

Určuje, zda má `associated asynchronous state`objekt soubor .

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud má objekt přidružený asynchronní stav; jinak **false**.

## <a name="packaged_taskpackaged_task-constructor"></a><a name="packaged_task"></a>packaged_task:konstruktor :packaged_task

Vytvoří `packaged_task` objekt.

```cpp
packaged_task() noexcept;
packaged_task(packaged_task&& Right) noexcept;
template <class Fn>
   explicit packaged_task(Fn&& fn);

template <class Fn, class Alloc>
   explicit packaged_task(
      allocator_arg_t, const Alloc& alloc, Fn&& fn);
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt. `packaged_task`

*Alloc*\
Alokátor paměti. Další informace naleznete [ \<v tématu alokátory>](../standard-library/allocators-header.md).

*Fn*\
Objekt funkce.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří `packaged_task` objekt, který nemá žádný *přidružený asynchronní stav*.

Druhý konstruktor vytvoří `packaged_task` objekt a přenese přidružený asynchronní stav z *Right*. Po operaci *Right* již nemá přidružený asynchronní stav.

Třetí konstruktor vytvoří `packaged_task` objekt, který má kopii *fn* uloženou v přidruženém asynchronním stavu.

Čtvrtý konstruktor vytvoří `packaged_task` objekt, který má kopii *fn* uloženou v přidruženém `alloc` asynchronním stavu a používá pro přidělení paměti.

## <a name="packaged_taskpackaged_task-destructor"></a><a name="dtorpackaged_task_destructor"></a>packaged_task::~packaged_task destruktor

Zničí `packaged_task` objekt.

```cpp
~packaged_task();
```

### <a name="remarks"></a>Poznámky

Pokud *přidružený asynchronní stav* není *připraven*, destruktor ukládá [future_error](../standard-library/future-error-class.md) výjimku, která má kód chyby `broken_promise` jako výsledek v přidruženém asynchronním stavu a všechna vlákna, která jsou blokována v přidruženém asynchronním stavu, budou odblokována.

## <a name="packaged_taskreset"></a><a name="reset"></a>packaged_task::obnovit

Používá nový *přidružený asynchronní stav* k nahrazení existujícího přidruženého asynchronního stavu.

```cpp
void reset();
```

### <a name="remarks"></a>Poznámky

Ve skutečnosti se tato `*this = packaged_task(move(fn))`metoda spustí , kde *fn* je objekt funkce, který je uložen v přidruženém asynchronním stavu pro tento objekt. Proto je zrušen stav objektu a [get_future](#get_future), [operátor()](#op_call)a [make_ready_at_thread_exit](#make_ready_at_thread_exit) lze volat jako by na nově konstruované objektu.

## <a name="packaged_taskswap"></a><a name="swap"></a>packaged_task::swap

Vyměňuje přidružený asynchronní stav s přidruženým asynchronním stavem zadaného objektu.

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt. `packaged_task`

## <a name="packaged_taskvalid"></a><a name="valid"></a>packaged_task::platný

Určuje, zda má `associated asynchronous state`objekt soubor .

```cpp
bool valid() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud má objekt přidružený asynchronní stav; jinak **false**.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<budoucí>](../standard-library/future.md)
