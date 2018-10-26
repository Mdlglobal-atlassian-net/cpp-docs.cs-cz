---
title: DURATION – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
dev_langs:
- C++
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::chrono [C++], duration
ms.workload:
- cplusplus
ms.openlocfilehash: db0ba9b841b26cab9f36cddba0c1f402e4812a20
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072000"
---
# <a name="duration-class"></a>duration – třída

Popisuje typ, který obsahuje *časový interval*, což je uplynulý čas mezi dvěma body v čase.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep, class Period = ratio<1>>
class duration;
template <class Rep, class Period>
class duration;
template <class Rep, class Period1, class Period2>
class duration <duration<Rep, Period1>, Period2>;
```

## <a name="remarks"></a>Poznámky

Argument šablony `Rep` popisuje typ, který se používá k ukládání počtu taktů v intervalu. Argument šablony `Period` je instance [poměr](../standard-library/ratio.md) , který označuje velikost intervalu, který jednotlivé takty představují.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|DURATION::period – Typedef|Představuje synonymum pro parametr šablony `Period`.|
|DURATION::rep – Typedef|Představuje synonymum pro parametr šablony `Rep`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Doba trvání](#duration)|Vytvoří `duration` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Počet](#count)|Vrátí počet taktů v časovém intervalu.|
|[max](#max)|Statické. Vrátí maximální povolenou hodnotou parametru šablony `Ref`.|
|[min](#min)|Statické. Vrátí nejnižší povolenou hodnotou parametru šablony `Ref`.|
|[Nula](#zero)|Statické. V důsledku toho vrátí `Rep`(0).|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[DURATION::Operator-](#operator-)|Vrátí kopii objektu `duration` společně s negovaným čítačem značek.|
|[DURATION::Operator--](#operator--)|Sníží počet uložených impulzů.|
|[DURATION::Operator =](#op_eq)|Sníží uložený čítač značek modulo zadaná hodnota.|
|[DURATION::Operator * =](#op_star_eq)|Vynásobí uložený čítač impulzů zadanou hodnotou.|
|[DURATION::Operator / =](#op_div_eq)|Vydělí uložený čítač impulzů počtem impulzů zadaného `duration` objektu.|
|[DURATION::Operator +](#op_add)|Vrátí `*this`.|
|[DURATION::Operator ++](#op_add_add)|Zvýší počet uložených impulzů.|
|[DURATION::Operator +=](#op_add_eq)|Přidá počet impulsů zadaného `duration` objektu do uloženého počtu impulsů.|
|[DURATION::Operator-=](#operator-_eq)|Odečte počet impulsů zadaného `duration` objekt od uloženého počtu impulsů.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono >

**Namespace:** std::chrono

## <a name="count"></a>  DURATION::Count –

Načte počet taktů v časovém intervalu.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet taktů v časovém intervalu.

## <a name="duration"></a>  DURATION::Duration – konstruktor

Vytvoří `duration` objektu.

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>Parametry

*Rep2*<br/>
Aritmetický typ představující počet taktů.

*Period2*<br/>
A `std::ratio` specializace šablony pro počet dob taktů v jednotkách sady sekund.

*R*<br/>
Počet taktů výchozí období.

*Doba trvání*<br/>
Počet taktů limitu určeného *Period2*.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří objekt, který není inicializován. Inicializace hodnoty pomocí prázdné závorky inicializuje objekt, který představuje časový interval nula taktů.

Druhé, jedna šablona argument konstruktor vytvoří objekt, který představuje časový interval *R* pomocí výchozí období v taktech `std::ratio<1>`. Chcete-li zabránit zaokrouhlování počtu impulsů, je chybou konstruovat objekt trvání z typu reprezentace *Rep2* , který lze zacházet jako plovoucí desetinnou čárkou když `duration::rep` nemůže být zpracován jako typ s plovoucí desetinnou čárkou.

Třetí, dvě šablony argument konstruktor vytvoří objekt, který představuje časový interval, jehož délka je časový interval, který je určen *doba trvání*. Chcete-li zabránit zkrácení čítače impulzů, je chybou konstruovat objekt trvání z jiného objektu trvání, jehož typ je *incommensurable* s cílovým typem.

Typ trvání `D1` je *incommensurable* s dalším typem trvání `D2` Pokud `D2` nemůže být zpracován jako typ s plovoucí desetinnou čárkou a [ratio_divide\<D1::period, D2:: období >:: type::den](../standard-library/ratio.md) není 1.

Není-li *Rep2* implicitně převést na `rep` a buď `treat_as_floating_point<rep>` *platí* nebo `treat_as_floating_point<Rep2>` *obsahuje hodnotu false*, druhý konstruktor není součástí řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

Pokud je způsobený bez přetečení při převodu a `treat_as_floating_point<rep>` *platí*, nebo obojí `ratio_divide<Period2, period>::den` je rovno 1 a `treat_as_floating_point<Rep2>` *obsahuje hodnotu false*, třetí konstruktor není součástí řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

## <a name="max"></a>  DURATION::max –

Statická metoda, která vrátí horní mez pro hodnoty typu parametru šablony `Ref`.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `duration(duration_values<rep>::max())`.

## <a name="min"></a>  DURATION::min –

Statická metoda, která vrátí dolní mez pro hodnoty typu parametru šablony `Ref`.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `duration(duration_values<rep>::min())`.

## <a name="duration__operator-"></a>  DURATION::Operator-

Vrátí kopii objektu `duration` společně s negovaným čítačem značek.

```cpp
constexpr duration operator-() const;
```

## <a name="duration__operator--"></a>  DURATION::Operator--

Sníží počet uložených impulzů.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

První metoda vrátí `*this`.

Druhá metoda vrátí kopii objektu `*this` , která je provedena před snížení.

## <a name="op_eq"></a>  DURATION::Operator =

Sníží uložený čítač značek modulo zadaná hodnota.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*div*<br/>
První metoda *Div* představuje počet cyklů. Pro druhý způsob *Div* je `duration` objekt, který obsahuje počet cyklů.

### <a name="return-value"></a>Návratová hodnota

`duration` Objektu po operace modulo.

## <a name="op_star_eq"></a>  DURATION::Operator * =

Vynásobí uložený čítač impulzů zadanou hodnotou.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Parametry

*Mult*<br/>
Hodnota typu, která je zadána `duration::rep`.

### <a name="return-value"></a>Návratová hodnota

`duration` Objektu po provedení násobení.

## <a name="op_div_eq"></a>  DURATION::Operator / =

Vydělí uložený čítač impulzů zadanou hodnotou.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Parametry

*div*<br/>
Hodnota typu, která je zadána `duration::rep`.

### <a name="return-value"></a>Návratová hodnota

`duration` Objektu po provedení odečítání.

## <a name="op_add"></a>  DURATION::Operator +

Vrátí `*this`.

```cpp
constexpr duration operator+() const;
```

## <a name="op_add_add"></a>  DURATION::Operator ++

Zvýší počet uložených impulzů.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První metoda vrátí `*this`.

Druhá metoda vrátí kopii objektu `*this` , která je provedena před inkrementací.

## <a name="op_add_eq"></a>  DURATION::Operator +=

Přidá počet impulsů zadaného `duration` objektu do uloženého počtu impulsů.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`duration` Objektu po provedení sčítání.

## <a name="duration__operator-_eq"></a>  DURATION::Operator-=

Odečte počet impulsů zadaného `duration` objekt od uloženého počtu impulsů.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`duration` Objektu po provedení odečtení.

## <a name="zero"></a>  DURATION::Zero

Vrátí `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="op_mod_eq"></a>  DURATION::Operator mod =

Sníží uložený čítač značek modulo Div nebo Div.count().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*div*<br/>
Dělitel, který je buď objekt trvání, nebo hodnotu, která představuje čítače impulzů.

### <a name="remarks"></a>Poznámky

První členská funkce sníží uložený čítač značek modulo Div a vrátí * to. Druhá členská funkce sníží uložený čítač značek modulo Div.count() a vrátí \*to.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[duration_values – struktura](../standard-library/duration-values-structure.md)<br/>
