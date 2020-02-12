---
title: sampler – třída
ms.date: 06/28/2018
f1_keywords:
- sampler
- AMP_GRAPHICS/sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::get_address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::get_border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::get_filter_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::filter_mode
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
ms.openlocfilehash: 8f47bf6e9b88dba1e94e9e2ed2b93c8d2d3f9b8c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126347"
---
# <a name="sampler-class"></a>sampler – třída

Třída vzorkovače agreguje informace o konfiguraci vzorkování, které se mají použít pro vzorkování textury.

## <a name="syntax"></a>Syntaxe

```cpp
class sampler;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Vzorkovník – konstruktor](#ctor)|Přetíženo. Vytvoří instanci vzorkovače.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|Vrátí `address_mode`, která je přidružena k objektu vzorkovače.|
|[get_border_color](#get_border_color)|Vrátí barvu ohraničení, která je přidružena k objektu vzorkovače.|
|[get_filter_mode](#get_filter_mode)|Vrátí `filter_mode`, která je přidružena k objektu vzorkovače.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Přetíženo. Operátor přiřazení|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[address_mode](#address_mode)|Získá režim adresy objektu `sampler`.|
|[border_color](#border_color)|Získá barvu ohraničení objektu `sampler`.|
|[filter_mode](#filter_mode)|Získá režim filtru objektu `sampler`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`sampler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics. h

**Obor názvů:** concurrency:: Graphics

## <a name="ctor"></a>vzorkovače

Vytvoří instanci [třídy vzorkovače](sampler-class.md).

```cpp
sampler() restrict(cpu);    // [1] default constructor

sampler(                    // [2] constructor
    filter_mode _Filter_mode) restrict(cpu);

sampler(                    // [3] constructor
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [4] constructor
    filter_mode _Filter_mode,
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [5] copy constructor
    const sampler& _Other) restrict(amp,
    cpu);

sampler(                    // [6] move constructor
    sampler&& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parametry

*_Filter_mode*<br/>
Režim filtru, který se má použít při vzorkování.

*_Address_mode*<br/>
Režim adresování, který se má použít při vzorkování pro všechny dimenze.

*_Border_color*<br/>
Barva ohraničení, která se má použít, pokud je režim adresy address_border. Výchozí hodnota je `float_4(0.0f, 0.0f, 0.0f, 0.0f)`.

*_Other*<br/>
[5] zkopírování objektu `sampler` a zkopírování do nové instance `sampler`.

[6] přesunutí konstruktoru objekt `sampler`, který se má přesunout do nové instance `sampler`.

## <a name="address_mode"></a>address_mode

Získá režim adresy objektu `sampler`.

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

## <a name="border_color"></a>border_color

Získá barvu ohraničení objektu `sampler`.

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

## <a name="filter_mode"></a>filter_mode

Získá režim filtru objektu `sampler`.

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

## <a name="get_address_mode"></a>get_address_mode

Vrátí režim filtru, který je nakonfigurován pro tento `sampler`.

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>Návratová hodnota

Režim adresy, který je nakonfigurován pro vzorkovník.

## <a name="get_border_color"></a>get_border_color

Vrátí barvu ohraničení, která je konfigurována pro tento `sampler`.

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>Návratová hodnota

Float_4, který obsahuje barvu ohraničení.

## <a name="get_filter_mode"></a>get_filter_mode

Vrátí režim filtru, který je nakonfigurován pro tento `sampler`.

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>Návratová hodnota

Režim filtru, který je nakonfigurován pro vzorkovník.

## <a name="operator_eq"></a>operátor =

Přiřadí hodnotu jiného objektu vzorkovače existujícímu vzorkovači.

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
[1] zkopírovat operátor přiřazení: objekt `sampler` ke zkopírování do tohoto `sampler`.

[2] operátor přiřazení přesunu `sampler` objekt, který se má přesunout do tohoto `sampler`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tuto instanci vzorkovače.

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
