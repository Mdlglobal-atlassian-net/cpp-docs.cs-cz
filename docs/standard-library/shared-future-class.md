---
title: shared_future – třída
ms.date: 11/04/2016
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.openlocfilehash: 3b08a1341ed450dd5d5cee93cdfcbab57f8d6760
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450496"
---
# <a name="sharedfuture-class"></a>shared_future – třída

Popisuje *asynchronní návratový objekt*. Na rozdíl od [budoucího](../standard-library/future-class.md) objektu může být *asynchronní zprostředkovatel* spojen s `shared_future` libovolným počtem objektů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Poznámky

Nevolejte žádné jiné metody `valid`než, `operator=` `shared_future` a destruktor na objektu, který je *prázdný*.

`shared_future`objekty nejsou synchronizovány. Volání metod u stejného objektu z více vláken zavádí datový závod, který má nepředvídatelné výsledky.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[shared_future](#shared_future)|`shared_future` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[get](#get)|Načte výsledek, který je uložen v *přidruženém asynchronním stavu*.|
|[platný](#valid)|Určuje, zda objekt není prázdný.|
|[Počkej](#wait)|Zablokuje aktuální vlákno, dokud není přidružený asynchronní stav připraven.|
|[wait_for](#wait_for)|Blokuje, dokud je přidružený asynchronní stav připraven nebo dokud neuplyne zadaný čas.|
|[wait_until](#wait_until)|Blokuje, dokud je přidružený asynchronní stav připraven nebo dokud není stanovený bod v čase.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[shared_future::operator=](#op_eq)|Přiřadí nový přidružený asynchronní stav.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<budoucí >

**Obor názvů:** std

## <a name="get"></a>shared_future:: Get

Načte výsledek, který je uložen v *přidruženém asynchronním stavu*.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Poznámky

Pokud je výsledkem výjimka, metoda ji znovu vyvolá. V opačném případě se vrátí výsledek.

Před tím, než bude načten výsledek, tato metoda zablokuje aktuální vlákno, dokud není přidružený asynchronní stav připraven.

Pro částečnou specializaci `shared_future<Ty&>`je uložená hodnota efektivně odkaz na objekt, který byl předán *asynchronnímu zprostředkovateli* jako návratová hodnota.

Vzhledem k tomu, že pro specializaci `shared_future<void>`neexistuje uložená hodnota, vrátí metoda hodnotu **void**.

## <a name="op_eq"></a>shared_future:: operator =

Převede *přidružený asynchronní stav* ze zadaného objektu.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
A `shared_future` objektu.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Pro první operátor už *práva* k asynchronnímu stavu po operaci nemá přidružený asynchronní stav.

Pro druhou metodu *pravá* udržuje svůj přidružený asynchronní stav.

## <a name="shared_future"></a>shared_future:: shared_future – konstruktor

`shared_future` Vytvoří objekt.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
[Budoucí](../standard-library/future-class.md) nebo `shared_future` objekt.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří `shared_future` objekt, který nemá *přidružený asynchronní stav*.

Druhý a třetí konstruktory vytvoří `shared_future` objekt a přenesí přidružený asynchronní stav *zprava*. *Právo* již nemá přidružený asynchronní stav.

Čtvrtý konstruktor vytvoří `shared_future` objekt, který má stejný přidružený asynchronní stav jako *pravý*.

## <a name="valid"></a>shared_future:: platný

Určuje, zda má objekt *přidružený asynchronní stav*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud má objekt přidružený asynchronní stav; v opačném případě **false**.

## <a name="wait"></a>shared_future:: wait

Zablokuje aktuální vlákno, dokud není *přidružený asynchronní stav* *připraven*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je připraven pouze v případě, že jeho asynchronní zprostředkovatel uložil návratovou hodnotu nebo uložila výjimku.

## <a name="wait_for"></a>shared_future::wait_for

Zablokuje aktuální vlákno, dokud není přidružený asynchronní stav *připraven* nebo dokud neuplyne zadaný čas.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Objekt [chrono::d uration](../standard-library/duration-class.md) , který určuje maximální časový interval, který vlákno blokuje.

### <a name="return-value"></a>Návratová hodnota

[Future_status](../standard-library/future-enums.md#future_status) , který označuje důvod vrácení.

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je *připraven* pouze v případě, že jeho asynchronní zprostředkovatel uložil návratovou hodnotu nebo uložila výjimku.

## <a name="wait_until"></a>shared_future::wait_until

Zablokuje aktuální vlákno, dokud není přidružený asynchronní stav *připraven* nebo dokud není za zadaným časovým bodem.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Objekt [chrono:: time_point](../standard-library/time-point-class.md) , který určuje čas, po jehož uplynutí může vlákno odblokovat.

### <a name="return-value"></a>Návratová hodnota

[Future_status](../standard-library/future-enums.md#future_status) , který označuje důvod vrácení.

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je připraven pouze v případě, že jeho asynchronní zprostředkovatel uložil návratovou hodnotu nebo uložila výjimku.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<budoucí >](../standard-library/future.md)
