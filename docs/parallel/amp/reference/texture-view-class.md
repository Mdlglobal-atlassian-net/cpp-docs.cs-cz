---
title: texture_view – třída
ms.date: 11/04/2016
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
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
ms.openlocfilehash: 6bf4b9666d746199cea92fa2bd52b691c67e4a5b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126342"
---
# <a name="texture_view-class"></a>texture_view – třída

Poskytuje přístup pro čtení a zápis k texturě. `texture_view` lze použít pouze ke čtení textur, jejichž typ hodnoty je `int`, `unsigned int`nebo `float`, které mají výchozí 32-bit bpse. Pro čtení dalších formátů textury použijte `texture_view<const value_type, _Rank>`.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename value_type,int _Rank>
class texture_view;

template<typename value_type, int _Rank>
class texture_view
   : public details::_Texture_base<value_type, _Rank>;

template<typename value_type, int _Rank>
class texture_view<const value_type, _Rank>
   : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>Parametry

*value_type*<br/>
Typ prvků v agregaci textury.

*_Rank*<br/>
Pořadí `texture_view`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`value_type`|Typ prvků v agregacích textury.|
|`coordinates_type`|Typ souřadnic, který slouží k určení Texel v `texture_view`– to znamená `short_vector`, která má stejný rozměr jako přidružená textura s typem hodnoty `float`.|
|`gather_return_type`|Návratový typ použitý pro shromáždění operací – to znamená, že pořadí 4 `short_vector`, které obsahuje čtyři homogenní barevné součásti shromážděné ze čtyř Texel hodnot.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[texture_view – konstruktor](#ctor)|Přetíženo. Vytvoří instanci `texture_view`.|
|[~ texture_view destruktor](#ctor)|Odstraní instanci `texture_view`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|Přetíženo. Vzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí komponenty alfa (w) čtyř navzorkovaných texelů.|
|[gather_blue](#gather_blue)|Přetíženo. Vzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí modré (z) komponenty čtyř vzorků texelů.|
|[gather_green](#gather_green)|Přetíženo. Vzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí zelené (y) komponenty čtyř navzorkovaných texelů.|
|[gather_red](#gather_red)|Přetíženo. Vzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí červené (x) komponenty čtyř vzorků texelů.|
|[get](#get)|Přetíženo. Získá hodnotu prvku podle indexu.|
|[vzorku](#sample)|Přetíženo. Vzorkuje texturu na zadaných souřadnicích a úrovni podrobností pomocí zadané konfigurace vzorkování.|
|[set](#set)|Nastaví hodnotu prvku podle indexu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator () – operátor](#operator_call)|Přetíženo. Získá hodnotu prvku podle indexu.|
|[operátor\[\]](#operator_at)|Přetíženo. Získá hodnotu prvku podle indexu.|
|[operátor =](#operator_eq)|Přetíženo. Operátor přiřazení|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[value_type](#value_type)|Typ hodnoty prvků `texture_view`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Texture_base`

`texture_view`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics. h

**Obor názvů:** concurrency:: Graphics

## <a name="dtor"></a>~ texture_view

Odstraní instanci `texture_view`.

```cpp
~texture_view() restrict(amp, cpu);
```

## <a name="ctor"></a>texture_view

Vytvoří instanci `texture_view`.

```cpp
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
[1, 2] Vytvoří konstruktor `texture`, na kterém je vytvořen zapisovatelný `texture_view`.

[3, 4] Vytvoří konstruktor `texture`, na kterém je vytvořena `texture_view`, který není zapisovatelný.

*_Other*<br/>
[5] kopírovacímu konstruktoru se `texture_view`zapisovatelný zdroj.

[6, 7] Kopírovací konstruktor, který není zapisovatelný `texture_view`zdrojového kódu.

*_Mipmap_level*<br/>
Konkrétní úroveň mipmap na zdrojovém `texture`, ke které se tento zapisovatelný `texture_view` váže. Výchozí hodnota je 0, což představuje úroveň MIP nejvyšší úrovně (nejpodrobnější).

*_Most_detailed_mip*<br/>
Nejvyšší úroveň (nejpodrobnější) úrovně MIP pro zobrazení relativně k zadanému objektu `texture_view`.

*_Mip_levels*<br/>
Počet úrovní mipmap přístupných prostřednictvím `texture_view`.

## <a name="gather_red"></a>gather_red

Vzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí červené (x) komponenty čtyř vzorků texelů.

```cpp
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
Režim adresy, který se použije k ukázce `texture_view`. Režim adresy je stejný pro všechny dimenze.

*_Sampler*<br/>
Konfigurace vzorkovače, která se má použít pro ukázku `texture_view`.

*_Coord*<br/>
Souřadnice, ze kterých se má provést ukázka Hodnoty zlomkové souřadnice se používají k interpolování vzorových texelů.

### <a name="return-value"></a>Návratová hodnota

Krátký vektor pořadí 4 obsahující červenou (x) komponentu se 4 vzorovými Texel hodnotami.

## <a name="gather_green"></a>gather_green

Vzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí zelené (y) komponenty čtyř navzorkovaných texelů.

```cpp
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
Režim adresy, který se použije k ukázce `texture_view`. Režim adresy je stejný pro všechny dimenze.

*_Sampler*<br/>
Konfigurace vzorkovače, která se má použít pro ukázku `texture_view`.

*_Coord*<br/>
Souřadnice, ze kterých se má provést ukázka Hodnoty zlomkové souřadnice se používají k interpolování vzorových texelů.

### <a name="return-value"></a>Návratová hodnota

Krátký vektor pořadí 4 obsahující zelenou (y) komponentu 4 navzorkovaných Texel hodnot.

## <a name="gather_blue"></a>gather_blue

Vzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí modré (z) komponenty čtyř vzorků texelů.

```cpp
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
Režim adresy, který se použije k ukázce `texture_view`. Režim adresy je stejný pro všechny dimenze.

*_Sampler*<br/>
Konfigurace vzorkovače, která se má použít pro ukázku `texture_view`.

*_Coord*<br/>
Souřadnice, ze kterých se má provést ukázka Hodnoty zlomkové souřadnice se používají k interpolování vzorových texelů.

### <a name="return-value"></a>Návratová hodnota

Krátký vektor pořadí 4 obsahující červenou (x) komponentu se 4 vzorovými Texel hodnotami.

## <a name="gather_alpha"></a>gather_alpha

Vzorkuje texturu na zadaných souřadnicích pomocí zadané konfigurace vzorkování a vrátí komponenty alfa (w) čtyř navzorkovaných texelů.

```cpp
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
Režim adresy, který se použije k ukázce `texture_view`. Režim adresy je stejný pro všechny dimenze.

*_Sampler*<br/>
Konfigurace vzorkovače, která se má použít pro ukázku `texture_view`.

*_Coord*<br/>
Souřadnice, ze kterých se má provést ukázka Hodnoty zlomkové souřadnice se používají k interpolování vzorových texelů.

### <a name="return-value"></a>Návratová hodnota

Krátký vektor pořadí 4 obsahující alfa (w) komponentu se 4 vzorovými Texel hodnotami.

## <a name="get"></a>Čtěte

Získá hodnotu prvku na zadaném indexu.

```cpp
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

value_type get(
    const index<_Rank>& _Index,
    unsigned int _Mip_level = 0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index elementu, který se má získat, možná multidimenzionální.

*_Mip_level*<br/>
Úroveň mipmap, ze které bychom měli získat hodnotu. Výchozí hodnota 0 představuje nejpodrobnější úroveň mipmap.

### <a name="return-value"></a>Návratová hodnota

Hodnota elementu.

## <a name="operator_eq"></a>operátor =

Přiřadí zobrazení stejné textury jako zadaný `texture_view` k této instanci `texture_view`.

```cpp
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
[1, 2] Kopírovací konstruktor pro zapisovatelný objekt `texture_view`.

[3] Kopírovat konstruktor objekt `texture_view`, který není zapisovatelný

### <a name="return-value"></a>Návratová hodnota

Odkaz na tuto instanci `texture_view`.

## <a name="operator_at"></a>operator [] – operátor

Vrátí hodnotu prvku podle indexu.

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index, možná multidimenzionální.

*_I0*<br/>
Jednorozměrného indexu.

### <a name="return-value"></a>Návratová hodnota

Hodnota elementu indexovaného `_Index`.

## <a name="operator_call"></a>operator () – operátor

Vrátí hodnotu prvku podle indexu.

```cpp
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
Index, možná multidimenzionální.

*_I0*<br/>
Nejvýznamnější součást indexu.

*_I1*<br/>
Další důležitou součást indexu.

*_I2*<br/>
Nejméně významná součást indexu.

### <a name="return-value"></a>Návratová hodnota

Hodnota elementu indexovaného `_Index`.

## <a name="sample"></a>vzorku

Vzorkuje texturu na zadaných souřadnicích a úrovni podrobností pomocí zadané konfigurace vzorkování.

```cpp
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
Režim filtru, který se má použít pro ukázku texture_view. Režim filtru je stejný pro minimalizaci, maximální a mipmap filtry.

*_Address_mode*<br/>
Režim adresy, který se použije k ukázce texture_view. Režim adresy je stejný pro všechny dimenze.

*_Sampler*<br/>
Konfigurace vzorkovače, která se má použít pro ukázku texture_view.

*_Coord*<br/>
Souřadnice, ze kterých se má provést ukázka Hodnoty zlomkové souřadnice se používají k interpolování hodnot Texel.

*_Level_of_detail*<br/>
Hodnota určuje úroveň mipmap, ze které se má vzorkovat. Zlomkové hodnoty se používají k interpolaci mezi dvěma mipmap úrovněmi. Výchozí úroveň podrobností je 0, což představuje nejpodrobnější úroveň MIP.

### <a name="return-value"></a>Návratová hodnota

Interpolovaná Ukázková hodnota.

## <a name="set"></a>stanovenými

Nastaví hodnotu elementu v zadaném indexu na zadanou hodnotu.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Index*<br/>
Index prvku, který se má nastavit, možná multidimenzionální.

*value*<br/>
Hodnota, na kterou se má nastavit element

## <a name="value_type"></a>value_type

Typ hodnoty prvků texture_view.

```cpp
typedef typename const value_type value_type;
```

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
