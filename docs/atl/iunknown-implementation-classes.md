---
title: Implementace třídy IUnknown (ATL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.atl.Iunknown
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
ms.openlocfilehash: 0a15a256f961d35f5153c11da6690f6908e08a52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484120"
---
# <a name="iunknown-implementation-classes"></a>Implementace třídy IUnknown

Následující třídy implementují `IUnknown` a související metody:

- [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) spravuje, neagregovaná i agregovaných objektů pro počítání odkazů. Umožňuje určit modelu vláken.

- [Ccomobjectroot –](../atl/reference/ccomobjectroot-class.md) spravuje, neagregovaná i agregovaných objektů pro počítání odkazů. Použije výchozí model serveru vláken.

- [CComAggObject](../atl/reference/ccomaggobject-class.md) implementuje `IUnknown` pro agregovaného objektu.

- [CComObject](../atl/reference/ccomobject-class.md) implementuje `IUnknown` pro neagregovaná objekt.

- [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje `IUnknown` agregované a neagregovaná objektů. Pomocí `CComPolyObject` díky tomu není nutné i `CComAggObject` a `CComObject` v modulu. Jediný `CComPolyObject` objekt zpracovává agregované a neagregovaná případy.

- [Ccomobjectnolock –](../atl/reference/ccomobjectnolock-class.md) implementuje `IUnknown` pro objekt neagregovaná beze změny počet zámků modulů.

- [Ccomtearoffobject –](../atl/reference/ccomtearoffobject-class.md) implementuje `IUnknown` pro rozhraní s odnímatelnými nabídkami.

- [Ccomcachedtearoffobject –](../atl/reference/ccomcachedtearoffobject-class.md) implementuje `IUnknown` "v mezipaměti" odtržených rozhraní.

- [Ccomcontainedobject –](../atl/reference/ccomcontainedobject-class.md) implementuje `IUnknown` pro vnitřní objekt agregace nebo rozhraní s odnímatelnými nabídkami.

- [Ccomobjectglobal –](../atl/reference/ccomobjectglobal-class.md) spravuje počet odkazů na modulu, aby váš objekt se neodstraní.

- [Ccomobjectstack –](../atl/reference/ccomobjectstack-class.md) vytvoří dočasný objekt modelu COM, pomocí základní implementace `IUnknown`.

## <a name="related-articles"></a>Související články

[Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)

## <a name="see-also"></a>Viz také

[Přehled tříd](../atl/atl-class-overview.md)<br/>
[Agregační makra a makra objektu pro vytváření tříd](../atl/reference/aggregation-and-class-factory-macros.md)<br/>
[Makra map COM](../atl/reference/com-map-macros.md)<br/>
[Globální funkce mapy modelu COM](../atl/reference/com-map-global-functions.md)

