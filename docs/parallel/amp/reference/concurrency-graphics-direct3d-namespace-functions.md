---
title: 'Funkce oboru názvů Concurrency::Graphics:: Direct3D'
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 18fb409b033ea14c3a140ea6600fc43cf3a8d603
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405544"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Funkce oboru názvů Concurrency::Graphics:: Direct3D

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

##  <a name="get_sampler"></a>  get_sampler –

Získejte rozhraní stavu D3D vzorkování pro dané akcelerátoru zobrazení, které představuje zadaný objekt vzorkovače.

```
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Zobrazení akcelerátoru D3D, na kterém má být vytvořen stavu odběrového zařízení D3D.

*_Sampler*<br/>
Objekt vzorkovače, pro kterou je vytvořena základní rozhraní D3D stavu vzorkování.

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní IUnknown odpovídá stavu odběrového zařízení D3D, který představuje dané vzorkování.

##  <a name="get_texture"></a>  get_texture

Získá rozhraní textury Direct3D základního zadaného [textury](texture-class.md) objektu.

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

*value_type*<br/>
Typ elementu textury.

*_Rank*<br/>
Řád textury.

*_Texture*<br/>
Textura nebo zobrazení textury asociované se accelerator_view, pro které je vráceno základní rozhraní textury Direct3D.

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní IUnknown odpovídající textuře rozhraní Direct3D podkládající texturu.

##  <a name="make_sampler"></a>  make_sampler –

Vytvořte vzorkovač z ukazatele na rozhraní stavu vzorkovníku D3D.

```
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_D3D_sampler*<br/>
Ukazatel na rozhraní IUnknown stavu vzorkování D3D na vytvořen.

### <a name="return-value"></a>Návratová hodnota

Vzorkování představuje zadaný stav vzorkování D3D.

##  <a name="make_texture"></a>  make_texture

Vytvoří [textury](texture-class.md) objektu pomocí zadaných parametrů.

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

*value_type*<br/>
Typ prvků v textuře.

*_Rank*<br/>
Řád textury.

*_Av*<br/>
Zobrazení akcelerátoru D3D, na kterém se má vytvořit texturu.

*_D3D_texture*<br/>
Ukazatel na rozhraní IUnknown textury D3D, vytvořte textur z.

*_View_format*<br/>
Použitý formát DXGI pro zobrazení vytvořené z této textury. Předání DXGI_FORMAT_UNKNOWN (výchozí) pro odvození formátu od základní formy _D3D_texture a value_type této šablony. Zadaný formát musí být kompatibilní se základním formátem _D3D_texture.

### <a name="return-value"></a>Návratová hodnota

Textura používající poskytnutou texturu D3D.

##  <a name="msad4"></a>  msad4

Porovnává 4bajtovou referenční hodnotou a 8 zdrojovou hodnotou a shromažďuje vektor součtu 4. Každá částka odpovídá maskovanému součtu absolutních rozdílů různých zarovnání bytů mezi referenčními hodnotami a zdrojovou hodnotou.

```
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Referenční*<br/>
Referenční pole 4 bajtů v jedné hodnotě uint

*_Source*<br/>
Zdrojové pole 8 bajtů hodnoty ve vektoru dvou hodnot uint.

*_Accum*<br/>
Vektor 4 hodnot mají být přidány k maskovanému součtu absolutních rozdílů různých zarovnání bytů mezi referenčními hodnotami a zdrojovou hodnotou.

### <a name="return-value"></a>Návratová hodnota

Vrátí vektor součtu 4. Každá částka odpovídá maskovanému součtu absolutních rozdílů různých zarovnání bytů mezi referenčními hodnotami a zdrojovou hodnotou.

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics.h

**Namespace:** Concurrency::Graphics:: Direct3D

## <a name="see-also"></a>Viz také:

[Concurrency::graphics::direct3d – obor názvů](concurrency-graphics-direct3d-namespace.md)
