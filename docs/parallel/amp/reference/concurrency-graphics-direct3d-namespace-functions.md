---
title: Funkce oboru názvů Concurrency::graphics::direct3d
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 330c1aa94b1d122901fc23576686032400249d31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376381"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Funkce oboru názvů Concurrency::graphics::direct3d

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

## <a name="get_sampler"></a><a name="get_sampler"></a>get_sampler

Získejte rozhraní stavu vzorkovače D3D v daném zobrazení akcelerátoru, které představuje zadaný objekt sampleru.

```cpp
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Av*<br/>
Zobrazení akcelerátoru D3D, na kterém má být vytvořen stav vzorkovače D3D.

*_Sampler*<br/>
Objekt sampler, pro který je vytvořeno základní rozhraní stavu vzorkovače D3D.

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní IUnknown odpovídající stavu vzorkovače D3D, který představuje daný sampler.

## <a name="get_texture"></a><a name="get_texture"></a>get_texture

Získá rozhraní textury Direct3D, které je základem zadaného objektu [textury.](texture-class.md)

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
Pořadí textury.

*_Texture*<br/>
Zobrazení textury nebo textury přidružené k accelerator_view, pro které je vráceno základní rozhraní textury Direct3D.

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní IUnknown odpovídající struktuře Direct3D, která je základem textury.

## <a name="make_sampler"></a><a name="make_sampler"></a>make_sampler

Vytvořte sampler z ukazatele rozhraní stavu vzorkovače D3D.

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_D3D_sampler*<br/>
IUnknown ukazatel rozhraní d3D sampler stavu k vytvoření sampler z.

### <a name="return-value"></a>Návratová hodnota

Sampler představuje zadaný stav vzorkovače D3D.

## <a name="make_texture"></a><a name="make_texture"></a>make_texture

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
Pořadí textury.

*_Av*<br/>
Zobrazení akcelerátoru D3D, ve kterém má být textura vytvořena.

*_D3D_texture*<br/>
INeznámý ukazatel rozhraní textury D3D k vytvoření textury z.

*_View_format*<br/>
Formát DXGI pro zobrazení vytvořená z této textury. Předajte DXGI_FORMAT_UNKNOWN (výchozí) k odvození formátu z podkladového formátu _D3D_texture a value_type této šablony. Poskytnutý formát musí být kompatibilní se základním formátem _D3D_texture.

### <a name="return-value"></a>Návratová hodnota

Textura pomocí poskytnuté textury D3D.

## <a name="msad4"></a><a name="msad4"></a>msad4

Porovná referenční hodnotu 4 bajtů a zdrojovou hodnotu 8 bajtů a akumuluje vektor 4 součty. Každý součet odpovídá maskovanému součtu absolutních rozdílů různých bajtových zarovnání mezi referenční hodnotou a zdrojovou hodnotou.

```cpp
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Reference*<br/>
Referenční pole 4 bajty v jedné hodnotě uint

*_Source*<br/>
Zdrojové pole 8 bajtů ve vektoru dvou hodnot uint.

*_Accum*<br/>
Vektor 4 hodnot, které mají být přidány k maskovanému součtu absolutních rozdílů různých zarovnání bajtů mezi referenční hodnotou a hodnotou zdroje.

### <a name="return-value"></a>Návratová hodnota

Vrátí vektor o 4 součty. Každý součet odpovídá maskovanému součtu absolutních rozdílů různých bajtových zarovnání mezi referenční hodnotou a zdrojovou hodnotou.

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics.h

**Obor názvů:** Souběžnost::grafika::direct3d

## <a name="see-also"></a>Viz také

[Souběžnost::grafika::direct3d Obor názvů](concurrency-graphics-direct3d-namespace.md)
