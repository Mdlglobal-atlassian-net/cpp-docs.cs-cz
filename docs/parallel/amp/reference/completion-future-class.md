---
title: completion_future – třída
ms.date: 11/04/2016
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
ms.openlocfilehash: 69aacad02df5290f161e9d8d311be347668be9f9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127017"
---
# <a name="completion_future-class"></a>completion_future – třída

Představuje budoucí odpovídající asynchronní operaci C++ amp.

## <a name="syntax"></a>Syntaxe

```cpp
class completion_future;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[completion_future – konstruktor](#ctor)|Inicializuje novou instanci třídy `completion_future`.|
|[~ completion_future destruktor](#dtor)|Odstraní objekt `completion_future`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get](#get)|Počká, až se dokončí přidružená asynchronní operace.|
|[Stisknutím](#then)|Zřetězí objekt funkce zpětného volání na objekt `completion_future`, který se má provést, když přidružená asynchronní operace dokončí provádění.|
|[to_task](#to_task)|Vrátí objekt `task`, který odpovídá přidružené asynchronní operaci.|
|[platný](#valid)|Získá logickou hodnotu, která označuje, zda je objekt přidružen k asynchronní operaci.|
|[Počkej](#wait)|Blokuje, dokud není dokončena přidružená asynchronní operace.|
|[wait_for](#wait_for)|Blokuje, dokud se nedokončí přidružená asynchronní operace nebo dokud neuplyne čas zadaný v `_Rel_time`.|
|[wait_until](#wait_until)|Blokuje, dokud není dokončena přidružená asynchronní operace nebo dokud aktuální čas nepřekračuje hodnotu zadanou v `_Abs_time`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor std:: shared_future\<void >](#operator_shared_future)|Implicitně převede objekt `completion_future` na objekt `std::shared_future`.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného objektu `completion_future` do tohoto objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`completion_future`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>completion_future

Inicializuje novou instanci třídy `completion_future`.

### <a name="syntax"></a>Syntaxe

```cpp
completion_future();

completion_future(
    const completion_future& _Other );

completion_future(
    completion_future&& _Other );
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt `completion_future`, který se má zkopírovat nebo přesunout.

### <a name="overloads-list"></a>Seznam přetížení

|Název|Popis|
|----------|-----------------|
|`completion_future();`|Inicializuje novou instanci třídy `completion_future`.|
|`completion_future(const completion_future& _Other);`|Inicializuje novou instanci třídy `completion_future` zkopírováním konstruktoru.|
|`completion_future(completion_future&& _Other);`|Inicializuje novou instanci třídy `completion_future` přesunutím konstruktoru.|

## <a name="get"></a>Čtěte

Počká, až se dokončí přidružená asynchronní operace. Vyvolá uloženou výjimku, pokud byla během asynchronní operace zjištěna jedna.

### <a name="syntax"></a>Syntaxe

```cpp
void get() const;
```

## <a name="operator_shared_future"></a>operátor std:: shared_future\<void >

Implicitně převede objekt `completion_future` na objekt `std::shared_future`.

### <a name="syntax"></a>Syntaxe

```cpp
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt `std::shared_future`.

## <a name="operator_eq"></a>operátor =

Zkopíruje obsah zadaného objektu `completion_future` do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```cpp
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt, ze kterého se má kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento objekt `completion_future`.

## <a name="overloads-list"></a>Seznam přetížení

|Název|Popis|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|Zkopíruje obsah zadaného objektu `completion_future` do tohoto objektu pomocí hlubokého kopírování.|
|`completion_future& operator=(completion_future&& _Other);`|Zkopíruje obsah zadaného objektu `completion_future` do tohoto objektu pomocí přiřazení přesunutí.|

## <a name="then"></a>Stisknutím

Zřetězí objekt funkce zpětného volání na objekt `completion_future`, který se má provést, když přidružená asynchronní operace dokončí provádění.

### <a name="syntax"></a>Syntaxe

```cpp
template <typename _Functor>
void then(const _Functor & _Func ) const;
```

### <a name="parameters"></a>Parametry

*_Functor*<br/>
Funktor zpětného volání.

*_Func*<br/>
Objekt funkce zpětného volání.

## <a name="to_task"></a>to_task

Vrátí objekt `task`, který odpovídá přidružené asynchronní operaci.

### <a name="syntax"></a>Syntaxe

```cpp
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt `task` odpovídající přidružené asynchronní operaci.

## <a name="valid"></a>platný

Získá logickou hodnotu, která označuje, zda je objekt přidružen k asynchronní operaci.

### <a name="syntax"></a>Syntaxe

```cpp
bool valid() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je objekt přidružen k asynchronní operaci; v opačném případě **false**.

## <a name="wait"></a>Počkej

Blokuje, dokud není dokončena přidružená asynchronní operace.

### <a name="syntax"></a>Syntaxe

```cpp
void wait() const;
```

## <a name="wait_for"></a>wait_for

Blokuje, dokud se nedokončí přidružená asynchronní operace nebo dokud neuplyne čas zadaný v `_Rel_time`.

### <a name="syntax"></a>Syntaxe

```cpp
template <
    class _Rep,
    class _Period
>
std::future_status::future_status wait_for(
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;
```

### <a name="parameters"></a>Parametry

*_Rep*<br/>
Aritmetický typ, který představuje počet tiků.

*_Period*<br/>
Std:: poměr, který představuje počet sekund, které uplynou na jednu značku.

*_Rel_time*<br/>
Maximální doba, po kterou se má čekat na dokončení operace.

### <a name="return-value"></a>Návratová hodnota

Vrátí

- `std::future_status::deferred`, pokud přidružená asynchronní operace neběží.

- `std::future_status::ready`, je-li přidružená asynchronní operace dokončena.

- `std::future_status::timeout`, pokud uplynulo zadané časové období.

## <a name="wait_until"></a>wait_until

Blokuje, dokud není dokončena přidružená asynchronní operace nebo dokud aktuální čas nepřekračuje hodnotu zadanou v `_Abs_time`.

### <a name="syntax"></a>Syntaxe

```cpp
template <
    class _Clock,
    class _Duration
>
std::future_status::future_status wait_until(
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;
```

### <a name="parameters"></a>Parametry

*_Clock*<br/>
Čas měření tohoto časového bodu.

*_Duration*<br/>
Časový interval od začátku `_Clock`epocha, po jehož uplynutí vyprší časový limit funkce.

*_Abs_time*<br/>
Bod v čase, po jehož uplynutí bude funkce vyprší.

### <a name="return-value"></a>Návratová hodnota

Vrátí

1. `std::future_status::deferred`, pokud přidružená asynchronní operace neběží.

1. `std::future_status::ready`, je-li přidružená asynchronní operace dokončena.

1. `std::future_status::timeout`, pokud zadané časové období uplynulo.

## <a name="dtor"></a>~ completion_future

Odstraní objekt `completion_future`.

### <a name="syntax"></a>Syntaxe

```cpp
~completion_future();
```

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
