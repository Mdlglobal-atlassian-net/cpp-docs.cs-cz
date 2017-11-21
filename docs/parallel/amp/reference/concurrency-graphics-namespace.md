---
title: Concurrency::Graphics Namespace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AMP_GRAPHICS/Concurrency
dev_langs: C++
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ad53fea97c98f496d1140725f4232052e2f53d3b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics – obor názvů
Obor názvů grafiky poskytuje typy a funkce, které jsou určeny pro programováním grafiky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace graphics;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="namespaces"></a>Obory názvů  
  
|Název|Popis|  
|----------|-----------------|  
|[Concurrency::Graphics:: Direct3D – Namespace](concurrency-graphics-direct3d-namespace.md)|Poskytuje funkce pro Direct3D – zprostředkovatel komunikace s objekty.|  
  
### <a name="typedefs"></a>Typedefs  
  
|Název|Popis|  
|----------|-----------------|  
|`uint`|Typ elementu pro [uint_2 – třída](uint-2-class.md), [uint_3 – třída](uint-3-class.md), a [uint_4 – třída](uint-4-class.md). Definované jako `typedef unsigned int uint;`.|  
  
### <a name="enumerations"></a>Výčty  
  
|Název|Popis|  
|----------|-----------------|  
|[address_mode – výčet](concurrency-graphics-namespace-enums.md#address_mode).|Určuje adresu režimy podporované pro texture vzorkování.|  
|[filter_mode – výčet](concurrency-graphics-namespace-enums.md#filter_mode)|Určuje filtr režimy podporované pro texture vzorkování.|  
  
### <a name="classes"></a>Třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[Texture – třída](texture-class.md)|Texturou je agregační na accelerator_view v doméně rozsah data. Jedná se o kolekci proměnných, jednu pro každý prvek v doméně rozsah. Každá proměnná obsahuje hodnotu odpovídající primitivní typ C++ (bez znaménka int, int, float, double) nebo norm skalárního typu nebo unorm (definovanou v concurrency::graphics) nebo oprávněné krátké vektoru typy definované v concurrency::graphics.|  
|[writeonly_texture_view – třída](writeonly-texture-view-class.md)|Writeonly_texture_view poskytuje writeonly přístup k texturou.|  
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
|[sampler – třída](sampler-class.md)|Představuje konfiguraci sampler používá pro texture vzorkování.|  
|[short_vector – struktura](short-vector-structure.md)|Poskytuje základní implementaci krátké vektoru hodnot.|  
|[short_vector_traits – struktura](short-vector-traits-structure.md)|Poskytuje pro načtení délku a typ krátké vektoru.|  
|[texture_view – třída](texture-view-class.md)|Poskytuje přístup pro čtení a zápis do texturou.|  
  
### <a name="functions"></a>Funkce  
  
|Název|Popis|  
|----------|-----------------|  
|[kopírování](concurrency-graphics-namespace-functions.md#copy)|Přetíženo. Zkopíruje obsah texture zdrojové do cílové vyrovnávací paměti hostitele.|  
|[copy_async –](concurrency-graphics-namespace-functions.md#copy_async)|Přetíženo. Asynchronně zkopíruje obsah texture zdroje do vyrovnávací paměti cílového hostitele.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp_graphics.h  
  
 **Namespace:** souběžnosti  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
