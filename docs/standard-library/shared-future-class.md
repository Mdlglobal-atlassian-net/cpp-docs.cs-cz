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
ms.openlocfilehash: 65ea01a9ced1ca69cd1b1526e7594c4b54387553
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336785"
---
# <a name="shared_future-class"></a>shared_future – třída

Popisuje *asynchronní návratový objekt*. Na rozdíl od [budoucí](../standard-library/future-class.md) objekt *asynchronní zprostředkovatel* může být `shared_future` přidružen a libovolný počet objektů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Poznámky

Nevolejte žádné jiné `valid`metody `operator=`než , a destruktor na `shared_future` objekt, který je *prázdný*.

`shared_future`objekty nejsou synchronizovány. Volání metody na stejný objekt z více vláken zavádí datový závod, který má nepředvídatelné výsledky.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[shared_future](#shared_future)|Vytvoří `shared_future` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[get](#get)|Načte výsledek, který je uložen v *přidruženém asynchronním stavu*.|
|[Platný](#valid)|Určuje, zda objekt není prázdný.|
|[Počkej](#wait)|Blokuje aktuální vlákno, dokud není připraven přidružený asynchronní stav.|
|[wait_for](#wait_for)|Blokuje, dokud není přidružený asynchronní stav připraven nebo dokud neuplyne zadaný čas.|
|[wait_until](#wait_until)|Blokuje, dokud není připraven přidružený asynchronní stav nebo dokud není zadán zadaný bod v čase.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[shared_future::operátor=](#op_eq)|Přiřadí nový přidružený asynchronní stav.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<budoucí>

**Obor názvů:** std

## <a name="shared_futureget"></a><a name="get"></a>shared_future::získat

Načte výsledek, který je uložen v *přidruženém asynchronním stavu*.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Poznámky

Pokud je výsledek výjimkou, metoda ji znovu vyvolá. V opačném případě je vrácen výsledek.

Před načtením výsledku tato metoda blokuje aktuální vlákno, dokud není připraven přidružený asynchronní stav.

Pro částečnou `shared_future<Ty&>`specializaci je uložená hodnota účinně odkazem na objekt, který byl předán *asynchronnímu zprostředkovateli* jako vrácená hodnota.

Protože pro specializaci `shared_future<void>`neexistuje žádná uložená hodnota , vrátí metoda **hodnotu void**.

## <a name="shared_futureoperator"></a><a name="op_eq"></a>shared_future::operátor=

Přenese *přidružený asynchronní stav* ze zadaného objektu.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt. `shared_future`

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Pro první operátor *Right* již nemá přidružený asynchronní stav po operaci.

Pro druhou metodu *Right* udržuje přidružený asynchronní stav.

## <a name="shared_futureshared_future-constructor"></a><a name="shared_future"></a>shared_future::shared_future konstruktor

Vytvoří `shared_future` objekt.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*Právo*\
[Budoucnost](../standard-library/future-class.md) nebo `shared_future` objekt.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří `shared_future` objekt, který nemá žádný *přidružený asynchronní stav*.

Druhý a třetí konstruktory `shared_future` vytvořit objekt a přenést přidružené asynchronní stav z *Right*. *Right* již nemá přidružený asynchronní stav.

Čtvrtý konstruktor vytvoří `shared_future` objekt, který má stejný přidružený asynchronní stav jako *Right*.

## <a name="shared_futurevalid"></a><a name="valid"></a>shared_future::platný

Určuje, zda má objekt *přidružený asynchronní stav*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud má objekt přidružený asynchronní stav; jinak **false**.

## <a name="shared_futurewait"></a><a name="wait"></a>shared_future::počkejte

Blokuje aktuální vlákno, dokud není *připraven* *přidružený asynchronní stav* .

```cpp
void wait() const;
```

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je připraven pouze v případě, že jeho asynchronní zprostředkovatel uložil vrácenou hodnotu nebo uložil výjimku.

## <a name="shared_futurewait_for"></a><a name="wait_for"></a>shared_future::wait_for

Blokuje aktuální vlákno, dokud není *připraven* přidružený asynchronní stav nebo dokud neuplyne zadaný čas.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Objekt [chrono::duration,](../standard-library/duration-class.md) který určuje maximální časový interval, který vlákno blokuje.

### <a name="return-value"></a>Návratová hodnota

[Future_status,](../standard-library/future-enums.md#future_status) který označuje důvod pro vrácení.

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je *připraven* pouze v případě, že jeho asynchronní zprostředkovatel uložil vrácenou hodnotu nebo uložil výjimku.

## <a name="shared_futurewait_until"></a><a name="wait_until"></a>shared_future::wait_until

Blokuje aktuální vlákno, dokud není přidružený asynchronní stav *připraven* nebo až po zadaném časovém bodu.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*\
[Chrono::time_point](../standard-library/time-point-class.md) objekt, který určuje čas, po kterém může vlákno odblokovat.

### <a name="return-value"></a>Návratová hodnota

[Future_status,](../standard-library/future-enums.md#future_status) který označuje důvod pro vrácení.

### <a name="remarks"></a>Poznámky

Přidružený asynchronní stav je připraven pouze v případě, že jeho asynchronní zprostředkovatel uložil vrácenou hodnotu nebo uložil výjimku.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<budoucí>](../standard-library/future.md)
