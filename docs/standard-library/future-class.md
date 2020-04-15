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
ms.openlocfilehash: e71c750ddeb198faa3ae9c5960b2668c376241ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370704"
---
# <a name="future-class"></a>future – třída

Popisuje *asynchronní návratový objekt*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>Poznámky

Každý standardní *asynchronní zprostředkovatel* vrátí objekt, jehož typ je vytvoření instance této šablony. Objekt `future` poskytuje jediný přístup k asynchronnímu zprostředkovateli, ke kterému je přidružen. Pokud potřebujete více asynchronních návratových objektů, které jsou přidruženy ke `future` stejnému asynchronnímu zprostředkovateli, zkopírujte objekt do [shared_future](../standard-library/shared-future-class.md) objektu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Budoucnosti](#future)|Vytvoří `future` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[get](#get)|Načte výsledek, který je uložen v přidruženém asynchronním stavu.|
|[sdílet](#share)|Převede objekt na `shared_future`.|
|[Platný](#valid)|Určuje, zda objekt není prázdný.|
|[Počkej](#wait)|Blokuje aktuální vlákno, dokud není připraven přidružený asynchronní stav.|
|[wait_for](#wait_for)|Blokuje, dokud není přidružený asynchronní stav připraven nebo dokud neuplyne zadaný čas.|
|[wait_until](#wait_until)|Blokuje, dokud není připraven přidružený asynchronní stav nebo dokud není zadán zadaný bod v čase.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[budoucnost::operátor=](#op_eq)|Přenese přidružený asynchronní stav ze zadaného objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<budoucí>

**Obor názvů:** std

## <a name="futurefuture-constructor"></a><a name="future"></a>budoucnost::budoucí konstruktor

Vytvoří `future` objekt.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Další*\
Objekt. `future`

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří `future` objekt, který nemá žádný přidružený asynchronní stav.

Druhý konstruktor vytvoří `future` objekt a přenese přidružený asynchronní stav z *jiného*. *Ostatní* již nemá přidružený asynchronní stav.

## <a name="futureget"></a><a name="get"></a>budoucnost::získat

Načte výsledek, který je uložen v přidruženém asynchronním stavu.

```cpp
Ty get();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je výsledek výjimkou, metoda ji znovu vyvolá. V opačném případě je vrácen výsledek.

### <a name="remarks"></a>Poznámky

Před načtením výsledku tato metoda blokuje aktuální vlákno, dokud není připraven přidružený asynchronní stav.

Pro částečnou `future<Ty&>`specializaci je uložená hodnota účinně odkazem na objekt, který byl předán asynchronnímu zprostředkovateli jako vrácená hodnota.

Protože pro specializaci `future<void>`neexistuje žádná uložená hodnota , vrátí metoda **hodnotu void**.

V jiných specializací metoda přesune jeho vrácená hodnota z uložené hodnoty. Proto volání této metody pouze jednou.

## <a name="futureoperator"></a><a name="op_eq"></a>budoucnost::operátor=

Přenese přidružený asynchronní stav ze zadaného objektu.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt. `future`

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Po přenosu *Right* již nemá přidružený asynchronní stav.

## <a name="futureshare"></a><a name="share"></a>budoucnost::sdílet

Převede objekt na [shared_future](../standard-library/shared-future-class.md) objekt.

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Návratová hodnota

`shared_future(move(*this))`

## <a name="futurevalid"></a><a name="valid"></a>budoucnost::platný

Určuje, zda má objekt přidružený asynchronní stav.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud má objekt přidružený asynchronní stav; jinak **false**.

## <a name="futurewait"></a><a name="wait"></a>budoucnost::čekání

Blokuje aktuální vlákno, dokud není *připraven*přidružený asynchronní stav .

```cpp
void wait() const;
```

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je *připraven* pouze v případě, že jeho asynchronní zprostředkovatel uložil vrácenou hodnotu nebo uložil výjimku.

## <a name="futurewait_for"></a><a name="wait_for"></a>budoucnost::wait_for

Blokuje aktuální vlákno, dokud není *připraven* přidružený asynchronní stav nebo dokud neuplyne zadaný časový interval.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Objekt [chrono::duration,](../standard-library/duration-class.md) který určuje maximální časový interval, který vlákno blokuje.

### <a name="return-value"></a>Návratová hodnota

[Future_status,](../standard-library/future-enums.md#future_status) který označuje důvod pro vrácení.

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je připraven pouze v případě, že jeho asynchronní zprostředkovatel uložil vrácenou hodnotu nebo uložil výjimku.

## <a name="futurewait_until"></a><a name="wait_until"></a>budoucnost::wait_until

Blokuje aktuální vlákno, dokud není přidružený asynchronní stav *připraven* nebo až po zadaném časovém bodu.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*\
[Chrono::time_point](../standard-library/time-point-class.md) objekt, který určuje čas, po kterém může vlákno odblokovat.

### <a name="return-value"></a>Návratová hodnota

[Future_status,](../standard-library/future-enums.md#future_status) který označuje důvod pro vrácení.

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je *připraven* pouze v případě, že jeho asynchronní zprostředkovatel uložil vrácenou hodnotu nebo uložil výjimku.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<budoucí>](../standard-library/future.md)
