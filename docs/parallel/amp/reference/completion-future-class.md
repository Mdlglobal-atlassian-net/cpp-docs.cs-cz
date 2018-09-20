---
title: completion_future – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac3072e3fafe317e0517c36b375259c3c98a1a41
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438480"
---
# <a name="completionfuture-class"></a>completion_future – třída

Představuje budoucí odpovídající asynchronní operaci C++ AMP.

### <a name="syntax"></a>Syntaxe

```
class completion_future;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[completion_future – konstruktor](#ctor)|Inicializuje novou instanci třídy `completion_future` třídy.|
|[~ completion_future – destruktor](#dtor)|Odstraní `completion_future` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get](#get)|Čeká na dokončení přidružené asynchronní operace.|
|[Potom](#then)|Zřetězí objekt funkce zpětného volání k `completion_future` objekt, který se spustí po dokončení spouštění přidružené asynchronní operace.|
|[to_task](#to_task)|Vrátí `task` objekt odpovídající přidružené asynchronní operace.|
|[platný](#valid)|Získá logickou hodnotu určující, zda je objekt přidružené asynchronní operace.|
|[Počkej](#wait)|Blokuje, dokud nebude dokončena přidružená asynchronní operace.|
|[wait_for](#wait_for)|Blokuje, dokud není dokončena přidružená asynchronní operace nebo časový limit určený parametrem `_Rel_time` uplynul.|
|[wait_until](#wait_until)|Blokuje, dokud není dokončena přidružená asynchronní operace nebo aktuální čas nepřekročí hodnotu zadanou pomocí `_Abs_time`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor std::shared_future\<void >](#operator_shared_future)|Implicitně převede `completion_future` objektu `std::shared_future` objektu.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `completion_future` do tohoto objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`completion_future`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt.h

**Namespace:** souběžnosti

## <a name="ctor"></a> completion_future –

Inicializuje novou instanci třídy `completion_future` třídy.

### <a name="syntax"></a>Syntaxe

```
completion_future();

completion_future(
    const completion_future& _Other );

completion_future(
    completion_future&& _Other );
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`completion_future` Objektu, který chcete zkopírovat nebo přesunout.

### <a name="overloads-list"></a>Seznam přetížení

|Název|Popis|
|----------|-----------------|
|`completion_future();`|Inicializuje novou instanci třídy `completion_future` třídy|
|`completion_future(const completion_future& _Other);`|Inicializuje novou instanci třídy `completion_future` zkopírováním konstruktor.|
|`completion_future(completion_future&& _Other);`|Inicializuje novou instanci třídy `completion_future` přesunutím konstruktor třídy.|

## <a name="get"></a> získat

Čeká na dokončení přidružené asynchronní operace. Vyvolá uložené výjimku, pokud jeden došlo během asynchronní operace.

### <a name="syntax"></a>Syntaxe

```
void get() const;
```

## <a name="operator_shared_future"></a> std::shared_future – operátor<void>

Implicitně převede `completion_future` objektu `std::shared_future` objektu.

### <a name="syntax"></a>Syntaxe

```
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>Návratová hodnota

`std::shared_future` Objektu.

## <a name="operator_eq"></a> operátor =

Zkopíruje obsah zadaného `completion_future` do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
Objekt, který bude kopírováno.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `completion_future` objektu.

## <a name="overloads-list"></a>Seznam přetížení

|Název|Popis|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|Zkopíruje obsah zadaného `completion_future` objektu do tohoto objektu za použití hlubokého kopírování.|
|`completion_future& operator=(completion_future&& _Other);`|Zkopíruje obsah zadaného `completion_future` objektu do tohoto objektu za použití přiřazení pro přesun.|

## <a name="then"></a> Potom

Zřetězí objekt funkce zpětného volání k `completion_future` objekt, který se spustí po dokončení spouštění přidružené asynchronní operace.

### <a name="syntax"></a>Syntaxe

```
template <typename _Functor>
void then(const _Functor & _Func ) const;
```

### <a name="parameters"></a>Parametry

*_Functor*<br/>
Zpětné volání funktor.

*_Func*<br/>
Objekt funkce zpětného volání.

## <a name="to_task"></a> to_task

Vrátí `task` objekt odpovídající přidružené asynchronní operace.

### <a name="syntax"></a>Syntaxe

```
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>Návratová hodnota

A `task` objekt odpovídající přidružené asynchronní operace.

## <a name="valid"></a> platný

Získá logickou hodnotu určující, zda je objekt přidružené asynchronní operace.

### <a name="syntax"></a>Syntaxe

```
bool valid() const;
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud se objekt přidružené asynchronní operace; v opačném případě `false`.

## <a name="wait"></a> Počkej

Blokuje, dokud nebude dokončena přidružená asynchronní operace.

### <a name="syntax"></a>Syntaxe

```
void wait() const;
```

## <a name="wait_for"></a> wait_for

Blokuje, dokud není dokončena přidružená asynchronní operace nebo čas, který je určen `_Rel_time` uplynul.

### <a name="syntax"></a>Syntaxe

```
template <
    class _Rep,
    class _Period
>
std::future_status::future_status wait_for(
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;
```

### <a name="parameters"></a>Parametry

*_Rep*<br/>
Aritmetický typ, který reprezentuje počet taktů.

*_Period*<br/>
Poměr std::ratio, který představuje počet sekund, po které uplynou na impulz.

*_Rel_time*<br/>
Maximální dobu čekání na dokončení operace.

### <a name="return-value"></a>Návratová hodnota

Vrátí:

- `std::future_status::deferred` je-li přidružená asynchronní operace neběží.

- `std::future_status::ready` Pokud je dokončena přidružená asynchronní operace.

- `std::future_status::timeout` Pokud zadané časové období uplynul.

## <a name="wait_until"></a> wait_until

Blokuje, dokud není dokončena přidružená asynchronní operace nebo aktuální čas nepřekročí hodnotu zadanou pomocí `_Abs_time`.

### <a name="syntax"></a>Syntaxe

```
template <
    class _Clock,
    class _Duration
>
std::future_status::future_status wait_until(
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;
```

### <a name="parameters"></a>Parametry

*_Clock*<br/>
Hodiny, ve kterém se měří tento časový bod.

*_Duration*<br/>
Časový interval od začátku `_Clock`od epochy, po jejímž uplynutí vyprší časový limit funkce.

*_Abs_time*<br/>
Bod v čase, po jejímž uplynutí funkce bude ukončen časový limit.

### <a name="return-value"></a>Návratová hodnota

Vrátí:

1. `std::future_status::deferred` je-li přidružená asynchronní operace neběží.

1. `std::future_status::ready` Pokud je dokončena přidružená asynchronní operace.

1. `std::future_status::timeout` Pokud zadaný časový limit uplynul.

## <a name="dtor"></a> ~ completion_future –

Odstraní `completion_future` objektu.

### <a name="syntax"></a>Syntaxe

```
~completion_future();
```

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
