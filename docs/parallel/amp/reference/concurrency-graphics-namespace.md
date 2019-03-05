---
title: Concurrency::graphics – obor názvů
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: ef61c93e062b375377a0afe62aa7f622f6c0d4ac
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326529"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics – obor názvů

Obor názvů graphics poskytuje typy a funkce, které jsou navržené pro grafické programování.

## <a name="syntax"></a>Syntaxe

```
namespace graphics;
```

## <a name="members"></a>Členové

### <a name="namespaces"></a>Jmenné prostory

|Název|Popis|
|----------|-----------------|
|[Concurrency::graphics::direct3d – obor názvů](concurrency-graphics-direct3d-namespace.md)|Poskytuje funkce pro spolupráci s Direct3D.|

### <a name="typedefs"></a>Typedefs

|Název|Popis|
|----------|-----------------|
|`uint`|Typ elementu pro [uint_2 – třída](uint-2-class.md), [uint_3 – třída](uint-3-class.md), a [uint_4 – třída](uint-4-class.md). Definuje jako `typedef unsigned int uint;`.|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[address_mode Enumeration](concurrency-graphics-namespace-enums.md#address_mode).|Určuje režimy adresy podporované pro vzorkování textury.|
|[filter_mode Enumeration](concurrency-graphics-namespace-enums.md#filter_mode)|Určuje režimy filtrování podporované pro vzorkování textury.|

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[texture – třída](texture-class.md)|Textura je souhrn dat na objektu accelerator_view v rozšířené doméně. Jde o kolekci proměnných, jedna pro každý prvek v rozšířené doméně. Každá proměnná obsahuje hodnotu odpovídající primitivnímu typu jazyka C++ (unsigned int, int, float, double) nebo skalárním typům norm a unorm (definovaných v oboru názvů concurrency::graphics) nebo způsobilým vektorovým typům, které jsou definovány v oboru názvů concurrency::graphics.|
|[writeonly_texture_view – třída](writeonly-texture-view-class.md)|Třída writeonly_texture_view poskytuje přístup typu writeonly k textuře.|
|[double_2 – třída](double-2-class.md)|Představuje krátký vektor 2 `double` hodnoty.|
|[double_3 – třída](double-3-class.md)|Představuje krátký vektor 3 `double` hodnoty.|
|[double_4 – třída](double-4-class.md)|Představuje krátký vektor 4 `double` hodnoty.|
|[float_2 – třída](float-2-class.md)|Představuje krátký vektor 2 `float` hodnoty.|
|[float_3 – třída](float-3-class.md)|Představuje krátký vektor 3 `float` hodnoty.|
|[float_4 – třída](float-4-class.md)|Představuje krátký vektor 4 `float` hodnoty.|
|[int_2 – třída](int-2-class.md)|Představuje krátký vektor 2 `int` hodnoty.|
|[int_3 – třída](int-3-class.md)|Představuje krátký vektor 3 `int` hodnoty.|
|[int_4 – třída](int-4-class.md)|Představuje krátký vektor 4 `int` hodnoty.|
|[norm_2 – třída](norm-2-class.md)|Představuje krátký vektor 2 `norm` hodnoty.|
|[norm_3 – třída](norm-3-class.md)|Představuje krátký vektor 3 `norm` hodnoty.|
|[norm_4 – třída](norm-4-class.md)|Představuje krátký vektor 4 `norm` hodnoty.|
|[uint_2 – třída](uint-2-class.md)|Představuje krátký vektor 2 `uint` hodnoty.|
|[uint_3 – třída](uint-3-class.md)|Představuje krátký vektor 3 `uint` hodnoty.|
|[uint_4 – třída](uint-4-class.md)|Představuje krátký vektor 4 `uint` hodnoty.|
|[unorm_2 – třída](unorm-2-class.md)|Představuje krátký vektor 2 `unorm` hodnoty.|
|[unorm_3 – třída](unorm-3-class.md)|Představuje krátký vektor 3 `unorm` hodnoty.|
|[unorm_4 – třída](unorm-4-class.md)|Představuje krátký vektor 4 `unorm` hodnoty.|
|[sampler – třída](sampler-class.md)|Představuje konfiguraci vzorkovače pro vzorkování textur.|
|[short_vector – struktura](short-vector-structure.md)|Poskytuje základní implementaci krátkého vektoru hodnot.|
|[short_vector_traits – struktura](short-vector-traits-structure.md)|Poskytuje prostředek pro získání délky a typu krátkého vektoru.|
|[texture_view – třída](texture-view-class.md)|Poskytuje přístup pro čtení a zápisu do textury.|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[kopírování](concurrency-graphics-namespace-functions.md#copy)|Přetíženo. Zkopíruje obsah zdrojové textury do vyrovnávací paměti cílového hostitele.|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|Přetíženo. Asynchronně zkopíruje obsah zdrojové textury do vyrovnávací paměti cílového hostitele.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics.h

**Namespace:** Souběžnost

## <a name="see-also"></a>Viz také:

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
