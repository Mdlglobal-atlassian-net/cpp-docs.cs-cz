---
title: sampler – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 4f9788b62385f7c6f5eb82e3fbc69d63d3120cc2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="sampler-class"></a>sampler – třída
Sampler – třída agreguje informace o konfiguraci vzorkování má být použit pro texture vzorkování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class sampler;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[sampler – konstruktor](#ctor)|Přetíženo. Vytvoří instanci sampler.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[get_address_mode](#get_address_mode)|Vrátí `address_mode` který je přidružený k objektu sampler.|  
|[get_border_color](#get_border_color)|Vrátí barvu ohraničení, který je spojen s sampler objektu.|  
|[get_filter_mode](#get_filter_mode)|Vrátí `filter_mode` který je přidružený k objektu sampler.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operátor =](#operator_eq)|Přetíženo. Operátor přiřazení.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[address_mode](#address_mode)|Získá režim adresu `sampler` objektu.|  
|[border_color](#border_color)|Získá barvu ohraničení `sampler` objektu.|  
|[filter_mode](#filter_mode)|Získá režim filtru `sampler` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `sampler`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp_graphics.h  
  
 **Namespace:** concurrency::graphics  
  
##  <a name="ctor"></a> sampler 

 Vytvoří instanci objektu [sampler – třída](sampler-class.md).  
  
```  
sampler() restrict(cpu);

 *// [1] default constructor  
 
sampler(// [2] constructor  
    filter_mode _Filter_mode) restrict(cpu);

 
sampler(// [3] constructor  
    address_mode _Address_mode,  
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

 
sampler(// [4] constructor  
    filter_mode _Filter_mode,  
    address_mode _Address_mode,  
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

 
sampler(// [5] copy constructor  
    const sampler& _Other) restrict(amp,
    cpu);

 
sampler(// [6] move constructor  
    sampler&& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Filter_mode`  
 Režim filtru pro použití v vzorkování.  
  
 `_Address_mode`  
 Adresování režim, který se má použít v vzorkování pro všechny dimenze.  
  
 `_Border_color`  
 Barva ohraničení, který se má použít, pokud je režim adresu address_border. Výchozí hodnota je `float_4(0.0f, 0.0f, 0.0f, 0.0f)`.  
  
 `_Other`  
 [5] kopírovací konstruktor  
 `sampler` Objekt, který chcete zkopírovat do nové `sampler` instance.  
  
 [6] move – konstruktor  
 `sampler` Objekt, který chcete přesunout do nové `sampler` instance.  
  
##  <a name="address_mode"></a> address_mode 

 Získá režim adresu `sampler` objektu.  
  
```  
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;  
```  
  
##  <a name="border_color"></a> border_color 

 Získá barvu ohraničení `sampler` objektu.  
  
```  
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;  
```  
  
##  <a name="filter_mode"></a> filter_mode 

 Získá režim filtru `sampler` objektu.  
  
```  
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;  
```  
  
##  <a name="get_address_mode"></a> get_address_mode 

 Vrátí režim filtru, který je nakonfigurovaný pro tento `sampler`.  
  
```  
Concurrency::graphics::address_mode get_address_mode() const __GPU;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Režim adres, který je nakonfigurován pro ho.  
  
##  <a name="get_border_color"></a> get_border_color 

 Vrátí barvu ohraničení, který je nakonfigurovaný pro tento `sampler`.  
  
```  
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Float_4, který obsahuje barvu ohraničení.  
  
##  <a name="get_filter_mode"></a> get_filter_mode 

 Vrátí režim filtru, který je nakonfigurovaný pro tento `sampler`.  
  
```  
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Režim filtru, který je nakonfigurován pro ho.  
  
##  <a name="operator_eq"></a> operátor = 

 Hodnota jiného objektu sampler přiřadí existující sampler.  
  
```  
sampler& operator= (// [1] copy assignment operator const sampler& _Other) restrict(amp,
    cpu);

 
sampler& operator= (// [2] move assingment operator sampler&& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 [1] operátor přiřazení kopírování  
 `sampler` Objekt, který chcete zkopírovat do této `sampler`.  
  
 [2] operátor přiřazení přesunutí  
 `sampler` Objekt, který chcete přesunout do této `sampler`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na tuto instanci sampler.  
  
## <a name="see-also"></a>Viz také  
 [Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
