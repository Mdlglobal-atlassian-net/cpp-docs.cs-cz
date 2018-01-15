---
title: "texture_view – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7ed3f9adb564676d54e06152bfd7d277c4a5d952
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="textureview-class"></a>texture_view – třída
Poskytuje přístup pro čtení a zápis do texturou. `texture_view`můžete použít pouze ke čtení textury, jehož typ hodnoty je `int`, `unsigned int`, nebo `float` mají výchozí 32-bit bpse. Číst ostatní formáty texture, použijte `texture_view<const value_type, _Rank>`.  
  
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
 `value_type`  
 Typ elementů v texture agregace.  
  
 `_Rank`  
 Pořadí `texture_view`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`value_type`|Typ elementů v texture agregace.|  
|`coordinates_type`|Typ souřadnice slouží k zadání texel v `texture_view`– to znamená, `short_vector` má stejné pořadí jako související texture, který má hodnotu typ `float`.|  
|`gather_return_type`|Návratový typ použitý pro shromažďování operations – to znamená, pořadí 4 `short_vector` , blokování čtyřmi součástmi homogenního barva shromáždit ze čtyř hodnot texel vzorků.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[texture_view – konstruktor](#ctor)|Přetíženo. Vytvoří `texture_view` instance.|  
|[~ texture_view – destruktor](#ctor)|Zničí `texture_view` instance.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[gather_alpha](#gather_alpha)|Přetíženo. Ukázky texture v zadaných souřadnic pomocí zadané vzorkování konfigurace a vrátí alpha (w) součástí čtyři jen Vzorkovaná texels.|  
|[gather_blue](#gather_blue)|Přetíženo. Ukázky texture v zadaných souřadnic pomocí zadané vzorkování konfigurace a vrátí blue (z) součástí čtyři jen Vzorkovaná texels.|  
|[gather_green](#gather_green)|Přetíženo. Ukázky texture v zadaných souřadnic pomocí zadané vzorkování konfigurace a vrátí zelený (y) součástí čtyři jen Vzorkovaná texels.|  
|[gather_red](#gather_red)|Přetíženo. Ukázky texture v zadaných souřadnic pomocí zadané vzorkování konfigurace a vrátí čtyři jen Vzorkovaná texels součásti červený (x).|  
|[get](#get)|Přetíženo. Získá hodnotu elementu index.|  
|[Ukázka](#sample)|Přetíženo. Ukázky texture v zadaných souřadnic a úroveň podrobností pomocí konfigurace zadané vzorkování.|  
|[set](#set)|Nastaví hodnotu elementu index.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[Operator() –](#operator_call)|Přetíženo. Získá hodnotu elementu index.|  
|[[] – operátor](#operator_at)|Přetíženo. Získá hodnotu elementu index.|  
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
  
##  <a name="dtor"></a>~ texture_view 

 Zničí `texture_view` instance.  
  
```  
~texture_view() restrict(amp, cpu);
```  
  
##  <a name="ctor"></a>texture_view 

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
 `_Src`  
 [1, 2] Konstruktor  
 `texture` Na kterém zapisovatelné `texture_view` je vytvořena.  
  
 [3, 4] Konstruktor  
 `texture` Na kterém umožňovat zápis `texture_view` je vytvořena.  
  
 `_Other`  
 [5] kopírovací konstruktor  
 Zdroj zapisovatelné `texture_view`.  
  
 [6, 7] Kopírovací konstruktor  
 Zdroj umožňovat zápis `texture_view`.  
  
 `_Mipmap_level`  
 Úroveň konkrétní mipmap ve zdroji `texture` to tomto zapisovatelné `texture_view` váže k. Výchozí hodnota je 0, která představuje úroveň mip nejvyšší úrovně (nejpodrobnější).  
  
 `_Most_detailed_mip`  
 TOP úroveň mip úroveň (nejpodrobnější) pro zobrazení, relativně k zadané `texture_view` objektu.  
  
 `_Mip_levels`  
 Počet úrovní mipmap přístupné prostřednictvím `texture_view`.  
  
##  <a name="gather_red"></a>gather_red 

 Ukázky texture v zadaných souřadnic pomocí zadané vzorkování konfigurace a vrátí čtyři jen Vzorkovaná texels součásti červený (x).  
  
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
 `_Address_mode`  
 Režim adresu používat ukázce `texture_view`. Adresa režim je stejný pro všechny dimenze.  
  
 `_Sampler`  
 Konfigurace sampler používat ukázce `texture_view`.  
  
 `_Coord`  
 Souřadnice provést ukázka z. Desetinné číslo souřadnic se používají promítnout mezi texels ukázka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pořadí 4 krátké vektor, který obsahuje komponentu červený (x) na 4 vzorkovat texel hodnoty.  
  
##  <a name="gather_green"></a>gather_green 

 Ukázky texture v zadaných souřadnic pomocí zadané vzorkování konfigurace a vrátí zelený (y) součástí čtyři jen Vzorkovaná texels.  
  
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
 `_Address_mode`  
 Režim adresu používat ukázce `texture_view`. Adresa režim je stejný pro všechny dimenze.  
  
 `_Sampler`  
 Konfigurace sampler používat ukázce `texture_view`.  
  
 `_Coord`  
 Souřadnice provést ukázka z. Desetinné číslo souřadnic se používají promítnout mezi texels ukázka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pořadí 4 krátké vektor, který obsahuje komponentu zelený (y) na 4 vzorkovat texel hodnoty.  
  
##  <a name="gather_blue"></a>gather_blue 

 Ukázky texture v zadaných souřadnic pomocí zadané vzorkování konfigurace a vrátí blue (z) součástí čtyři jen Vzorkovaná texels.  
  
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
 `_Address_mode`  
 Režim adresu používat ukázce `texture_view`. Adresa režim je stejný pro všechny dimenze.  
  
 `_Sampler`  
 Konfigurace sampler používat ukázce `texture_view`.  
  
 `_Coord`  
 Souřadnice provést ukázka z. Desetinné číslo souřadnic se používají promítnout mezi texels ukázka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pořadí 4 krátké vektor, který obsahuje komponentu červený (x) na 4 vzorkovat texel hodnoty.  
  
##  <a name="gather_alpha"></a>gather_alpha 

 Ukázky texture v zadaných souřadnic pomocí zadané vzorkování konfigurace a vrátí alpha (w) součástí čtyři jen Vzorkovaná texels.  
  
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
 `_Address_mode`  
 Režim adresu používat ukázce `texture_view`. Adresa režim je stejný pro všechny dimenze.  
  
 `_Sampler`  
 Konfigurace sampler používat ukázce `texture_view`.  
  
 `_Coord`  
 Souřadnice provést ukázka z. Desetinné číslo souřadnic se používají promítnout mezi texels ukázka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pořadí 4 krátké vector obsahující (w) součást na 4 vzorkovat texel hodnoty alfa.  
  
##  <a name="get"></a>GET 

 Získá hodnotu elementu v zadaném indexu.  
  
```  
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

 
value_type get(
    const index<_Rank>& _Index,  
    unsigned int _Mip_level = 0) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index elementu, který chcete získat, může být více dimenzí.  
  
 `_Mip_level`  
 Úroveň mipmap, ze kterého jsme měli získat hodnotu. Výchozí hodnota 0 představuje nejpodrobnější mipmap úrovni.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota elementu.  
  
##  <a name="operator_eq"></a>operátor = 

 Přiřadí zobrazení stejné struktury jako zadaná `texture_view` k tomuto `texture_view` instance.  
  
```  
texture_view<value_type, _Rank>& operator= (// [1] copy constructor  
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

 
texture_view<const value_type, _Rank>& operator= (// [2] copy constructor  
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

 
texture_view<const value_type, _Rank>& operator= (// [3] copy constructor  
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 [1, 2] Kopírovací konstruktor  
 Možností zápisu `texture_view` objektu.  
  
 [3] kopírovací konstruktor  
 Umožňovat zápis `texture_view` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `texture_view` instance.  
  
##  <a name="operator_at"></a>[] – operátor 

 Vrátí hodnotu elementu index.  
  
```  
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator[] (int _I0) const restrict(amp);

 
value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
value_type operator[] (int _I0) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index může být více dimenzí.  
  
 `_I0`  
 Jednorozměrná index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota elementu indexovat pomocí `_Index`.  
  
##  <a name="operator_call"></a>Operator() – 

 Vrátí hodnotu elementu index.  
  
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
 `_Index`  
 Index může být více dimenzí.  
  
 `_I0`  
 Většina významné součást index.  
  
 `_I1`  
 Další na většinu významné součást index.  
  
 `_I2`  
 Nejméně významným součást index.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota elementu indexovat pomocí `_Index`.  
  
##  <a name="sample"></a>Ukázka 

 Ukázky texture v zadaných souřadnic a úroveň podrobností pomocí konfigurace zadané vzorkování.  
  
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
 `_Filter_mode`  
 Režim filtru sloužící k ukázkové texture_view. Režim filtru je stejný pro minimalizaci, maximization a mipmap filtry.  
  
 `_Address_mode`  
 Režim adres sloužící k ukázkové texture_view. Adresa režim je stejný pro všechny dimenze.  
  
 `_Sampler`  
 Sampler konfigurace sloužící k ukázkové texture_view.  
  
 `_Coord`  
 Souřadnice provést ukázka z. Desetinné číslo souřadnic se používají promítnout mezi hodnotami texel.  
  
 `_Level_of_detail`  
 Hodnota určuje úroveň mipmap zkusit z. Promítnout mezi dvě úrovně mipmap se používají desetinné číslo. Výchozí úroveň podrobností je 0, což představuje nejpodrobnější mip úrovni.  
  
### <a name="return-value"></a>Návratová hodnota  
 Interpolované ukázkové hodnoty.  
  
##  <a name="set"></a>nastavení 

 Nastaví hodnotu elementu v zadaném indexu se zadanou hodnotou.  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) const restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Index`  
 Index elementu, který chcete nastavit, může být více dimenzí.  
  
 `value`  
 Hodnota k nastavení elementu.  
  
##  <a name="value_type"></a>value_type 

 Typ hodnoty elementů texture_view.  
  
```  
typedef typename const value_type value_type;  
```  
  
## <a name="see-also"></a>Viz také  
 [Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
