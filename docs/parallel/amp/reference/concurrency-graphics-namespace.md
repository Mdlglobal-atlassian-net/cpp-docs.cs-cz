---
title: Concurrency::graphics – obor názvů
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: c7e3b245c8d9e6ba0c563a63910fadd678523087
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139440"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics – obor názvů

Obor názvů Graphics poskytuje typy a funkce navržené pro grafické programování.

## <a name="syntax"></a>Syntaxe

```cpp
namespace graphics;
```

## <a name="members"></a>Členové

### <a name="namespaces"></a>Obory názvů

|Název|Popis|
|----------|-----------------|
|[Concurrency::graphics::direct3d – obor názvů](concurrency-graphics-direct3d-namespace.md)|Poskytuje funkce pro interoperabilitu Direct3D.|

### <a name="typedefs"></a>Typedefs

|Název|Popis|
|----------|-----------------|
|`uint`|Typ prvku pro třídu [uint_2](uint-2-class.md), [Uint_3 třídu](uint-3-class.md)a [třídu uint_4](uint-4-class.md). Definováno jako `typedef unsigned int uint;`.|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[výčet address_mode](concurrency-graphics-namespace-enums.md#address_mode).|Určuje režimy adres podporované pro vzorkování textury.|
|[Výčet filter_mode](concurrency-graphics-namespace-enums.md#filter_mode)|Určuje režimy filtrování podporované pro vzorkování textury.|

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[texture – třída](texture-class.md)|Textura je datová agregace na accelerator_view v rozsahu domény. Jedná se o kolekci proměnných, jednu pro každý prvek v doméně rozsahu. Každá proměnná obsahuje hodnotu odpovídající C++ primitivnímu typu (unsigned int, int, float, Double) nebo skalárního typu Standard nebo unorm (definované v Concurrency:: Graphics) nebo pro typy krátkých vektorů definovaných v Concurrency:: Graphics.|
|[writeonly_texture_view – třída](writeonly-texture-view-class.md)|Writeonly_texture_view poskytuje přístup WriteOnly k textuře.|
|[double_2 – třída](double-2-class.md)|Představuje krátký vektor dvou `double`ch hodnot.|
|[double_3 – třída](double-3-class.md)|Představuje krátký vektor tří hodnot `double`.|
|[double_4 – třída](double-4-class.md)|Představuje krátký vektor 4 `double` hodnot.|
|[float_2 – třída](float-2-class.md)|Představuje krátký vektor dvou `float`ch hodnot.|
|[float_3 – třída](float-3-class.md)|Představuje krátký vektor tří hodnot `float`.|
|[float_4 – třída](float-4-class.md)|Představuje krátký vektor 4 `float` hodnot.|
|[int_2 – třída](int-2-class.md)|Představuje krátký vektor dvou `int`ch hodnot.|
|[int_3 – třída](int-3-class.md)|Představuje krátký vektor tří hodnot `int`.|
|[int_4 – třída](int-4-class.md)|Představuje krátký vektor 4 `int` hodnot.|
|[norm_2 – třída](norm-2-class.md)|Představuje krátký vektor dvou `norm`ch hodnot.|
|[norm_3 – třída](norm-3-class.md)|Představuje krátký vektor tří hodnot `norm`.|
|[norm_4 – třída](norm-4-class.md)|Představuje krátký vektor 4 `norm` hodnot.|
|[uint_2 – třída](uint-2-class.md)|Představuje krátký vektor dvou `uint`ch hodnot.|
|[uint_3 – třída](uint-3-class.md)|Představuje krátký vektor tří hodnot `uint`.|
|[uint_4 – třída](uint-4-class.md)|Představuje krátký vektor 4 `uint` hodnot.|
|[unorm_2 – třída](unorm-2-class.md)|Představuje krátký vektor dvou `unorm`ch hodnot.|
|[unorm_3 – třída](unorm-3-class.md)|Představuje krátký vektor tří hodnot `unorm`.|
|[unorm_4 – třída](unorm-4-class.md)|Představuje krátký vektor 4 `unorm` hodnot.|
|[sampler – třída](sampler-class.md)|Představuje konfiguraci vzorkovače použitou pro vzorkování textury.|
|[short_vector – struktura](short-vector-structure.md)|Poskytuje základní implementaci krátkého vektoru hodnot.|
|[short_vector_traits – struktura](short-vector-traits-structure.md)|Poskytuje pro načtení délky a typu krátkého vektoru.|
|[texture_view – třída](texture-view-class.md)|Poskytuje přístup pro čtení a zápis k texturě.|

### <a name="functions"></a>Functions

|Název|Popis|
|----------|-----------------|
|[kopií](concurrency-graphics-namespace-functions.md#copy)|Přetíženo. Zkopíruje obsah zdrojové textury do vyrovnávací paměti cílového hostitele.|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|Přetíženo. Asynchronně zkopíruje obsah zdrojové textury do vyrovnávací paměti cílového hostitele.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics. h

**Obor názvů:** Concurrency

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
