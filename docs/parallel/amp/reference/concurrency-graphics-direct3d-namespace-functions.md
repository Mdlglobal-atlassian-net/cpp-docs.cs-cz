---
title: 'Concurrency::Graphics:: Direct3D – obor názvů funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
dev_langs:
- C++
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ed95ed8df8a42dc62684c71a3005c2f33fecd18
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686331"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Funkce Concurrency::Graphics:: Direct3D – obor názvů
||||  
|-|-|-|  
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|  
|[make_texture](#make_texture)|[msad4](#msad4)|  

 
##  <a name="get_sampler"></a>  get_sampler –  
 Get rozhraní D3D sampler stavu na danou akcelerátoru zobrazit tento představuje sampler zadaný objekt.  
  
```  
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,  
    const sampler& _Sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Av`  
 Zobrazení akcelerátoru D3D, na kterém má být vytvořen D3D sampler stavu.  
  
 `_Sampler`  
 Objekt sampler, pro kterou je vytvořen základní rozhraní stavu sampler D3D.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní IUnknown odpovídající stav sampler D3D, který představuje daný sampler.  
  
##  <a name="get_texture"></a>  get_texture –  
 Získá rozhraní texture Direct3D – základní zadaný [texture](texture-class.md) objektu.  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const texture<value_type, _Rank>& _Texture) restrict(cpu);

 
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const writeonly_texture_view<value_type, _Rank>& _Texture) restrict(cpu);

 
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const texture_view<value_type, _Rank>& _Texture) restrict(cpu);

 
```  
  
### <a name="parameters"></a>Parametry  
 `value_type`  
 Typ elementu textury.  
  
 `_Rank`  
 Pořadí textury.  
  
 `_Texture`  
 Texture nebo texture zobrazení související s accelerator_view, pro který je vrácen základní rozhraní texture Direct3D.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel rozhraní IUnknown odpovídající texture Direct3D – základní textury.  
  
##  <a name="make_sampler"></a>  make_sampler –  
 Vytvoření sampler z ukazatel D3D sampler stavu rozhraní.  
  
```  
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_D3D_sampler`  
 Ukazatel rozhraní IUnknown stavu sampler D3D vytvořit sampler z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Sampler představuje zadaný stav sampler D3D.  
  
##  <a name="make_texture"></a>  make_texture –  
 Vytvoří [texture](texture-class.md) objektu s použitím zadaných parametrů.  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
texture<value_type, _Rank> make_texture(
    const Concurrency::accelerator_view& _Av,  
    _In_ IUnknown* _D3D_texture,  
    DXGI_FORMAT _View_format = DXGI_FORMAT_UNKNOWN) restrict(cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `value_type`  
 Typ elementů v textury.  
  
 `_Rank`  
 Pořadí textury.  
  
 `_Av`  
 Zobrazení akcelerátoru D3D, na kterém má být vytvořen textury.  
  
 `_D3D_texture`  
 Ukazatel rozhraní IUnknown textury D3D textury od vytvoření.  
  
 `_View_format`  
 Formát DXGI, který se má použít pro zobrazení vytvořené z této texture. Předejte DXGI_FORMAT_UNKNOWN (výchozí) odvození formát od základní formát _D3D_texture a value_type této šablony. Zadaný formát musí být kompatibilní s základní formát _D3D_texture.  
  
### <a name="return-value"></a>Návratová hodnota  
 Texture, pomocí zadané texture D3D.  
  
##  <a name="msad4"></a>  msad4  
 Porovná 4bajtový referenční hodnotu a hodnotu 8bajtový zdroje a shromažďuje vektor 4 součtů. Každý součet odpovídá maskované součet různých bajtů zarovnání absolutní rozdíly mezi hodnota odkazu a zdrojové hodnoty.  
  
```  
inline uint4 msad4(
    uint _Reference,  
    uint2 _Source,  
    uint4 _Accum) restrict(amp);
```  
  
### <a name="parameters"></a>Parametry  
 `_Reference`  
 Odkaz na pole 4 bajtů jednu hodnotu Celé_číslo  
  
 `_Source`  
 Zdrojové pole 8 bajtů u funkce vector ze dvou hodnot celé_číslo.  
  
 `_Accum`  
 Vektor 4 hodnoty pro přidání do maskované součet zarovnání různých bajtů absolutní rozdíly mezi hodnota odkazu a zdrojové hodnoty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí vektor 4 součtů. Každý součet odpovídá maskované součet různých bajtů zarovnání absolutní rozdíly mezi hodnota odkazu a zdrojové hodnoty.  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp_graphics.h  
  
 **Namespace:** Concurrency::Graphics:: Direct3D – 

## <a name="see-also"></a>Viz také  
 [Concurrency::graphics::direct3d – obor názvů](concurrency-graphics-direct3d-namespace.md)
