---
title: texture_view – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- texture_view
- AMP_GRAPHICS/texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_alpha
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_blue
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_green
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_red
- AMP_GRAPHICS/Concurrency::graphics::texture_view::get
- AMP_GRAPHICS/Concurrency::graphics::texture_view::sample
- AMP_GRAPHICS/Concurrency::graphics::texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::texture_view::value_type
dev_langs:
- C++
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8a87c303d4527f89a7d7f59b69b3cc8572e0e7b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387403"
---
# <a name="textureview-class"></a>texture_view – třída

Poskytuje přístup pro čtení a zápisu do textury. `texture_view` jde použít jenom ke čtení textur s typem hodnoty `int`, `unsigned int`, nebo `float` , které mají výchozí 32bitovou hodnotu bpse. Chcete-li čtení ostatních formátů textur použijte `texture_view<const value_type, _Rank>`.

## <a name="syntax"></a>Syntaxe

```
template<typename value_type,int _Rank>
class texture_view;

template<typename value_type, int _Rank>
class texture_view
   : public details::_Texture_base<value_type, _Rank>;

template<typename value_type, int _Rank>
class texture_view<const value_type, _Rank>
   : public details::_Texture_base<value_type, _Rank>;
```

#### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ prvků v agregátu textury.

*_Rank*<br/>
Řád objektu `texture_view`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`value_type`|Typ prvků v agregátech textury.|
|`coordinates_type`|Typ souřadnice použitý k určení texelu v `texture_view`– to znamená, `short_vector` , který se stejným názvem, jako má přidružená textura s typem hodnoty z `float`.|
|`gather_return_type`|Návratový typ použitý pro operace shromažďování – tedy pořadí 4 `short_vector` , že obsahuje čtyři homogenní barevné složky komponenty shromážděných z čtyř hodnot texel.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[texture_view – konstruktor](#ctor)|Přetíženo. Vytvoří `texture_view` instance.|
|[~texture_view Destructor](#ctor)|Odstraní `texture_view` instance.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|Přetíženo. Navzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí komponenty alpha (w) čtyř navzorkovaných texelů.|
|[gather_blue](#gather_blue)|Přetíženo. Navzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí komponenty blue (z) čtyř navzorkovaných texelů.|
|[gather_green](#gather_green)|Přetíženo. Navzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí komponenty green (y) čtyř navzorkovaných texelů.|
|[gather_red](#gather_red)|Přetíženo. Navzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí komponenty red (x) čtyř navzorkovaných texelů.|
|[get](#get)|Přetíženo. Získá hodnotu prvku podle indexu.|
|[Ukázka](#sample)|Přetíženo. Navzorkuje texturu na zadaných souřadnicích a úrovni podrobností pomocí zadané konfigurace vzorkování.|
|[set](#set)|Nastaví hodnotu prvku podle indexu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[Operator()](#operator_call)|Přetíženo. Získá hodnotu prvku podle indexu.|
|[Operator [].](#operator_at)|Přetíženo. Získá hodnotu prvku podle indexu.|
|[operátor =](#operator_eq)|Přetíženo. Operátor přiřazení.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[value_type](#value_type)|Typ hodnoty elementů `texture_view`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Texture_base`

`texture_view`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics.h

**Namespace:** concurrency::graphics

##  <a name="dtor"></a> ~ texture_view –

Odstraní `texture_view` instance.

```
~texture_view() restrict(amp, cpu);
```

##  <a name="ctor"></a> texture_view –

Vytvoří `texture_view` instance.

```
texture_view(// [1] constructor
    texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [2] constructor
    texture<value_type, _Rank>& _Src,
    unsigned int _Mipmap_level = 0) restrict(cpu);

texture_view(// [3] constructor
    const texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [4] constructor
    const texture<value_type, _Rank>& _Src,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);

texture_view(// [5] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [6] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [7] copy constructor
    const texture_view<const value_type, _Rank>& _Other,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
[1, 2] Konstruktor `texture` využívající zapisovatelná `texture_view` se vytvoří.

[3, 4] Konstruktor `texture` využívající nezapisovatelná `texture_view` se vytvoří.

*Ji_né*<br/>
[5] Kopírovat konstruktor zapisovatelný zdroj `texture_view`.

[6, 7]. Kopírovací konstruktor nezapisovatelný zdroj `texture_view`.

*_Mipmap_level*<br/>
Konkrétní úroveň mipmap ve zdroji `texture` to tomto zapisovatelné `texture_view` vytvoří vazbu. Výchozí hodnota je 0, což představuje úroveň mip (nejpodrobnější) nejvyšší úrovně.

*_Most_detailed_mip*<br/>
Nejvyšší úrovně (nejpodrobnější) dovozní ceny pro zobrazení relativní k zadanému `texture_view` objektu.

*_Mip_levels*<br/>
Počet úrovní mipmapy přístupných prostřednictvím `texture_view`.

##  <a name="gather_red"></a> gather_red

Navzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí komponenty red (x) čtyř navzorkovaných texelů.

```
const gather_return_type gather_red(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_red(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Address_mode*<br/>
Režim adresy, které chcete použít k ukázce `texture_view`. Režim adresy, který je stejný pro všechny dimenze.

*_Sampler*<br/>
Konfigurace vzorkovníku pro použití k ukázce `texture_view`.

*_Coord*<br/>
Souřadnice, kde je vzorek odebírán. Desetinné hodnoty souřadnic lze interpolovat mezi vzorovými texely.

### <a name="return-value"></a>Návratová hodnota

Krátký vektor pořadí 4 obsahující červenou (y) součást 4 vzorkovaných hodnot texel.

##  <a name="gather_green"></a> gather_green

Navzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí komponenty green (y) čtyř navzorkovaných texelů.

```
const gather_return_type gather_green(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_green(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Address_mode*<br/>
Režim adresy, které chcete použít k ukázce `texture_view`. Režim adresy, který je stejný pro všechny dimenze.

*_Sampler*<br/>
Konfigurace vzorkovníku pro použití k ukázce `texture_view`.

*_Coord*<br/>
Souřadnice, kde je vzorek odebírán. Desetinné hodnoty souřadnic lze interpolovat mezi vzorovými texely.

### <a name="return-value"></a>Návratová hodnota

Krátký vektor pořadí 4 obsahující zelenou (y) součást 4 vzorkovaných hodnot texel.

##  <a name="gather_blue"></a> gather_blue

Navzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí komponenty blue (z) čtyř navzorkovaných texelů.

```
const gather_return_type gather_blue(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_blue(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Address_mode*<br/>
Režim adresy, které chcete použít k ukázce `texture_view`. Režim adresy, který je stejný pro všechny dimenze.

*_Sampler*<br/>
Konfigurace vzorkovníku pro použití k ukázce `texture_view`.

*_Coord*<br/>
Souřadnice, kde je vzorek odebírán. Desetinné hodnoty souřadnic lze interpolovat mezi vzorovými texely.

### <a name="return-value"></a>Návratová hodnota

Krátký vektor pořadí 4 obsahující červenou (y) součást 4 vzorkovaných hodnot texel.

##  <a name="gather_alpha"></a> gather_alpha

Navzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí komponenty alpha (w) čtyř navzorkovaných texelů.

```
const gather_return_type gather_alpha(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_alpha(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Address_mode*<br/>
Režim adresy, které chcete použít k ukázce `texture_view`. Režim adresy, který je stejný pro všechny dimenze.

*_Sampler*<br/>
Konfigurace vzorkovníku pro použití k ukázce `texture_view`.

*_Coord*<br/>
Souřadnice, kde je vzorek odebírán. Desetinné hodnoty souřadnic lze interpolovat mezi vzorovými texely.

### <a name="return-value"></a>Návratová hodnota

Krátký vektor pořadí 4 obsahující alfa (w) součást 4 vzorkovaných hodnot texel.

##  <a name="get"></a> získat

Získá hodnotu prvku na zadaném indexu.

```
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

value_type get(
    const index<_Rank>& _Index,
    unsigned int _Mip_level = 0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index prvku, který chcete získat, případně může být vícedimenzionální.

*_Mip_level*<br/>
Úroveň mipmapy, ze které jsme měli získat hodnotu. Výchozí hodnota 0 představuje nejpodrobnější úroveň mipmapy.

### <a name="return-value"></a>Návratová hodnota

Hodnota elementu.

##  <a name="operator_eq"></a> operátor =

Přiřadí zobrazení stejné textury, jak uvádí `texture_view` tomuto `texture_view` instance.

```
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
[1, 2] Kopírovací konstruktor A zapisovatelné `texture_view` objektu.

[3] Kopírovat konstruktor A nezapisovatelný `texture_view` objektu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `texture_view` instance.

##  <a name="operator_at"></a> Operator [].

Vrátí hodnotu prvku podle indexu.

```
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index, případně může být vícedimenzionální.

*_I0*<br/>
Jednorozměrný index.

### <a name="return-value"></a>Návratová hodnota

Indexovaná hodnota prvku podle `_Index`.

##  <a name="operator_call"></a> Operator()

Vrátí hodnotu prvku podle indexu.

```
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,   int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);

value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

value_type operator() (
    int _I0) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index, případně může být vícedimenzionální.

*_I0*<br/>
Nejvýznamnější komponenta indexu.

*_I1*<br/>
Další na nejvýznamnější komponenta indexu.

*_I2*<br/>
Nejméně významná komponenta indexu.

### <a name="return-value"></a>Návratová hodnota

Indexovaná hodnota prvku podle `_Index`.

##  <a name="sample"></a> Ukázka

Navzorkuje texturu na zadaných souřadnicích a úrovni podrobností pomocí zadané konfigurace vzorkování.

```
value_type sample(
    const sampler& _Sampler,
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);

template<
    filter_mode _Filter_mode = filter_linear,
    address_mode _Address_mode = address_clamp
>
value_type sample(
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Filter_mode*<br/>
Režim filtru, který chcete použít pro vzorkování texture_view. Režim filtru, který je stejný pro minimalizaci, maximalizaci a filtry mipmapy.

*_Address_mode*<br/>
Režim adresy, který chcete použít pro vzorkování texture_view. Režim adresy, který je stejný pro všechny dimenze.

*_Sampler*<br/>
Konfigurace vzorkovníku pro použití pro vzorkování texture_view.

*_Coord*<br/>
Souřadnice, kde je vzorek odebírán. Desetinné hodnoty souřadnic lze interpolovat mezi hodnotami texel.

*_Level_of_detail*<br/>
Hodnota určuje úroveň mipmap k ukázkový z. Desetinné hodnoty se používají k lze interpolovat mezi dvěma úrovněmi mipmap. Výchozí úroveň podrobností je 0, což představuje nejpodrobnější úroveň mip.

### <a name="return-value"></a>Návratová hodnota

Interpolovaná Ukázková hodnota.

##  <a name="set"></a> Nastavit

Nastaví hodnotu prvku na zadaném indexu se zadanou hodnotou.

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index prvku, který chcete nastavit, případně může být vícedimenzionální.

*value*<br/>
Hodnotu nastavit na element.

##  <a name="value_type"></a> value_type

Typ hodnoty elementů texture_view.

```
typedef typename const value_type value_type;
```

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
