---
title: duration – třída
ms.date: 03/27/2016
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
helpviewer_keywords:
- std::chrono [C++], duration
ms.openlocfilehash: 4c537b7dfdd23ba641438e0caf6306cf5549b2d7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454308"
---
# <a name="duration-class"></a>duration – třída

Popisuje typ, který obsahuje *časový interval*, což je uplynulý čas mezi dvěma časovými body.

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

Argument `Rep` šablony popisuje typ, který se používá k uchování počtu taktů v intervalu. Argument `Period` šablony je instance poměru, který [](../standard-library/ratio.md) popisuje velikost intervalu, který jednotlivé značky představují.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|Doba trvání::p eriod typedef|Představuje synonymum pro parametr `Period`šablony.|
|Duration:: REP – definice|Představuje synonymum pro parametr `Rep`šablony.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[Doba trvání](#duration)|`duration` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[výpočtu](#count)|Vrátí počet taktů v časovém intervalu.|
|[max](#max)|Tras. Vrátí maximální povolenou hodnotu parametru `Ref`šablony.|
|[dlouhé](#min)|Tras. Vrátí nejnižší povolenou hodnotu parametru `Ref`šablony.|
|[vynulujte](#zero)|Tras. V důsledku toho vrátí `Rep`(0).|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[Duration:: operator-](#operator-)|Vrátí kopii `duration` objektu společně se počtem impulzů typu negace.|
|[Duration:: operator--](#operator--)|Sníží počet uložených impulsů.|
|[Duration:: operator =](#op_eq)|Snižuje počet uložených impulsů modulo podle zadané hodnoty.|
|[Duration:: operator * =](#op_star_eq)|Vynásobí uložený počet impulsů zadanou hodnotou.|
|[Duration:: operator/=](#op_div_eq)|Vydělí uložený počet impulsů podle počtu impulsů zadaného `duration` objektu.|
|[Duration:: operator + – operátor](#op_add)|Vrátí `*this`.|
|[Duration:: operator + +](#op_add_add)|Zvýší počet uložených impulsů.|
|[Duration:: operator + =](#op_add_eq)|Přidá počet impulsů zadaného `duration` objektu do uloženého počtu impulsů.|
|[Duration:: operator-=](#operator-_eq)|Odečte počet impulsů zadaného `duration` objektu od uloženého počtu impulsů.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<Chrono >

**Obor názvů:** std:: chrono

## <a name="count"></a>Doba trvání:: počet

Načte počet taktů v časovém intervalu.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet taktů v časovém intervalu.

## <a name="duration"></a>Duration::d konstruktor uration

`duration` Vytvoří objekt.

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>Parametry

*Rep2*\
Aritmetický typ, který představuje počet tiků.

*Period2*\
Specializace `std::ratio` šablony představující období zatržení v jednotkách sekund.

*R*\
Počet taktů výchozího období.

*Doba*\
Počet tiků periody určených parametrem *Period2*.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří objekt, který není inicializovaný. Inicializace hodnoty pomocí prázdných složených závorek inicializuje objekt, který představuje časový interval s nulovými takty.

Druhý, jeden konstruktor argumentu šablony vytvoří objekt, který představuje časový interval časových taktů *R* , pomocí výchozího období `std::ratio<1>`. Chcete-li se vyhnout zaokrouhlení počtu impulsů, jedná se o chybu při vytváření objektu doby trvání z typu reprezentace *Rep2* , který lze považovat za typ s plovoucí desetinnou čárkou, pokud `duration::rep` nelze považovat za typ s plovoucí desetinnou čárkou.

Třetí, dva konstruktory argumentů šablony vytvoří objekt, který představuje časový interval, jehož délka je časový interval, který je určen dobou *Trvání*. Aby nedošlo ke zkrácení počtu impulsů, je chyba při vytváření objektu Duration z jiného objektu Duration, jehož typ je *nezpracovatelný* s cílovým typem.

Typ `D1` trvání je *nezpracovatelný* s jiným typem `D2` trvání, pokud `D2` nelze považovat za typ s plovoucí desetinnou čárkou a [\<ratio_divide D1::p eriod, D2::p eriod >:: Type::d EN](../standard-library/ratio.md) není 1.

Pokud je *Rep2* implicitně převoditelná `rep` na a `treat_as_floating_point<rep>`buď má *hodnotu true* , nebo `treat_as_floating_point<Rep2>` *má hodnotu false*, druhý konstruktor se nepodílí na řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

Není-li v převodu vyvoláno přetečení `treat_as_floating_point<rep>`a *má hodnotu true*, `ratio_divide<Period2, period>::den` nebo se v obou `treat_as_floating_point<Rep2>`případech rovná 1 a *obsahuje hodnotu false*, třetí konstruktor se nepodílí na řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

## <a name="max"></a>Doba trvání:: max

Statická metoda, která vrátí horní mez pro hodnoty typu `Ref`parametru šablony.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `duration(duration_values<rep>::max())`.

## <a name="min"></a>Doba trvání:: min

Statická metoda, která vrátí dolní mez pro hodnoty typu `Ref`parametru šablony.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `duration(duration_values<rep>::min())`.

## <a name="operator-"></a>Duration:: operator-

Vrátí kopii `duration` objektu společně se počtem impulzů typu negace.

```cpp
constexpr duration operator-() const;
```

## <a name="operator--"></a>Duration:: operator--

Sníží počet uložených impulsů.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

První metoda vrátí `*this`.

Druhá metoda vrátí kopii `*this` , která je vytvořena před snížením.

## <a name="op_eq"></a>Duration:: operator =

Snižuje počet uložených impulsů modulo podle zadané hodnoty.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*Značek*\
Pro první metodu představuje *div* počet impulsů. Pro druhou metodu je `duration` *div* objekt, který obsahuje počet impulsů.

### <a name="return-value"></a>Návratová hodnota

`duration` Objekt po provedení operace modulo.

## <a name="op_star_eq"></a>Duration:: operator * =

Vynásobí uložený počet impulsů zadanou hodnotou.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Parametry

*Mult*\
Hodnota typu, který je určen parametrem `duration::rep`.

### <a name="return-value"></a>Návratová hodnota

`duration` Objekt po provedení násobení.

## <a name="op_div_eq"></a>Duration:: operator/=

Vydělí uložený počet impulsů zadanou hodnotou.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Parametry

*Značek*\
Hodnota typu, který je určen parametrem `duration::rep`.

### <a name="return-value"></a>Návratová hodnota

`duration` Objekt po dělení.

## <a name="op_add"></a>Duration:: operator + – operátor

Vrátí `*this`.

```cpp
constexpr duration operator+() const;
```

## <a name="op_add_add"></a>Duration:: operator + +

Zvýší počet uložených impulsů.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První metoda vrátí `*this`.

Druhá metoda vrátí kopii `*this` , která je vytvořena před přírůstem.

## <a name="op_add_eq"></a>Duration:: operator + =

Přidá počet impulsů zadaného `duration` objektu do uloženého počtu impulsů.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Doba*\
A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`duration` Objekt po provedení přidání.

## <a name="operator-_eq"></a>Duration:: operator-=

Odečte počet impulsů zadaného `duration` objektu od uloženého počtu impulsů.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Doba*\
A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`duration` Objekt po odčítání.

## <a name="zero"></a>Doba trvání:: nula

Vrátí `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="op_mod_eq"></a>Duration:: operator mod =

Snižuje počet uložených impulsů modulo Div nebo div. Count ().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*Značek*\
Dělitel, což je buď objekt duration, nebo hodnota, která představuje počty impulsů.

### <a name="remarks"></a>Poznámky

První členská funkce zmenší počet uložených impulsů modulo Div a vrátí hodnotu * this. Druhá členská funkce zmenší počet uložených impulsů modulo Div. Count () a vrátí \*tuto hodnotu.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[duration_values – struktura](../standard-library/duration-values-structure.md)
