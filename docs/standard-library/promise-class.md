---
title: promise – třída
ms.date: 10/18/2018
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.openlocfilehash: a6541fefb2423853f8e59a662e1c8a37777dc14c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323043"
---
# <a name="promise-class"></a>promise – třída

Popisuje *asynchronního zprostředkovatele*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class promise;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Slib](#promise)|Vytvoří `promise` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[get_future](#get_future)|Vrátí [budoucnost](../standard-library/future-class.md) přidruženou k tomuto slibu.|
|[set_exception](#set_exception)|Atomicky nastaví výsledek tohoto slibu označující výjimku.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Atomicky nastaví výsledek tohoto slibu označující výjimku a odešle oznámení pouze poté, co všechny objekty místní vlákno v aktuálním vlákně byly zničeny (obvykle při ukončení podprocesu).|
|[set_value](#set_value)|Atomicky nastaví výsledek tohoto slibu k označení hodnoty.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Atomicky nastaví výsledek tohoto slibu označit hodnotu a odešle oznámení pouze po všechny objekty místní vlákno v aktuálním vlákně byly zničeny (obvykle při ukončení podprocesu).|
|[Swap](#swap)|Vyměňuje *přidružený asynchronní stav* tohoto příslibu s zadaným objektem promise.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[slíbit::operátor=](#op_eq)|Přiřazení sdíleného stavu tohoto objektu zaslíbení.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

*Slib*

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<budoucí>

**Obor názvů:** std

## <a name="promiseget_future"></a><a name="get_future"></a>zaslíbení::get_future

Vrátí [budoucí](../standard-library/future-class.md) objekt, který má stejný *přidružený asynchronní stav* jako tento slib.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt promise prázdný, tato metoda vyvolá [future_error,](../standard-library/future-error-class.md) která má [error_code](../standard-library/error-code-class.md) `no_state`.

Pokud tato metoda již byla volána pro promise objekt, který má stejný přidružený `future_error` asynchronní stav, metoda vyvolá, který má `error_code` . `future_already_retrieved`

## <a name="promiseoperator"></a><a name="op_eq"></a>slíbit::operátor=

Přenese *přidružený asynchronní* stav `promise` ze zadaného objektu.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Další*\
Objekt. `promise`

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Tento operátor přenáší přidružený asynchronní stav z *jiného*. Po převodu *Other* je *prázdný*.

## <a name="promisepromise-constructor"></a><a name="promise"></a>slib::promise konstruktor

Vytvoří `promise` objekt.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Al*\
Alokátor paměti. Další informace naleznete [ \<v>přidělování.](../standard-library/allocators-header.md)

*Další*\
Objekt. `promise`

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří *prázdný* `promise` objekt.

Druhý konstruktor vytvoří prázdný `promise` objekt a použije *Al* pro přidělení paměti.

Třetí konstruktor vytvoří `promise` objekt a přenese přidružený asynchronní stav z *jiného*a ponechá *other* prázdný.

## <a name="promiseset_exception"></a><a name="set_exception"></a>slib::set_exception

Atomicky ukládá výjimku jako `promise` výsledek tohoto objektu a nastaví *přidružený asynchronní stav* na *připraven*.

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

*Výborný*\
[exception_ptr,](../standard-library/exception-typedefs.md#exception_ptr) který je uložen touto metodou jako výsledek výjimky.

### <a name="remarks"></a>Poznámky

Pokud `promise` objekt nemá žádný přidružený asynchronní stav, tato metoda vyvolá [future_error,](../standard-library/future-error-class.md) který má kód chyby `no_state`.

Pokud `set_exception`již byl `promise` volán `future_error` `promise_already_satisfied` [objekt,](#set_exception_at_thread_exit)který má stejný přidružený asynchronní stav, set_exception_at_thread_exit , [set_value](#set_value)nebo [set_value_at_thread_exit,](#set_value_at_thread_exit) tato metoda vyvolá kód chyby .

V důsledku této metody budou odblokována všechna vlákna, která jsou blokována v přidruženém asynchronním stavu.

## <a name="promiseset_exception_at_thread_exit"></a><a name="set_exception_at_thread_exit"></a>slíbit::set_exception_at_thread_exit

Atomicky nastaví výsledek `promise` tohoto označující výjimku, doručení oznámení pouze po všechny místní objekty podprocesu v aktuálním vlákně byly zničeny (obvykle při ukončení podprocesu).

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

*Výborný*\
[exception_ptr,](../standard-library/exception-typedefs.md#exception_ptr) který je uložen touto metodou jako výsledek výjimky.

### <a name="remarks"></a>Poznámky

Pokud objekt promise nemá žádný *přidružený asynchronní stav*, tato metoda vyvolá `no_state` [future_error,](../standard-library/future-error-class.md) který má kód chyby .

Pokud již `set_exception_at_thread_exit`byl volán `promise` [objekt,](#set_exception)který má stejný přidružený asynchronní stav, set_exception , `future_error` [set_value](#set_value)nebo [set_value_at_thread_exit,](#set_value_at_thread_exit) tato metoda vyvolá kód chyby `promise_already_satisfied`.

Na rozdíl od [set_exception](#set_exception)tato metoda nenastaví přidružený asynchronní stav na připraven, dokud nebudou zničeny všechny místní objekty podprocesu v aktuálním vlákně. Obvykle vlákna, které jsou blokovány v přidruženém asynchronním stavu nejsou odblokovány, dokud aktuální vlákno ukončí.

## <a name="promiseset_value"></a><a name="set_value"></a>slib::set_value

Atomicky ukládá hodnotu jako `promise` výsledek tohoto objektu a nastaví *přidružený asynchronní stav* na *připraven*.

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>Parametry

*Val*\
Hodnota, která má být uložena jako výsledek.

### <a name="remarks"></a>Poznámky

Pokud `promise` objekt nemá žádný přidružený asynchronní stav, tato metoda vyvolá [future_error,](../standard-library/future-error-class.md) který má kód chyby `no_state`.

Pokud již [set_exception_at_thread_exit](#set_exception_at_thread_exit)byl `set_value`volán `promise` [set_exception](#set_exception), set_exception_at_thread_exit nebo [set_value_at_thread_exit](#set_value_at_thread_exit) pro objekt, který má stejný přidružený `future_error` asynchronní stav, tato metoda vyvolá kód chyby `promise_already_satisfied`.

V důsledku této metody budou odblokována všechna vlákna, která jsou blokována v přidruženém asynchronním stavu.

První metoda také vyvolá všechny výjimky, která je vyvolána při *Val* je zkopírován do přidruženého asynchronního stavu. V takovém případě přidružený asynchronní stav není nastavena na připraven.

Druhá metoda také vyvolá všechny výjimky, která je vyvolána při *Val* je přesunuta do přidruženého asynchronního stavu. V takovém případě přidružený asynchronní stav není nastavena na připraven.

Pro částečnou `promise<Ty&>`specializaci je uložená hodnota ve skutečnosti odkazem na *Val*.

Pro specializaci `promise<void>`neexistuje žádná uložená hodnota.

## <a name="promiseset_value_at_thread_exit"></a><a name="set_value_at_thread_exit"></a>slib::set_value_at_thread_exit

Atomicky ukládá hodnotu jako `promise` výsledek tohoto objektu.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>Parametry

*Val*\
Hodnota, která má být uložena jako výsledek.

### <a name="remarks"></a>Poznámky

Pokud objekt promise nemá žádný *přidružený asynchronní stav*, tato metoda vyvolá `no_state` [future_error,](../standard-library/future-error-class.md) který má kód chyby .

Pokud [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value) `set_value_at_thread_exit` nebo `promise` již byla volána pro objekt, který má stejný `future_error` přidružený asynchronní `promise_already_satisfied`stav, tato metoda vyvolá, který má kód chyby .

Na rozdíl `set_value`od , přidružený asynchronní stav není nastavena na připraven, dokud všechny místní objekty vlákna v aktuálním vlákně byly zničeny. Obvykle vlákna, které jsou blokovány v přidruženém asynchronním stavu nejsou odblokovány, dokud aktuální vlákno ukončí.

První metoda také vyvolá všechny výjimky, která je vyvolána při *Val* je zkopírován do přidruženého asynchronního stavu.

Druhá metoda také vyvolá všechny výjimky, která je vyvolána při *Val* je přesunuta do přidruženého asynchronního stavu.

Pro částečnou `promise<Ty&>`specializaci je uložená hodnota skutečně odkazem na *Val*.

Pro specializaci `promise<void>`neexistuje žádná uložená hodnota.

## <a name="promiseswap"></a><a name="swap"></a>promise::swap

Vyměňuje *přidružený asynchronní stav* tohoto objektu promise s stavem zadaného objektu.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Další*\
Objekt. `promise`

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)
