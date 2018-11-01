---
title: future – třída
ms.date: 11/04/2016
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.openlocfilehash: 9ca18e62038d93a50b592868f71223962a22857d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551876"
---
# <a name="future-class"></a>future – třída

Popisuje, *asynchronní vrácený objekt*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>Poznámky

Jednotlivé normy *asynchronního poskytovatele* vrátí objekt, jehož typ je instance této šablony. A `future` objekt poskytuje přístup jenom k asynchronního poskytovatele, který je přidružený. Pokud potřebujete více asynchronních návratových objektů, které jsou přidruženy stejném asynchronního poskytovatele, zkopírujte `future` do objektu [shared_future –](../standard-library/shared-future-class.md) objektu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[budoucí](#future)|Vytvoří `future` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get](#get)|Získá výsledek, který je uložený v přidruženém asynchronním stavu.|
|[sdílené složky](#share)|Převede objekt, který má `shared_future`.|
|[platný](#valid)|Určuje, zda objekt není prázdný.|
|[Počkej](#wait)|Blokuje aktuální vlákno, dokud není přidružený asynchronní stav připraven.|
|[wait_for](#wait_for)|Blokuje až do přidruženého asynchronní stavu připravený nebo dokud určený čas uplynul.|
|[wait_until](#wait_until)|Blokuje až do přidruženého asynchronní stavu je připravený, nebo dokud určitému bodu v čase.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Future::Operator =](#op_eq)|Přenese přidružený asynchronní stav ze zadaného objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<budoucí >

**Namespace:** std

## <a name="future"></a>  Future::Future – konstruktor

Vytvoří `future` objektu.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiné*<br/>
A `future` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor zkonstruuje `future` objekt, který nemá žádný přidružený asynchronní stav.

Druhý konstruktor vytvoří `future` objektu a přenese přidružený asynchronní stav z *jiných*. *Další* již nemá přidružený asynchronní stav.

## <a name="get"></a>  Future::Get –

Získá výsledek, který je uložený v přidruženém asynchronním stavu.

```cpp
Ty get();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je výsledkem výjimka, znovu vyvolá metodu ho. Jinak se vrátí výsledek.

### <a name="remarks"></a>Poznámky

Předtím, než načte výsledky, tato metoda blokuje aktuální vlákno, dokud není přidružený asynchronní stav připraven.

Pro částečnou specializaci `future<Ty&>`, je uložená hodnota je v podstatě odkaz na objekt, který byl předán asynchronního poskytovatele jako návratovou hodnotu.

Protože neexistuje žádná uložená hodnota pro specializaci `future<void>`, vrátí metoda **void**.

Metoda v ostatní specializace přesune jeho návratovou hodnotu od uložené hodnoty. Proto pouze jednou volejte tuto metodu.

## <a name="op_eq"></a>  Future::Operator =

Přenese přidružený asynchronní stav ze zadaného objektu.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
A `future` objektu.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Po předání *vpravo* již nemá přidružený asynchronní stav.

## <a name="share"></a>  Future::share –

Převede objekt, který má [shared_future –](../standard-library/shared-future-class.md) objektu.

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Návratová hodnota

`shared_future(move(*this))`

## <a name="valid"></a>  Future::valid –

Určuje, zda má objekt přidružený asynchronní stav.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud objekt má přidružený asynchronní stav; v opačném případě **false**.

## <a name="wait"></a>  Future::wait –

Blokuje aktuální vlákno, dokud není přidružený asynchronní stav *připravené*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Poznámky

Je přidružený asynchronní stav *připravené* pouze v případě, že jeho asynchronního poskytovatele má uložené návratovou hodnotu nebo uložené výjimku.

## <a name="wait_for"></a>  Future::wait_for –

Blokuje aktuální vlákno, dokud není přidružený asynchronní stav *připravené* nebo až do uplynutí zadaného časového intervalu.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*<br/>
A [chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální časový interval, který vlákno blokováno.

### <a name="return-value"></a>Návratová hodnota

A [future_status –](../standard-library/future-enums.md#future_status) , který označuje důvod pro vrácení.

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav připravený, pouze v případě, že jeho asynchronního poskytovatele má uložené návratovou hodnotu nebo uložené výjimku.

## <a name="wait_until"></a>  Future::wait_until –

Blokuje aktuální vlákno, dokud není přidružený asynchronní stav *připravené* nebo až po zadaný časový bod.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*<br/>
A [chrono::time_point](../standard-library/time-point-class.md) objekt, který určuje dobu, po jejímž uplynutí může odblokovat vlákna.

### <a name="return-value"></a>Návratová hodnota

A [future_status –](../standard-library/future-enums.md#future_status) , který označuje důvod pro vrácení.

### <a name="remarks"></a>Poznámky

Je přidružený asynchronní stav *připravené* pouze v případě, že jeho asynchronního poskytovatele má uložené návratovou hodnotu nebo uložené výjimku.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<Další >](../standard-library/future.md)<br/>
