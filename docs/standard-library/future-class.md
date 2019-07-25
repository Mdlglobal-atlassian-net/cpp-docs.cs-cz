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
ms.openlocfilehash: 1519fa105f2cd73c1165bb30264828aa987fbd35
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458446"
---
# <a name="future-class"></a>future – třída

Popisuje *asynchronní návratový objekt*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>Poznámky

Každý standardní *asynchronní zprostředkovatel* vrátí objekt, jehož typ je instancí této šablony. `future` Objekt poskytuje přístup pouze k asynchronnímu zprostředkovateli, ke kterému je přidružen. Pokud potřebujete více asynchronních návratových objektů, které jsou přidruženy ke stejnému asynchronnímu `future` zprostředkovateli, zkopírujte objekt do objektu [shared_future](../standard-library/shared-future-class.md) .

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[pozdější](#future)|`future` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[get](#get)|Načte výsledek, který je uložen v přidruženém asynchronním stavu.|
|[předem](#share)|Převede objekt na `shared_future`.|
|[platný](#valid)|Určuje, zda objekt není prázdný.|
|[Počkej](#wait)|Zablokuje aktuální vlákno, dokud není přidružený asynchronní stav připraven.|
|[wait_for](#wait_for)|Blokuje, dokud je přidružený asynchronní stav připraven nebo dokud neuplyne zadaný čas.|
|[wait_until](#wait_until)|Blokuje, dokud je přidružený asynchronní stav připraven nebo dokud není stanovený bod v čase.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[Future:: operator =](#op_eq)|Převede přidružený asynchronní stav ze zadaného objektu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<budoucí >

**Obor názvů:** std

## <a name="future"></a>Future:: Future – konstruktor

`future` Vytvoří objekt.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiná*\
`future` Objekt.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří `future` objekt, který nemá přidružený asynchronní stav.

Druhý konstruktor vytvoří `future` objekt a převede přidružený asynchronní stav z *jiné*. *Další* už nemá přidružený asynchronní stav.

## <a name="get"></a>budoucnost:: Get

Načte výsledek, který je uložen v přidruženém asynchronním stavu.

```cpp
Ty get();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je výsledkem výjimka, metoda ji znovu vyvolá. V opačném případě se vrátí výsledek.

### <a name="remarks"></a>Poznámky

Před tím, než bude načten výsledek, tato metoda zablokuje aktuální vlákno, dokud není přidružený asynchronní stav připraven.

Pro částečnou specializaci `future<Ty&>`je uložená hodnota efektivně odkaz na objekt, který byl předán asynchronnímu zprostředkovateli jako návratová hodnota.

Vzhledem k tomu, že pro specializaci `future<void>`neexistuje uložená hodnota, vrátí metoda hodnotu **void**.

V jiných specializacích metoda přesune svou návratovou hodnotu z uložené hodnoty. Proto volejte tuto metodu pouze jednou.

## <a name="op_eq"></a>Future:: operator =

Převede přidružený asynchronní stav ze zadaného objektu.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
`future` Objekt.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Po převodu už nemá  k dispozici přidružený asynchronní stav.

## <a name="share"></a>budoucnost:: Share

Převede objekt na objekt [shared_future](../standard-library/shared-future-class.md) .

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Návratová hodnota

`shared_future(move(*this))`

## <a name="valid"></a>budoucí:: platné

Určuje, zda má objekt přidružený asynchronní stav.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud má objekt přidružený asynchronní stav; v opačném případě **false**.

## <a name="wait"></a>budoucnost:: wait

Zablokuje aktuální vlákno, dokud není přidružený asynchronní stav *připraven*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je *připraven* pouze v případě, že jeho asynchronní zprostředkovatel uložil návratovou hodnotu nebo uložila výjimku.

## <a name="wait_for"></a>budoucnost:: wait_for

Zablokuje aktuální vlákno, dokud není přidružený asynchronní stav *připraven* nebo dokud neuplyne zadaný časový interval.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Objekt [chrono::d uration](../standard-library/duration-class.md) , který určuje maximální časový interval, který vlákno blokuje.

### <a name="return-value"></a>Návratová hodnota

[Future_status](../standard-library/future-enums.md#future_status) , který označuje důvod vrácení.

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je připraven pouze v případě, že jeho asynchronní zprostředkovatel uložil návratovou hodnotu nebo uložila výjimku.

## <a name="wait_until"></a>budoucnost:: wait_until

Zablokuje aktuální vlákno, dokud není přidružený asynchronní stav *připraven* nebo dokud není za zadaným časovým bodem.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Objekt [chrono:: time_point](../standard-library/time-point-class.md) , který určuje čas, po jehož uplynutí může vlákno odblokovat.

### <a name="return-value"></a>Návratová hodnota

[Future_status](../standard-library/future-enums.md#future_status) , který označuje důvod vrácení.

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je *připraven* pouze v případě, že jeho asynchronní zprostředkovatel uložil návratovou hodnotu nebo uložila výjimku.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<budoucí >](../standard-library/future.md)
