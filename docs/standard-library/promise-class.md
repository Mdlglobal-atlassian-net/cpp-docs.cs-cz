---
title: Promise – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- future/std::promise
- future/std::promise::promise
- future/std::promise::get_future
- future/std::promise::set_exception
- future/std::promise::set_exception_at_thread_exit
- future/std::promise::set_value
- future/std::promise::set_value_at_thread_exit
- future/std::promise::swap
dev_langs:
- C++
ms.assetid: 2931558c-d94a-4ba1-ac4f-20bf7b6e23f9
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::promise [C++]
- std::promise [C++], promise
- std::promise [C++], get_future
- std::promise [C++], set_exception
- std::promise [C++], set_exception_at_thread_exit
- std::promise [C++], set_value
- std::promise [C++], set_value_at_thread_exit
- std::promise [C++], swap
ms.workload:
- cplusplus
ms.openlocfilehash: 8a1ddfd30a1e061426f0a19ac1118aa5ade1de17
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958550"
---
# <a name="promise-class"></a>promise – třída

Popisuje, *asynchronního poskytovatele*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class promise;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Promise](#promise)|Vytvoří `promise` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_future](#get_future)|Vrátí [budoucí](../standard-library/future-class.md) spojené s tímto příslibem.|
|[set_exception](#set_exception)|Atomicky nastaví výsledek této snahy na označení výjimky.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Atomicky nastaví výsledek této snahy na označení výjimky a doručí oznámení pouze po všech místních objektů v aktuálním vlákně nejsou zničeny (obvykle při ukončení podprocesu).|
|[set_value](#set_value)|Atomicky nastaví výsledek této snahy na označení hodnoty.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Atomicky nastaví výsledek této snahy na označení hodnoty a doručí oznámení pouze po všech místních objektů v aktuálním vlákně nejsou zničeny (obvykle při ukončení podprocesu).|
|[Prohození](#swap)|Výměna *přidružený asynchronní stav* tohoto objektu promise za zadaný objekt promise u.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Promise::Operator =](#op_eq)|Přiřazení sdíleného stavu tohoto objektu promise.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`promise`

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<budoucí >

**Namespace:** std

## <a name="get_future"></a>  Promise::get_future –

Vrátí [budoucí](../standard-library/future-class.md) objekt, který má stejný *přidružený asynchronní stav* jako tento příslib.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Poznámky

Pokud objekt promise je prázdný, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má [error_code](../standard-library/error-code-class.md) z `no_state`.

Pokud tato metoda již byla volána pro objekt promise, který má stejný přidružený asynchronní stav, vyvolá metoda `future_error` , který má `error_code` z `future_already_retrieved`.

## <a name="op_eq"></a>  Promise::Operator =

Převody *přidružený asynchronní stav* ze zadaného `promise` objektu.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Další* A `promise` objektu.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Tento operátor přenese přidružený asynchronní stav z *jiných*. Po předání *jiných* je *prázdný*.

## <a name="promise"></a>  Promise::Promise – konstruktor

Vytvoří `promise` objektu.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Al* Přidělovač paměti. Zobrazit [ \<alokátorů >](../standard-library/allocators-header.md) Další informace.

*Další* A `promise` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor zkonstruuje *prázdný* `promise` objektu.

Druhý konstruktor vytvoří prázdnou `promise` a použije *Al* pro přidělení paměti.

Třetí konstruktor vytvoří `promise` objektu a přenese přidružený asynchronní stav z *jiných*a nechá *jiných* prázdný.

## <a name="set_exception"></a>  Promise::set_exception –

Atomicky ukládá výjimku jako výsledek tohoto `promise` objekt a nastaví *přidružený asynchronní stav* k *připravené*.

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

*Výhradní* [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) touto metodou, která je uložena jako výsledek výjimky.

### <a name="remarks"></a>Poznámky

Pokud `promise` objekt nemá žádný přidružený asynchronní stav, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód chyby `no_state`.

Pokud `set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value), nebo [set_value_at_thread_exit](#set_value_at_thread_exit) již byly volány pro `promise` objekt, který má stejný připojený asynchronní stav, tato metoda vyvolá `future_error` , který má kód chyby `promise_already_satisfied`.

V důsledku této metody budou odblokována veškerá vlákna, která jsou blokována v přidruženém asynchronním stavu.

## <a name="set_exception_at_thread_exit"></a>  Promise::set_exception_at_thread_exit –

Atomicky nastaví výsledek této `promise` na označení výjimky a doručí oznámení pouze po všech místních objektů v aktuálním vlákně zničení (obvykle při ukončení podprocesu).

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

*Výhradní* [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) touto metodou, která je uložena jako výsledek výjimky.

### <a name="remarks"></a>Poznámky

Pokud objekt promise nemá žádný *přidružený asynchronní stav*, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód chyby `no_state`.

Pokud [set_exception](#set_exception), `set_exception_at_thread_exit`, [set_value](#set_value), nebo [set_value_at_thread_exit](#set_value_at_thread_exit) již byly volány pro `promise` objekt, který má stejný přidružený asynchronní stav, tato metoda vyvolá výjimku `future_error` , který má kód chyby `promise_already_satisfied`.

Rozdíl od [set_exception](#set_exception), tato metoda nenastaví přidružený asynchronní stav na Připraveno, dokud všechny místní objekty v aktuálním vlákně nejsou zničeny. Vlákna, která jsou blokována v přidruženém asynchronním stavu obvykle nejsou odblokovány, dokud aktuální vlákno neskončí.

## <a name="set_value"></a>  Promise::set_value –

Atomicky ukládá hodnotu jako výsledek tohoto `promise` objekt a nastaví *přidružený asynchronní stav* k *připravené*.

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>Parametry

*Val* hodnota, která má být uložena jako výsledek.

### <a name="remarks"></a>Poznámky

Pokud `promise` objekt nemá žádný přidružený asynchronní stav, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód chyby `no_state`.

Pokud [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value`, nebo [set_value_at_thread_exit](#set_value_at_thread_exit) již byly volány pro `promise` objektu který má stejný přidružený asynchronní stav, tato metoda vyvolá `future_error` , který má kód chyby `promise_already_satisfied`.

V důsledku této metody budou odblokována veškerá vlákna, která jsou blokována v přidruženém asynchronním stavu.

První metoda vyvolá také jakoukoliv výjimku, která je vyvolána, když *Val* zkopírována do přidruženého asynchronní stavu. V takovém případě není přidružený asynchronní stav nastaven na hodnotu Připraveno.

Druhá metoda vyvolá také jakoukoliv výjimku, která je vyvolána, když *Val* je přesunuta do přidruženého asynchronní stavu. V takovém případě není přidružený asynchronní stav nastaven na hodnotu Připraveno.

Pro částečnou specializaci `promise<Ty&>`, uložené hodnoty je výsledkem odkaz na *Val*.

Pro specializaci `promise<void>`, neexistuje žádná uložená hodnota.

## <a name="set_value_at_thread_exit"></a>  Promise::set_value_at_thread_exit –

Atomicky ukládá hodnotu jako výsledek tohoto `promise` objektu.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>Parametry

*Val* hodnota, která má být uložena jako výsledek.

### <a name="remarks"></a>Poznámky

Pokud objekt promise nemá žádný *přidružený asynchronní stav*, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód chyby `no_state`.

Pokud [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value), nebo `set_value_at_thread_exit` již byly volány pro `promise` objekt, který má stejný přidružený asynchronní stav, tato metoda vyvolá výjimku `future_error` , který má kód chyby `promise_already_satisfied`.

Rozdíl od `set_value`, není přidružený asynchronní stav nastaven na Připraveno, dokud všechny místní objekty v aktuálním vlákně nejsou zničeny. Vlákna, která jsou blokována v přidruženém asynchronním stavu obvykle nejsou odblokovány, dokud aktuální vlákno neskončí.

První metoda vyvolá také jakoukoliv výjimku, která je vyvolána, když *Val* zkopírována do přidruženého asynchronní stavu.

Druhá metoda vyvolá také jakoukoliv výjimku, která je vyvolána, když *Val* je přesunuta do přidruženého asynchronní stavu.

Pro částečnou specializaci `promise<Ty&>`, je uložená hodnota je v podstatě odkaz na *Val*.

Pro specializaci `promise<void>`, neexistuje žádná uložená hodnota.

## <a name="swap"></a>  Promise::swap –

Výměna *přidružený asynchronní stav* tohoto objektu promise za zadaný objekt.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Další* A `promise` objektu.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
