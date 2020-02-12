---
title: Funkce oboru názvů Concurrency::graphics::direct3d
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 665732700ee6b85425f332a0eb96a5b75864a74e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126965"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Funkce oboru názvů Concurrency::graphics::direct3d

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

## <a name="get_sampler"></a>get_sampler

Získejte rozhraní stavu vzorkovače D3D pro dané zobrazení akcelerátoru, které představuje zadaný objekt vzorkovače.

```cpp
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Zobrazení akcelerátoru D3D, na kterém má být vytvořen stav vzorkovače D3D.

*_Sampler*<br/>
Objekt vzorkovače, pro který se vytvoří základní rozhraní stavu vzorkovače D3D.

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní IUnknown odpovídající stavu vzorkovače D3D, který představuje dané vzorkovače.

## <a name="get_texture"></a>get_texture

Získá rozhraní textury Direct3D, které je podkladem zadaného objektu [textury](texture-class.md) .

```cpp
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
Typ prvku textury.

*_Rank*<br/>
Rozměr textury.

*_Texture*<br/>
Textura nebo zobrazení textury přidružené k accelerator_view, pro kterou je vráceno základní rozhraní Direct3D textur.

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní IUnknown odpovídající Texture Direct3D podkladové textury.

## <a name="make_sampler"></a>make_sampler

Vytvoří vzorkovník z ukazatele rozhraní stavu vzorkovače D3D.

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_D3D_sampler*<br/>
Ukazatel rozhraní IUnknown stavu vzorkování D3D, ze kterého se má vytvořit vzorkovník.

### <a name="return-value"></a>Návratová hodnota

Vzorkovník představuje zadaný stav vzorkování D3D.

## <a name="make_texture"></a>make_texture

Vytvoří objekt [textury](texture-class.md) pomocí zadaných parametrů.

```cpp
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
Rozměr textury.

*_Av*<br/>
Zobrazení akcelerátoru D3D, na kterém má být textura vytvořena.

*_D3D_texture*<br/>
Ukazatel rozhraní IUnknown textury D3D, ze kterého se má textura vytvořit

*_View_format*<br/>
Formát DXGI, který se má použít pro zobrazení vytvořená z této textury. Předat DXGI_FORMAT_UNKNOWN (výchozí) pro odvození formátu z podkladového formátu _D3D_texture a value_type této šablony. Poskytnutý formát musí být kompatibilní s podkladovým formátem _D3D_texture.

### <a name="return-value"></a>Návratová hodnota

Textura používající zadanou texturu D3D.

## <a name="msad4"></a>msad4

Porovná referenční hodnotu o velikosti 4 bajty a 8 bajtů zdrojové hodnoty a shromáždí vektor 4 součtů. Každý součet odpovídá maskovanému součtu absolutních rozdílů různých zarovnání bytů mezi referenční hodnotou a zdrojovou hodnotou.

```cpp
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Reference*<br/>
Referenční pole 4 bajtů v jedné hodnotě uint

*_Source*<br/>
Zdrojové pole 8 bajtů v vektoru dvou hodnot uint.

*_Accum*<br/>
Vektor ze 4 hodnot, které mají být přidány do maskovaného součtu absolutních rozdílů mezi Referenční a zdrojovou hodnotou v různých bajtech.

### <a name="return-value"></a>Návratová hodnota

Vrátí Vektor o 4 součtech. Každý součet odpovídá maskovanému součtu absolutních rozdílů různých zarovnání bytů mezi referenční hodnotou a zdrojovou hodnotou.

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics. h

**Obor názvů:** Concurrency:: Graphics::d irect3d

## <a name="see-also"></a>Viz také

[Concurrency::graphics::direct3d – obor názvů](concurrency-graphics-direct3d-namespace.md)
