---
title: Concurrency::graphics::direct3d – obor názvů
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d
- amp_short_vectors/Concurrency::graphics::direct3d
ms.assetid: be283331-07cf-46e4-91a1-e8aa85d4ec8e
ms.openlocfilehash: 4911787fd17877769eb723cf1e61e29fe626a783
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139428"
---
# <a name="concurrencygraphicsdirect3d-namespace"></a>Concurrency::graphics::direct3d – obor názvů

Poskytuje metody [get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture) a [make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture) .

## <a name="syntax"></a>Syntaxe

```cpp
namespace direct3d;
```

## <a name="members"></a>Členové

### <a name="functions"></a>Funkce

|Název<br /><br /> Popis|
|--------------------------|
|[get_sampler](concurrency-graphics-direct3d-namespace-functions.md#get_sampler)<br /><br /> Získejte rozhraní stavu vzorkování Direct3D pro dané zobrazení akcelerátoru, které představuje zadaný objekt vzorkovače.|
|[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)<br /><br /> Získá rozhraní textury Direct3D, které je podkladem zadaného objektu [textury](texture-class.md) .|
|[make_sampler](concurrency-graphics-direct3d-namespace-functions.md#make_sampler)<br /><br /> Vytvoří vzorkovník z ukazatele rozhraní stavu vzorkovače Direct3D.|
|[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)<br /><br /> Vytvoří objekt [textury](texture-class.md) pomocí zadaných parametrů.|
|[msad4](concurrency-graphics-direct3d-namespace-functions.md#msad4)<br /><br /> Porovná referenční hodnotu o velikosti 4 bajty a 8 bajtů zdrojové hodnoty a shromáždí vektor 4 součtů.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_graphics. h

**Obor názvů:** Concurrency:: Graphics

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
