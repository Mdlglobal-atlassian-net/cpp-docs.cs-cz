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
ms.openlocfilehash: 2280c17c4ce58fe06365c107ad26d646c7ae2d72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412602"
---
# <a name="sharedfuture-class"></a>shared_future – třída

Popisuje, *asynchronní vrácený objekt*. Rozdíl od s [budoucí](../standard-library/future-class.md) objekt, *asynchronního poskytovatele* lze přidružit libovolný počet `shared_future` objekty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Poznámky

Nevolejte jakékoli metody jiné než `valid`, `operator=`a destruktor na `shared_future` objektu, která *prázdný*.

`shared_future` objekty nejsou synchronizovány. Volání metod na stejný objekt z více vláken představuje závodu data, která má nepředvídatelné výsledky.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[shared_future](#shared_future)|Vytvoří `shared_future` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get](#get)|Získá výsledek, který je uložený v *přidružený asynchronní stav*.|
|[platný](#valid)|Určuje, zda objekt není prázdný.|
|[Počkej](#wait)|Blokuje aktuální vlákno, dokud není přidružený asynchronní stav připraven.|
|[wait_for](#wait_for)|Blokuje až do přidruženého asynchronní stavu připravený nebo dokud určený čas uplynul.|
|[wait_until](#wait_until)|Blokuje až do přidruženého asynchronní stavu je připravený, nebo dokud určitému bodu v čase.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[shared_future::operator=](#op_eq)|Přiřadí nové přidružený asynchronní stav.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<budoucí >

**Namespace:** std

## <a name="get"></a>  shared_future::Get –

Získá výsledek, který je uložený v *přidružený asynchronní stav*.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Poznámky

Pokud je výsledkem výjimka, znovu vyvolá metodu ho. Jinak se vrátí výsledek.

Předtím, než načte výsledky, tato metoda blokuje aktuální vlákno, dokud není přidružený asynchronní stav připraven.

Pro částečnou specializaci `shared_future<Ty&>`, je uložená hodnota je v podstatě odkaz na objekt, který byl předán *asynchronního poskytovatele* jako návratovou hodnotu.

Protože neexistuje žádná uložená hodnota pro specializaci `shared_future<void>`, vrátí metoda **void**.

## <a name="op_eq"></a>  shared_future::Operator =

Přenosy *přidružený asynchronní stav* ze zadaného objektu.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
A `shared_future` objektu.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Pro první operátor *vpravo* již nemá přidružený asynchronní stav po provedení této operace.

Pro druhý způsob *vpravo* udržuje příslušném asynchronním stavu.

## <a name="shared_future"></a>  shared_future::shared_future – konstruktor

Vytvoří `shared_future` objektu.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
A [budoucí](../standard-library/future-class.md) nebo `shared_future` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor zkonstruuje `shared_future` objekt, který nemá žádné *přidružený asynchronní stav*.

Sestavit druhý a třetí konstruktor `shared_future` objektu a přenos přidružený asynchronní stav z *vpravo*. *Pravé* již nemá přidružený asynchronní stav.

Čtvrtý konstruktor vytvoří `shared_future` objekt, který má stejný připojený asynchronní stav jako *vpravo*.

## <a name="valid"></a>  shared_future::valid –

Určuje, zda má objekt *přidružený asynchronní stav*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud objekt má přidružený asynchronní stav; v opačném případě **false**.

## <a name="wait"></a>  shared_future::wait –

Blokuje aktuální vlákno, dokud *přidružený asynchronní stav* je *připravené*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav připravený, pouze v případě, že jeho asynchronního poskytovatele má uložené návratovou hodnotu nebo uložené výjimku.

## <a name="wait_for"></a>  shared_future::wait_for –

Blokuje aktuální vlákno, dokud není přidružený asynchronní stav *připravené* nebo dokud neuplyne určitou dobu.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*<br/>
A [chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální časový interval, který vlákno blokováno.

### <a name="return-value"></a>Návratová hodnota

A [future_status –](../standard-library/future-enums.md#future_status) , který označuje důvod pro vrácení.

### <a name="remarks"></a>Poznámky

Je přidružený asynchronní stav *připravené* pouze v případě, že jeho asynchronního poskytovatele má uložené návratovou hodnotu nebo uložené výjimku.

## <a name="wait_until"></a>  shared_future::wait_until –

Blokuje aktuální vlákno, dokud není přidružený asynchronní stav *připravené* nebo až po zadaný časový bod.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*<br/>
A [chrono::time_point](../standard-library/time-point-class.md) objekt, který určuje dobu, po jejímž uplynutí může odblokovat vlákna.

### <a name="return-value"></a>Návratová hodnota

A [future_status –](../standard-library/future-enums.md#future_status) , který označuje důvod pro vrácení.

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav připravený, pouze v případě, že jeho asynchronního poskytovatele má uložené návratovou hodnotu nebo uložené výjimku.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<Další >](../standard-library/future.md)<br/>
