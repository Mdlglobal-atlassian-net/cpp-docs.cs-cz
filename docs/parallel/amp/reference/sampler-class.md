---
title: sampler – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee5d50976b6d91bff6d84ec288560ff1348c73d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424687"
---
# <a name="sampler-class"></a>sampler – třída

Třída vzorkovače agreguje informace o konfiguraci odběru vzorků má být použit pro vzorkování textury.

## <a name="syntax"></a>Syntaxe

```cpp
class sampler;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[vzorkování konstruktor](#ctor)|Přetíženo. Vytvoří instanci vzorkovače.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|Vrátí `address_mode` , který je asociován s objektem vzorkovače.|
|[get_border_color](#get_border_color)|Vrátí barvu ohraničení, který je spojen s objektem vzorkovače.|
|[get_filter_mode](#get_filter_mode)|Vrátí `filter_mode` , který je asociován s objektem vzorkovače.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Přetíženo. Operátor přiřazení.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[address_mode](#address_mode)|Načte režim adresy objektu `sampler` objektu.|
|[border_color](#border_color)|Získá barvu ohraničení `sampler` objektu.|
|[filter_mode –](#filter_mode)|Načte režim filtru objektu `sampler` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`sampler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics.h

**Namespace:** concurrency::graphics

##  <a name="ctor"></a> vzorkování

Vytvoří instanci objektu [sampler – třída](sampler-class.md).

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
Režim filtru, který má být použit při vzorkování.

*_Address_mode*<br/>
Režim adresování má být použit při vzorkování pro všechny dimenze.

*_Border_color*<br/>
Barva ohraničení, která se použije, pokud je režim adresy address_border. Výchozí hodnota je `float_4(0.0f, 0.0f, 0.0f, 0.0f)`.

*Ji_né*<br/>
[5] Kopírovat konstruktor `sampler` objekt ke zkopírování do nové `sampler` instance.

[6] přesunout konstruktor `sampler` objektu přesunout do nové `sampler` instance.

##  <a name="address_mode"></a> address_mode –

Načte režim adresy objektu `sampler` objektu.

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

##  <a name="border_color"></a> border_color

Získá barvu ohraničení `sampler` objektu.

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

##  <a name="filter_mode"></a> filter_mode –

Načte režim filtru objektu `sampler` objektu.

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

##  <a name="get_address_mode"></a> get_address_mode

Vrátí režim filtru, který je nakonfigurovaný pro tento `sampler`.

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>Návratová hodnota

Režim adresy, který je nakonfigurován pro vzorkovač.

##  <a name="get_border_color"></a> get_border_color

Vrátí barvu ohraničení, která je nakonfigurována pro tento `sampler`.

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>Návratová hodnota

Float_4 obsahující barvu ohraničení.

##  <a name="get_filter_mode"></a> get_filter_mode

Vrátí režim filtru, který je nakonfigurovaný pro tento `sampler`.

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>Návratová hodnota

Režim filtru, který je nakonfigurován pro vzorkovač.

##  <a name="operator_eq"></a> operátor =

Přiřadí hodnotu jiného objektu vzorkovače existujícímu vzorkovači.

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
[1] zkopírujte operátor přiřazení `sampler` ke zkopírování do tohoto objektu `sampler`.

[2] přesuňte operátor přiřazení `sampler` k přesunutí do tohoto objektu `sampler`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tuto instanci vzorkovače.

## <a name="see-also"></a>Viz také:

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
