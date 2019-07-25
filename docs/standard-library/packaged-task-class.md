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
ms.openlocfilehash: 5bb04b84b723f239c338c02befa8cd3468cec3f2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450084"
---
# <a name="packagedtask-class"></a>packaged_task – třída

Popisuje *asynchronního zprostředkovatele* , který je obálkou volání, jehož signatura volání je `Ty(ArgTypes...)`. Jeho *přidružený asynchronní stav* obsahuje kopii jeho volatelné objektu kromě potenciálního výsledku.

## <a name="syntax"></a>Syntaxe

```cpp
template <class>
class packaged_task;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[packaged_task](#packaged_task)|`packaged_task` Vytvoří objekt.|
|[packaged_task::~packaged_task Destructor](#dtorpackaged_task_destructor)|`packaged_task` Odstraní objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[get_future](#get_future)|Vrátí [budoucí](../standard-library/future-class.md) objekt, který má stejný přidružený asynchronní stav.|
|[make_ready_at_thread_exit](#make_ready_at_thread_exit)|Volá objekt pro volání, který je uložen v přidruženém asynchronním stavu a atomicky ukládá vrácenou hodnotu.|
|[reset](#reset)|Nahradí přidružený asynchronní stav.|
|[swap](#swap)|Vyměňuje přidružený asynchronní stav se zadaným objektem.|
|[platný](#valid)|Určuje, zda má objekt přidružený asynchronní stav.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[packaged_task::operator=](#op_eq)|Převede přidružený asynchronní stav ze zadaného objektu.|
|[packaged_task::operator()](#op_call)|Volá objekt pro volání, který je uložen v přidruženém asynchronním stavu, atomicky ukládá vrácenou hodnotu a nastaví stav na *připraveno*.|
|[packaged_task:: operator bool](#op_bool)|Určuje, zda má objekt přidružený asynchronní stav.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<budoucí >

**Obor názvů:** std

## <a name="get_future"></a>packaged_task::get_future

Vrátí objekt typu `future<Ty>` , který má stejný *přidružený asynchronní stav*.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Poznámky

Pokud objekt nemá přidružený asynchronní stav, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód `no_state`chyby. `packaged_task`

Pokud již byla tato metoda volána pro `packaged_task` objekt, který má stejný přidružený asynchronní stav, metoda `future_error` vyvolá výjimku, která `future_already_retrieved`má kód chyby.

## <a name="make_ready_at_thread_exit"></a>packaged_task::make_ready_at_thread_exit

Volá objekt pro volání, který je uložen v *přidruženém asynchronním stavu* a atomicky ukládá vrácenou hodnotu.

```cpp
void make_ready_at_thread_exit(ArgTypes... args);
```

### <a name="remarks"></a>Poznámky

Pokud objekt nemá přidružený asynchronní stav, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód `no_state`chyby. `packaged_task`

Pokud tato metoda nebo [make_ready_at_thread_exit](#make_ready_at_thread_exit) již byla volána pro `packaged_task` objekt, který má stejný přidružený asynchronní stav, metoda vyvolá výjimku `future_error` , která má kód `promise_already_satisfied`chyby.

V opačném případě tento `INVOKE(fn, args..., Ty)`operátor volá, kde *FN* je přivolatelné objekty, které jsou uloženy v přidruženém asynchronním stavu. Všechny vrácené hodnoty jsou uloženy atomicky jako vrácený výsledek přidruženého asynchronního stavu.

Na rozdíl od [packaged_task:: operator ()](#op_call)není přidružený asynchronní stav nastaven na `ready` dokud všechny místní objekty v volajícím vlákně nejsou zničeny. Vlákna, která jsou zablokována v přidruženém asynchronním stavu, jsou obvykle odblokována, dokud volající vlákno neukončí.

## <a name="op_eq"></a>packaged_task:: operator =

Převede *přidružený asynchronní stav* ze zadaného objektu.

```cpp
packaged_task& operator=(packaged_task&& Right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
`packaged_task` Objekt.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Po operaci již nemá  k dispozici přidružený asynchronní stav.

## <a name="op_call"></a>packaged_task:: operator () – operátor ()

Volá objekt pro volání, který je uložen v *přidruženém asynchronním stavu*, atomicky ukládá vrácenou hodnotu a nastaví stav na *připraveno*.

```cpp
void operator()(ArgTypes... args);
```

### <a name="remarks"></a>Poznámky

Pokud objekt nemá přidružený asynchronní stav, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód `no_state`chyby. `packaged_task`

Pokud tato metoda nebo [make_ready_at_thread_exit](#make_ready_at_thread_exit) již byla volána pro `packaged_task` objekt, který má stejný přidružený asynchronní stav, metoda vyvolá výjimku `future_error` , která má kód `promise_already_satisfied`chyby.

V opačném případě tento `INVOKE(fn, args..., Ty)`operátor volá, kde *FN* je přivolatelné objekty, které jsou uloženy v přidruženém asynchronním stavu. Vrácená hodnota je uložená atomicky jako vrácený výsledek přidruženého asynchronního stavu a stav je nastaven na připraveno. V důsledku toho dojde k odblokování všech vláken, která jsou blokována v přidruženém asynchronním stavu.

## <a name="op_bool"></a>packaged_task:: operator bool

Určuje, zda má `associated asynchronous state`objekt.

```cpp
operator bool() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud má objekt přidružený asynchronní stav; v opačném případě **false**.

## <a name="packaged_task"></a>packaged_task::p ackaged_task – konstruktor

`packaged_task` Vytvoří objekt.

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

*Kliknutím*\
A `packaged_task` objektu.

*vyhrazen*\
Přidělování paměti. Další informace najdete v tématu [ \<přidělování >](../standard-library/allocators-header.md).

*VistaScan*\
Objekt funkce.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří `packaged_task` objekt, který nemá *přidružený asynchronní stav*.

Druhý konstruktor vytvoří `packaged_task` objekt a převede přidružený asynchronní stav *zprava*. Po operaci již nemá  k dispozici přidružený asynchronní stav.

Třetí konstruktor vytvoří `packaged_task` objekt, který má kopii *FN* uloženou v přidruženém asynchronním stavu.

Čtvrtý konstruktor vytvoří `packaged_task` objekt, který má kopii *FN* uloženou v přidruženém asynchronním stavu a používá `alloc` pro přidělení paměti.

## <a name="dtorpackaged_task_destructor"></a>packaged_task:: ~ packaged_task – destruktor

`packaged_task` Odstraní objekt.

```cpp
~packaged_task();
```

### <a name="remarks"></a>Poznámky

Pokud *přidružený asynchronní stav* není *připravený*, destruktor uloží výjimku [future_error](../standard-library/future-error-class.md) , která `broken_promise` má chybový kód jako výsledek v přidruženém asynchronním stavu, a všechna vlákna, která jsou zablokovaná na dojde k odblokování přidruženého asynchronního stavu.

## <a name="reset"></a>packaged_task:: Reset

Použije nový *přidružený asynchronní stav* k nahrazení stávajícího přidruženého asynchronního stavu.

```cpp
void reset();
```

### <a name="remarks"></a>Poznámky

V důsledku toho je tato metoda `*this = packaged_task(move(fn))`spuštěna, kde *FN* je objekt funkce, který je uložen v přidruženém asynchronním stavu pro tento objekt. Proto je stav objektu vymazán a [get_future](#get_future), [operator ()](#op_call)a [make_ready_at_thread_exit](#make_ready_at_thread_exit) lze volat jako if u nově vytvořeného objektu.

## <a name="swap"></a>packaged_task:: swap

Vyměňuje přidružený asynchronní stav se zadaným objektem.

```cpp
void swap(packaged_task& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
A `packaged_task` objektu.

## <a name="valid"></a>packaged_task:: platný

Určuje, zda má `associated asynchronous state`objekt.

```cpp
bool valid() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud má objekt přidružený asynchronní stav; v opačném případě **false**.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<budoucí >](../standard-library/future.md)
