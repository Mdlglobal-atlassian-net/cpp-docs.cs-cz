---
title: shared_future – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
dev_langs:
- C++
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: 2ac125b068de5111a2b98800956c12a0c979737f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859661"
---
# <a name="sharedfuture-class"></a>shared_future – třída

Popisuje, *asynchronní návratové objekt*. Rozdíl s [budoucí](../standard-library/future-class.md) objektu, *asynchronní zprostředkovatele* lze přidružit libovolný počet `shared_future` objekty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Poznámky

Nevolejte žádné metody jiné než `valid`, `operator=`a destruktor na `shared_future` objekt to je *prázdný*.

`shared_future` objekty nejsou synchronizovány. Volání metody na stejný objekt z více vláken představuje soupeření dat, který má vést k neočekávaným výsledkům.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[shared_future](#shared_future)|Vytvoří `shared_future` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get](#get)|Načte výsledek, který je uložen v *přidružené asynchronní stavu*.|
|[Platný](#valid)|Určuje, zda objekt není prázdný.|
|[Počkej](#wait)|Aktuální vlákno zablokuje, dokud přidružený stav asynchronní je připraven.|
|[wait_for](#wait_for)|Bloky dokud přidružený stav asynchronní je připraven nebo dokud určený čas uplynul.|
|[wait_until](#wait_until)|Bloky dokud přidružený stav asynchronní je připravená, nebo dokud se zadaný bod v čase.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[shared_future::operator=](#op_eq)|Přiřadí nový asynchronní přidružený stav.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<budoucí >

**Namespace:** – std

## <a name="get"></a>  shared_future::Get –

Načte výsledek, který je uložen v *přidružené asynchronní stavu*.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Poznámky

Pokud je výsledek výjimku, znovu vyvolá metodu ho. Jinak se vrátí výsledek.

Předtím, než se načte výsledek, tato metoda blokuje aktuální vlákno, dokud přidružený stav asynchronní je připraven.

Pro částečná specializace `shared_future<Ty&>`, uložené hodnoty je efektivně odkaz na objekt, který byl předán *asynchronní zprostředkovatele* jako návratová hodnota.

Vzhledem k tomu, že neexistuje žádná hodnota uložené pro specializace `shared_future<void>`, vrátí metoda `void`.

## <a name="op_eq"></a>  shared_future::Operator =

Přenosy *přidružené asynchronní stavu* ze zadaného objektu.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

`Right` A `shared_future` objektu.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Pro první operátor `Right` již nemá přidružený asynchronní stát po operaci.

Pro metodu druhý `Right` udržuje jeho přidružený stav asynchronní.

## <a name="shared_future"></a>  shared_future::shared_future – konstruktor

Vytvoří `shared_future` objektu.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

`Right` A [budoucí](../standard-library/future-class.md) nebo `shared_future` objektu.

### <a name="remarks"></a>Poznámky

První konstrukce konstruktor `shared_future` objekt, který neobsahuje žádné *přidružené asynchronní stavu*.

Vytvořit druhý a třetí konstruktory `shared_future` objektu a přenos přidružený stav asynchronní z `Right`. `Right` již nemá přidružený asynchronní stát.

Čtvrtý konstrukce konstruktor `shared_future` objekt, který má stejné přidružené asynchronní stavu jako `Right`.

## <a name="valid"></a>  shared_future::valid –

Určuje, zda je objekt *přidružené asynchronní stavu*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud objekt má přidružený stav asynchronní; v opačném `false`.

## <a name="wait"></a>  shared_future::wait –

Blokuje aktuální vlákno, dokud *přidružené asynchronní stavu* je *připraven*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stát je připraven jenom v případě jeho asynchronní zprostředkovatelem má uložené návratovou hodnotu nebo uložené výjimku.

## <a name="wait_for"></a>  shared_future::wait_for –

Blokuje aktuální vlákno, dokud je přidružený stav asynchronní *připraven* nebo dokud uplynutí zadané doby.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

`Rel_time` A [chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální časový interval, která blokuje přístup z více vláken.

### <a name="return-value"></a>Návratová hodnota

A [future_status](../standard-library/future-enums.md#future_status) určující důvod pro vrácení.

### <a name="remarks"></a>Poznámky

Je k dispozici přidružený stav asynchronní *připraven* jenom v případě jeho asynchronní zprostředkovatelem má uložené návratovou hodnotu nebo uložené výjimku.

## <a name="wait_until"></a>  shared_future::wait_until –

Blokuje aktuální vlákno, dokud je přidružený stav asynchronní *připraven* nebo dokud nebude po zadaném časovém bodě.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

`Abs_time` A [chrono::time_point](../standard-library/time-point-class.md) objekt, který určuje dobu, po jejímž uplynutí vlákno odblokovat.

### <a name="return-value"></a>Návratová hodnota

A [future_status](../standard-library/future-enums.md#future_status) určující důvod pro vrácení.

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stát je připraven jenom v případě jeho asynchronní zprostředkovatelem má uložené návratovou hodnotu nebo uložené výjimku.

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<budoucí >](../standard-library/future.md)<br/>
