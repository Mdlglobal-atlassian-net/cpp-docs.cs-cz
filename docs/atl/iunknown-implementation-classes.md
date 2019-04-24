---
title: Implementace třídy IUnknown (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
ms.openlocfilehash: 26751c013d65142393377394006a9833e6c8f7bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261888"
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

## <a name="see-also"></a>Viz také:

[Přehled tříd](../atl/atl-class-overview.md)<br/>
[Agregační makra a makra objektu pro vytváření tříd](../atl/reference/aggregation-and-class-factory-macros.md)<br/>
[Makra map COM](../atl/reference/com-map-macros.md)<br/>
[Globální funkce mapy modelu COM](../atl/reference/com-map-global-functions.md)
