---
title: Promise – třída | Microsoft Docs
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
ms.openlocfilehash: ac8508cab7afc7e6614c29b64d78849383f5bc2d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="promise-class"></a>promise – třída

Popisuje, *asynchronní zprostředkovatele*.

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
|[get_future](#get_future)|Vrátí [budoucí](../standard-library/future-class.md) přidružené k této promise.|
|[set_exception](#set_exception)|Atomicky nastaví výsledky této promise udávajících výjimku.|
|[set_exception_at_thread_exit](#set_exception_at_thread_exit)|Atomicky nastaví výsledky této promise udávajících výjimku a doručí oznámení, která byla zničena pouze po všech místní objekty v aktuální vlákno (obvykle při ukončení vlákna).|
|[set_value](#set_value)|Atomicky nastaví výsledky této promise pro zobrazení hodnoty.|
|[set_value_at_thread_exit](#set_value_at_thread_exit)|Atomicky nastaví výsledky této promise pro zobrazení hodnoty a doručí oznámení, která byla zničena pouze po všech místní objekty v aktuální vlákno (obvykle při ukončení vlákna).|
|[Swap](#swap)|Výměnu *přidružené asynchronní stavu* z této promise s třídou promise zadaného objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Promise::Operator =](#op_eq)|Přiřazení sdílený stav tohoto objektu promise.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`promise`

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<budoucí >

**Namespace:** – std

## <a name="get_future"></a>  Promise::get_future –

Vrátí [budoucí](../standard-library/future-class.md) objekt, který má stejné *přidružené asynchronní stavu* jako tento promise.

```cpp
future<Ty> get_future();
```

### <a name="remarks"></a>Poznámky

Pokud objekt promise je prázdná, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) má [error_code](../standard-library/error-code-class.md) z `no_state`.

Pokud tato metoda již byla volána pro promise objekt, který má stejné přidružený stav asynchronní, vyvolá metoda `future_error` má `error_code` z `future_already_retrieved`.

## <a name="op_eq"></a>  Promise::Operator =

Přenosy *přidružené asynchronní stavu* ze zadané `promise` objektu.

```cpp
promise& operator=(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

`Other` A `promise` objektu.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Tento operátor přenáší přidružený stav asynchronní z `Other`. Po předání `Other` je *prázdný*.

## <a name="promise"></a>  Promise::Promise – konstruktor

Vytvoří `promise` objektu.

```cpp
promise();
template <class Alloc>
promise(allocator_arg_t, const Alloc& Al);
promise(promise&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

`Al` Přidělení paměti. V tématu [ \<alokátorů >](../standard-library/allocators-header.md) Další informace.

`Other` A `promise` objektu.

### <a name="remarks"></a>Poznámky

První konstrukce konstruktor *prázdný* `promise` objektu.

Druhý konstruktor vytvoří prázdnou `promise` objekt a používá `Al` pro přidělení paměti.

Třetí konstrukce konstruktor `promise` objektu a přenáší přidružený stav asynchronní z `Other`nebo je opustí `Other` prázdný.

## <a name="set_exception"></a>  Promise::set_exception –

Atomicky ukládá výjimka v důsledku tohoto `promise` objekt a nastaví *přidružené asynchronní stavu* k *připraven*.

```cpp
void set_exception(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

`Exc` [Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) touto metodou, je uložen v důsledku výjimky.

### <a name="remarks"></a>Poznámky

Pokud `promise` objekt nemá žádné přidružené asynchronní stavu, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) s kódem chyby `no_state`.

Pokud `set_exception`, [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value), nebo [set_value_at_thread_exit](#set_value_at_thread_exit) již byla volána pro `promise` objektu, který má stejné přidružené asynchronní stavu, tato metoda vyvolá `future_error` s kódem chyby `promise_already_satisfied`.

V důsledku této metody stát žádné podprocesy, které blokují na přidružený stav asynchronní odblokování.

## <a name="set_exception_at_thread_exit"></a>  Promise::set_exception_at_thread_exit –

Atomicky nastaví výsledek tohoto `promise` udávajících výjimku doručování oznámení pouze po všech místní objekty v aktuální vlákno zničena (obvykle při ukončení vlákna).

```cpp
void set_exception_at_thread_exit(exception_ptr Exc);
```

### <a name="parameters"></a>Parametry

`Exc` [Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) touto metodou, je uložen v důsledku výjimky.

### <a name="remarks"></a>Poznámky

Pokud objekt promise neobsahuje žádné *přidružené asynchronní stavu*, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) s kódem chyby `no_state`.

Pokud [set_exception –](#set_exception), `set_exception_at_thread_exit`, [set_value](#set_value), nebo [set_value_at_thread_exit](#set_value_at_thread_exit) již byla volána pro `promise` objekt, který má stejné přidružený stav asynchronní, tato metoda vyvolá `future_error` s kódem chyby `promise_already_satisfied`.

Rozdíl k [set_exception –](#set_exception), tato metoda nenastaví přidružený stav asynchronní připravte až po všech místní objekty v aktuální vlákno zničena. Obvykle vláken, které blokují na přidružený stav asynchronní nejsou odblokuje, až do konce aktuální vlákno.

## <a name="set_value"></a>  Promise::set_value –

Atomicky ukládá hodnotu jako výsledek tohoto `promise` objekt a nastaví *přidružené asynchronní stavu* k *připraven*.

```cpp
void promise::set_value(const Ty& Val);
void promise::set_value(Ty&& Val);
void promise<Ty&>::set_value(Ty& Val);
void promise<void>::set_value();
```

### <a name="parameters"></a>Parametry

`Val` Hodnota ukládaly jako výsledek.

### <a name="remarks"></a>Poznámky

Pokud `promise` objekt nemá žádné přidružené asynchronní stavu, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) s kódem chyby `no_state`.

Pokud [set_exception –](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), `set_value`, nebo [set_value_at_thread_exit](#set_value_at_thread_exit) již byla volána pro `promise` objektu který má stejné přidružený stav asynchronní, tato metoda vyvolá `future_error` s kódem chyby `promise_already_satisfied`.

V důsledku této metody stát žádné podprocesy, které blokují na přidružený stav asynchronní odblokování.

První metoda také výjimku, když je výjimka `Val` se zkopíruje do přidružený stav asynchronní. V takovém případě není přidružené asynchronní stav nastaven na hodnotu Připraveno.

Druhá metoda také výjimku, když je výjimka `Val` je přesunut do přidružený stav asynchronní. V takovém případě není přidružené asynchronní stav nastaven na hodnotu Připraveno.

Pro částečná specializace `promise<Ty&>`, uložené hodnoty je v platnosti odkaz na `Val`.

Pro specializace `promise<void>`, neexistuje žádná hodnota uložené.

## <a name="set_value_at_thread_exit"></a>  Promise::set_value_at_thread_exit –

Atomicky ukládá hodnotu jako výsledek tohoto `promise` objektu.

```cpp
void promise::set_value_at_thread_exit(const Ty& Val);
void promise::set_value_at_thread_exit(Ty&& Val);
void promise<Ty&>::set_value_at_thread_exit(Ty& Val);
void promise<void>::set_value_at_thread_exit();
```

### <a name="parameters"></a>Parametry

`Val` Hodnota ukládaly jako výsledek.

### <a name="remarks"></a>Poznámky

Pokud objekt promise neobsahuje žádné *přidružené asynchronní stavu*, tato metoda vyvolá [future_error](../standard-library/future-error-class.md) s kódem chyby `no_state`.

Pokud [set_exception –](#set_exception), [set_exception_at_thread_exit](#set_exception_at_thread_exit), [set_value](#set_value), nebo `set_value_at_thread_exit` již byla volána pro `promise` objekt, který má stejné přidružený stav asynchronní, tato metoda vyvolá `future_error` s kódem chyby `promise_already_satisfied`.

Rozdíl k `set_value`, přidružené asynchronní stav není nastavený připravte až po všech místní objekty v aktuální vlákno zničena. Obvykle vláken, které blokují na přidružený stav asynchronní nejsou odblokuje, až do konce aktuální vlákno.

První metoda také výjimku, když je výjimka `Val` se zkopíruje do přidružený stav asynchronní.

Druhá metoda také výjimku, když je výjimka `Val` je přesunut do přidružený stav asynchronní.

Pro částečná specializace `promise<Ty&>`, uložené hodnoty je efektivně odkaz na `Val`.

Pro specializace `promise<void>`, neexistuje žádná hodnota uložené.

## <a name="swap"></a>  Promise::swap –

Výměnu *přidružené asynchronní stavu* tohoto objektu promise se u zadaného objektu.

```cpp
void swap(promise& Other) noexcept;
```

### <a name="parameters"></a>Parametry

`Other` A `promise` objektu.

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
