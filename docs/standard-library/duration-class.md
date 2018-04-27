---
title: Doba trvání třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::chrono [C++], duration
ms.workload:
- cplusplus
ms.openlocfilehash: 5f7e1b7bcf1cfa91a3b1a5d528ee77552e56dad5
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="duration-class"></a>duration – třída

Popisuje typ, který obsahuje *časový interval*, který je uplynulý čas mezi dvěma body čas.

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

Argument šablony `Rep` popisuje typ, který se používá k uložení všech počtu taktů v intervalu. Argument šablony `Period` je vytváření instancí z [poměr](../standard-library/ratio.md) , který popisuje velikost interval, který představuje jednotlivých značek.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné – definice TypeDef

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
|[Počet](#count)|Vrátí počet počtu taktů v časovém intervalu.|
|[max](#max)|Statické. Vrátí maximální povolená hodnota parametru šablony `Ref`.|
|[Min.](#min)|Statické. Vrátí nejnižší povolená hodnota parametru šablony `Ref`.|
|[Nula.](#zero)|Statické. V důsledku toho vrátí `Rep`(0).|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[DURATION::Operator-](#operator-)|Vrátí kopii `duration` objekt společně s počet posunut značek.|
|[DURATION::Operator--](#operator--)|Snižuje počet uložených značek.|
|[DURATION::Operator =](#op_eq)|Snižuje počet uložených značek modulo zadanou hodnotou.|
|[DURATION::Operator * =](#op_star_eq)|Vynásobí počet uložených značek zadanou hodnotou.|
|[DURATION::Operator / =](#op_div_eq)|Rozdělí počet uložených značek podle značek počtu zadané `duration` objektu.|
|[DURATION::Operator +](#op_add)|Vrátí `*this`.|
|[DURATION::Operator ++](#op_add_add)|Zvýší počet uložených značek.|
|[DURATION::Operator +=](#op_add_eq)|Přidá značek počet zadané `duration` objekt, který má počet uložených značek.|
|[DURATION::Operator-=](#operator-_eq)|Odečítá od značek počet zadané `duration` objekt z počet uložených značek.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<typu chrono >

**Namespace:** std::chrono

## <a name="count"></a>  DURATION::Count –

Načte počet taktů v časovém intervalu.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet počtu taktů v časovém intervalu.

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

`Rep2` Aritmetické typ představující počet značek.

`Period2` A `std::ratio` specializace šablony k reprezentaci značky období v jednotkách sekund.

`R` Počet rysky výchozí dobu.

`Dur` Počet značek určeného období `Period2`.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor vytvoří objekt, který není inicializován. Inicializace hodnotu pomocí prázdné složené závorky inicializuje objekt, který představuje časovém intervalu nulové počtu taktů.

Druhý, jedna šablona argument konstruktoru vytvoří objekt představující časovém intervalu z `R` taktovací rysky pomocí výchozí období `std::ratio<1>`. Abyste se vyhnuli zaokrouhlená čítače impulzů, jedná se o chybu vytvořit objekt trvání z typu reprezentace `Rep2` , lze zacházet jako plovoucí desetinnou čárkou zadejte, kdy `duration::rep` nemohou být považovány za typu s plovoucí desetinnou čárkou.

Třetí, dvě šablony argument konstruktoru vytvoří objekt, který představuje časový interval, jehož délka je časový interval, která je zadána `Dur`. Abyste se vyhnuli zkrácení čítače impulzů, jedná se o chybu při sestavování trvání objektu z jiného objektu doba trvání, jejichž typ je *incommensurable* s typ cíle.

Doba trvání typ `D1` je *incommensurable* s jiným typem trvání `D2` Pokud `D2` nemohou být považovány za typu s plovoucí desetinnou čárkou a [ratio_divide\<D1::period, D2:: období >:: type::den](../standard-library/ratio.md) není 1.

Pokud `Rep2` implicitně převést na `rep` a buď `treat_as_floating_point<rep>` *platí* nebo `treat_as_floating_point<Rep2>` *obsahuje false*, druhý konstruktor není součástí řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

Pokud je vyvolané žádné přetečení při převodu a `treat_as_floating_point<rep>` *platí*, nebo obojí `ratio_divide<Period2, period>::den` rovná 1 a `treat_as_floating_point<Rep2>` *obsahuje false*, třetí konstruktor není součástí řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

## <a name="max"></a>  DURATION::max –

Statickou metodu, která vrací horní mez pro hodnoty typu parametru šablony `Ref`.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `duration(duration_values<rep>::max())`.

## <a name="min"></a>  DURATION::min –

Statickou metodu, která vrátí dolní mez pro hodnoty typu parametru šablony `Ref`.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `duration(duration_values<rep>::min())`.

## <a name="duration__operator-"></a>  DURATION::Operator-

Vrátí kopii `duration` objekt společně s počet posunut značek.

```cpp
constexpr duration operator-() const;
```

## <a name="duration__operator--"></a>  DURATION::Operator--

Snižuje počet uložených značek.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí první metoda `*this`.

Druhá metoda vrátí kopii `*this` , se provádí před snížení.

## <a name="op_eq"></a>  DURATION::Operator =

Snižuje počet uložených značek modulo zadanou hodnotou.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

`Div` Pro metodu první `Div` představuje počet značek. Pro metodu druhý `Div` je `duration` objekt, který obsahuje počet značek.

### <a name="return-value"></a>Návratová hodnota

`duration` Objektu po modulo operace provádí.

## <a name="op_star_eq"></a>  DURATION::Operator * =

Vynásobí počet uložených značek zadanou hodnotou.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Parametry

`Mult` Hodnotu typu, která je zadána `duration::rep`.

### <a name="return-value"></a>Návratová hodnota

`duration` Objektu po provedení násobení.

## <a name="op_div_eq"></a>  DURATION::Operator / =

Vydělí počet uložených značek zadanou hodnotou.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Parametry

`Div` Hodnotu typu, která je zadána `duration::rep`.

### <a name="return-value"></a>Návratová hodnota

`duration` Objektu po dělení.

## <a name="op_add"></a>  DURATION::Operator +

Vrátí `*this`.

```cpp
constexpr duration operator+() const;
```

## <a name="op_add_add"></a>  DURATION::Operator ++

Zvýší počet uložených značek.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí první metoda `*this`.

Druhá metoda vrátí kopii `*this` , se provádí před přírůstku.

## <a name="op_add_eq"></a>  DURATION::Operator +=

Přidá značek počet zadané `duration` objekt, který má počet uložených značek.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

`Dur` A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`duration` Objektu po přidání provádí.

## <a name="duration__operator-_eq"></a>  DURATION::Operator-=

Odečítá od značek počet zadané `duration` objekt z počet uložených značek.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

`Dur` A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`duration` Objektu po provedení odčítání.

## <a name="zero"></a>  DURATION::Zero –

Vrátí `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="op_mod_eq"></a>  DURATION::Operator mod =

Snižuje počet uložených značek modulo Div nebo Div.count().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

`Div` Dělitel, který se buď objekt doba trvání, nebo hodnotu, která představuje čítače impulzů.

### <a name="remarks"></a>Poznámky

První člen funkce snižuje počet uložených značek modulo Div a vrátí * to. Druhý členská funkce snižuje počet uložených značek modulo Div.count() a vrátí \*to.

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[duration_values – struktura](../standard-library/duration-values-structure.md)<br/>
