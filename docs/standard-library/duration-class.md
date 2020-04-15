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
ms.openlocfilehash: 3669935bf094f476ca24a8170a0388dff29e0a0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368757"
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

Argument `Rep` šablony popisuje typ, který se používá k uložení počtu značek hodin v intervalu. Argument `Period` šablony je konkretizace [poměru,](../standard-library/ratio.md) který popisuje velikost intervalu, který představuje každý tick.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|doba trvání::period Typedef|Představuje synonymum pro `Period`parametr šablony .|
|doba trvání::rep Typedef|Představuje synonymum pro `Rep`parametr šablony .|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Doba trvání](#duration)|Vytvoří `duration` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Počet](#count)|Vrátí počet značek hodin v časovém intervalu.|
|[Max](#max)|Statická. Vrátí maximální přípustnou hodnotu `Ref`parametru šablony .|
|[Min](#min)|Statická. Vrátí nejnižší přípustnou hodnotu `Ref`parametru šablony .|
|[Nula](#zero)|Statická. Ve skutečnosti `Rep`vrátí (0).|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[doba trvání::operátor-](#operator-)|Vrátí kopii `duration` objektu spolu s negovaný počet značek.|
|[doba trvání::operátor--](#operator--)|Sníží počet uložených značek.|
|[doba trvání::operátor=](#op_eq)|Snižuje uložené tick počet modulo zadanou hodnotu.|
|[doba trvání::operátor*=](#op_star_eq)|Vynásobí počet uložených značek zadanou hodnotou.|
|[doba trvání::operátor/=](#op_div_eq)|Vydělí uložený počet značek počtem `duration` značek zadaného objektu.|
|[doba trvání::operátor+](#op_add)|Vrací objekt `*this`.|
|[doba trvání::operátor++](#op_add_add)|Zvýšení počtu uložených značek.|
|[doba trvání::operátor+=](#op_add_eq)|Přidá počet značek zadaného `duration` objektu do uloženého počtu značek.|
|[doba trvání::operátor-=](#operator-_eq)|Odečte počet značek zadaného `duration` objektu od uloženého počtu značek.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono>

**Obor názvů:** std::chrono

## <a name="durationcount"></a><a name="count"></a>doba trvání::počet

Načte počet značek hodin v časovém intervalu.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet hodin tiká v časovém intervalu.

## <a name="durationduration-constructor"></a><a name="duration"></a>doba trvání::dkonstruktivní konstruktor

Vytvoří `duration` objekt.

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>Parametry

*Rep2*\
Aritmetický typ představující počet značek.

*Období2*\
Specializace `std::ratio` šablony představující období značek v jednotkách sekund.

*R*\
Počet značek výchozí období.

*Dur (Dur)*\
Počet značek období *určeného period2*.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří objekt, který je neinicializován. Inicializace hodnoty pomocí prázdných složených závorek inicializuje objekt, který představuje časový interval nulových značek hodin.

Druhý, jeden konstruktor argument šablony vytvoří objekt, který představuje časový interval r *hodiny* značky pomocí výchozí období `std::ratio<1>`. Chcete-li se vyhnout zaokrouhlení počtu značek, je chyba vytvořit objekt doby trvání z reprezentace `duration::rep` typu *Rep2,* který lze považovat za typ s plovoucí desetinnou desetinnou, když nelze považovat za typ s plovoucí desetinnou desetinnou.

Třetí, dva argument šablony konstruktor vytvoří objekt, který představuje časový interval, jehož délka je časový interval, který je určen *Dur*. Aby se zabránilo zkrácení počtu značek, je chyba vytvořit objekt doby trvání z jiného objektu duration, jehož typ je *neslučitelný* s cílovým typem.

Typ `D1` doby trvání je *neslučitelný* s `D2` `D2` jiným typem doby trvání, pokud nelze považovat za typ s plovoucí desetinnou čárkou a [ratio_divide\<D1::period, D2::period>::type::den](../standard-library/ratio.md) není 1.

Pokud *Rep2* je implicitně `rep` konvertibilní a `treat_as_floating_point<rep>` *buď platí* nebo `treat_as_floating_point<Rep2>` *obsahuje false*, druhý konstruktor se neúčastní řešení přetížení. Další informace naleznete [v tématu<type_traits>](../standard-library/type-traits.md).

Pokud žádné přetečení je vyvolána v převodu a `treat_as_floating_point<rep>` `treat_as_floating_point<Rep2>` *platí*, nebo oba `ratio_divide<Period2, period>::den` se rovná 1 a drží *false*, třetí konstruktor se neúčastní řešení přetížení. Další informace naleznete [v tématu<type_traits>](../standard-library/type-traits.md).

## <a name="durationmax"></a><a name="max"></a>doba trvání::max

Statická metoda, která vrací horní mez pro hodnoty typu `Ref`parametru šablony .

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Návratová hodnota

Ve skutečnosti `duration(duration_values<rep>::max())`vrátí .

## <a name="durationmin"></a><a name="min"></a>doba trvání::min

Statická metoda, která vrací dolní mez pro hodnoty typu `Ref`parametru šablony .

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Návratová hodnota

Ve skutečnosti `duration(duration_values<rep>::min())`vrátí .

## <a name="durationoperator-"></a><a name="operator-"></a>doba trvání::operátor-

Vrátí kopii `duration` objektu spolu s negovaný počet značek.

```cpp
constexpr duration operator-() const;
```

## <a name="durationoperator--"></a><a name="operator--"></a>doba trvání::operátor--

Sníží počet uložených značek.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

První metoda `*this`vrátí .

Druhá metoda vrátí `*this` kopii, která je provedena před snížení.

## <a name="durationoperator"></a><a name="op_eq"></a>doba trvání::operátor=

Snižuje uložené tick počet modulo zadanou hodnotu.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*Div*\
Pro první metodu *Div* představuje počet značek. Pro druhou metodu *Div* je `duration` objekt, který obsahuje počet značek.

### <a name="return-value"></a>Návratová hodnota

Objekt `duration` po operaci modulo je provedena.

## <a name="durationoperator"></a><a name="op_star_eq"></a>doba trvání::operátor*=

Vynásobí počet uložených značek zadanou hodnotou.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Parametry

*Mult*\
Hodnota typu, který je `duration::rep`určen .

### <a name="return-value"></a>Návratová hodnota

Objekt `duration` po násobení se provádí.

## <a name="durationoperator"></a><a name="op_div_eq"></a>doba trvání::operátor/=

Vydělí uložený počet značek zadanou hodnotou.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Parametry

*Div*\
Hodnota typu, který je `duration::rep`určen .

### <a name="return-value"></a>Návratová hodnota

Objekt `duration` po provedení dělení.

## <a name="durationoperator"></a><a name="op_add"></a>doba trvání::operátor+

Vrací objekt `*this`.

```cpp
constexpr duration operator+() const;
```

## <a name="durationoperator"></a><a name="op_add_add"></a>doba trvání::operátor++

Zvýšení počtu uložených značek.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

První metoda `*this`vrátí .

Druhá metoda vrátí `*this` kopii, která je provedena před přírůstek.

## <a name="durationoperator"></a><a name="op_add_eq"></a>doba trvání::operátor+=

Přidá počet značek zadaného `duration` objektu do uloženého počtu značek.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Dur (Dur)*\
Objekt. `duration`

### <a name="return-value"></a>Návratová hodnota

Objekt `duration` po přidání se provádí.

## <a name="durationoperator-"></a><a name="operator-_eq"></a>doba trvání::operátor-=

Odečte počet značek zadaného `duration` objektu od uloženého počtu značek.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Dur (Dur)*\
Objekt. `duration`

### <a name="return-value"></a>Návratová hodnota

Objekt `duration` po odčítání je provedena.

## <a name="durationzero"></a><a name="zero"></a>doba trvání::nula

Vrací objekt `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="durationoperator-mod"></a><a name="op_mod_eq"></a>doba trvání::operátor mod=

Snižuje uložené tick count modulo Div nebo Div.count().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*Div*\
Dělitel, což je buď objekt doby trvání nebo hodnota, která představuje počty značek.

### <a name="remarks"></a>Poznámky

První členská funkce snižuje uložené tick count modulo Div a vrátí *this. Druhá členská funkce snižuje uložené tick count modulo \*Div.count() a vrátí toto.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[duration_values – struktura](../standard-library/duration-values-structure.md)
