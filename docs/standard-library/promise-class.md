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
ms.openlocfilehash: 560339dee5b13ddc13ff2f8af8283ea8615d804a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458363"
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

|Name|Popis|
|----------|-----------------|
|[slíbit](#promise)|`promise` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[get_future](#get_future)|Vrátí [budoucí](../standard-library/future-class.md) přidružení k tomuto příslibu.|
|[set_exception](#set_exception)|Atomicky nastaví výsledek tohoto příslibu na indikaci výjimky.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Atomicky nastaví výsledek této snahy na označení výjimky a doručí oznámení až po zničení všech místních objektů v aktuálním podprocesu (obvykle při ukončení vlákna).|
|[set_value](#set_value)|Atomicky nastaví výsledek tohoto Promise na označení hodnoty.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Atomicky nastaví výsledek této snahy na označení hodnoty a doručí oznámení až po zničení všech místních objektů v aktuálním podprocesu (obvykle při ukončení vlákna).|
|[swap](#swap)|Vyměňuje *přidružený asynchronní stav* tohoto Promise se zadaným objektem Promise.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[Promise:: operator =](#op_eq)|Přiřazení sdíleného stavu tohoto objektu Promise.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

*slíbit*

## <a name="requirements"></a>Požadavky

**Hlavička:** \<budoucí >

**Obor názvů:** std

## <a name="get_future"></a>Promise:: get_future

Vrátí [budoucí](../standard-library/future-class.md) objekt, který má stejný *přidružený asynchronní stav* jako tento příslib.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt Promise prázdný, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má [error_code](../standard-library/error-code-class.md) z `no_state`.

Pokud již byla tato metoda volána pro objekt Promise, který má stejný přidružený asynchronní stav, metoda vyvolá výjimku `future_error` , která `error_code` má `future_already_retrieved`.

## <a name="op_eq"></a>Promise:: operator =

Převede *přidružený asynchronní stav* ze zadaného `promise` objektu.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiná*\
A `promise` objektu.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Tento operátor převede přidružený asynchronní stav z *jiné*. Po převodu je *jiná* *prázdná*.

## <a name="promise"></a>Promise::p konstruktor romise

`promise` Vytvoří objekt.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*VŠ*\
Přidělování paměti. Další informace najdete v tématu [ \<přidělování >](../standard-library/allocators-header.md) .

*Jiná*\
`promise` Objekt.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří *prázdný* `promise` objekt.

Druhý konstruktor vytvoří prázdný `promise` objekt a používá *Al* pro přidělení paměti.

Třetí konstruktor vytvoří `promise` objekt a převede přidružený asynchronní stav z *jiného*a opustí *jiné* prázdné.

## <a name="set_exception"></a>Promise:: set_exception

Atomicky ukládá výjimku jako výsledek tohoto `promise` objektu a nastaví *přidružený asynchronní stav* na *připraven*.

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

*EXC*\
[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) , který je uložen touto metodou jako výsledek výjimky.

### <a name="remarks"></a>Poznámky

Pokud objekt nemá přidružený asynchronní stav, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód `no_state`chyby. `promise`

IF `set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_Value](#set_value)nebo `promise` [set_value_at_thread_exit](#set_value_at_thread_exit) již byly volány pro objekt, který má stejný přidružený asynchronní stav, tato metoda vyvolá `future_error`obsahující kód `promise_already_satisfied`chyby.

V důsledku této metody dojde k odblokování všech vláken, která jsou blokovaná v přidruženém asynchronním stavu.

## <a name="set_exception_at_thread_exit"></a>Promise:: set_exception_at_thread_exit

Atomicky nastaví výsledek této `promise` hodnoty, aby označoval výjimku, doručení oznámení až po zničení všech místních objektů v aktuálním podprocesu (obvykle při ukončení podprocesu).

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

*EXC*\
[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) , který je uložen touto metodou jako výsledek výjimky.

### <a name="remarks"></a>Poznámky

Pokud objekt Promise nemá žádný *přidružený asynchronní stav*, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód `no_state`chyby.

Pokud [set_exception](#set_exception), `set_exception_at_thread_exit`, [set_Value](#set_value)nebo `promise` [set_value_at_thread_exit](#set_value_at_thread_exit) již byly volány pro objekt, který `future_error` má stejný přidružený asynchronní stav, tato metoda vyvolá výjimku, která obsahuje chybu. `promise_already_satisfied`kód.

Na rozdíl od [set_exception](#set_exception)Tato metoda nenastaví přidružený asynchronní stav na připraveno, dokud všechny místní objekty vlákna v aktuálním vlákně nejsou zničeny. Vlákna, která jsou blokována v přidruženém asynchronním stavu, jsou obvykle odblokována, dokud se aktuální vlákno neukončí.

## <a name="set_value"></a>Promise:: set_Value

Atomicky ukládá hodnotu jako výsledek tohoto `promise` objektu a nastaví *přidružený asynchronní stav* na *připraven*.

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>Parametry

*Počítává*\
Hodnota, která má být uložena jako výsledek.

### <a name="remarks"></a>Poznámky

Pokud objekt nemá přidružený asynchronní stav, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód `no_state`chyby. `promise`

Pokud [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value`nebo `promise` [set_value_at_thread_exit](#set_value_at_thread_exit) již byly volány pro objekt, který má stejný přidružený asynchronní stav, tato metoda vyvolá `future_error`obsahující kód `promise_already_satisfied`chyby.

V důsledku této metody dojde k odblokování všech vláken, která jsou blokovaná v přidruženém asynchronním stavu.

První metoda vyvolá také jakoukoliv výjimku, která je vyvolána, když je hodnota *Val* zkopírována do přidruženého asynchronního stavu. V takovém případě není přidružený asynchronní stav nastaven na připraveno.

Druhá metoda vyvolá také jakoukoliv výjimku, která je vyvolána, když je hodnota *Val* přesunuta do přidruženého asynchronního stavu. V takovém případě není přidružený asynchronní stav nastaven na připraveno.

Pro částečnou specializaci `promise<Ty&>`je uložená hodnota v platnosti odkazem na hodnotu *Val*.

Pro specializaci `promise<void>`neexistuje žádná uložená hodnota.

## <a name="set_value_at_thread_exit"></a>Promise:: set_value_at_thread_exit

Atomicky ukládá hodnotu jako výsledek tohoto `promise` objektu.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>Parametry

*Počítává*\
Hodnota, která má být uložena jako výsledek.

### <a name="remarks"></a>Poznámky

Pokud objekt Promise nemá žádný *přidružený asynchronní stav*, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) , který má kód `no_state`chyby.

Pokud [set_exception](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_Value](#set_value)nebo `set_value_at_thread_exit` již bylo voláno pro `promise` objekt, který `future_error` má stejný přidružený asynchronní stav, tato metoda vyvolá výjimku, která má kód `promise_already_satisfied`chyby.

Na rozdíl od `set_value`, přidružený asynchronní stav není nastaven na připraveno, dokud všechny místní objekty vlákna v aktuálním vlákně nejsou zničeny. Vlákna, která jsou blokována v přidruženém asynchronním stavu, jsou obvykle odblokována, dokud se aktuální vlákno neukončí.

První metoda vyvolá také jakoukoliv výjimku, která je vyvolána, když je hodnota *Val* zkopírována do přidruženého asynchronního stavu.

Druhá metoda vyvolá také jakoukoliv výjimku, která je vyvolána, když je hodnota *Val* přesunuta do přidruženého asynchronního stavu.

Pro částečnou specializaci `promise<Ty&>`je uložená hodnota efektivně odkaz na *Val*.

Pro specializaci `promise<void>`neexistuje žádná uložená hodnota.

## <a name="swap"></a>Promise:: swap

Vyměňuje *přidružený asynchronní stav* tohoto objektu Promise se zadaným objektem.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiná*\
A `promise` objektu.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)
