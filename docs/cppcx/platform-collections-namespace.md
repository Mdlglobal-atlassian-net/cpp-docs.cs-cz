---
title: Platform::Collections – Namespace
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
ms.openlocfilehash: 025c25d6c01ab9a28c68574cc2a13e09dbf28388
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480363"
---
# <a name="platformcollections-namespace"></a>Platform::Collections – Namespace

Platform::Collections – obor názvů obsahuje `Map`, `MapView`, `Vector`, a `VectorView` třídy. Tyto třídy jsou konkrétní implementace rozhraní, které jsou definovány v odpovídající [Windows::Foundation:: Collections –](/uwp/api/Windows.Foundation.Collections) oboru názvů. Konkrétní kolekci typů nejsou přenosné mezi ABI (třeba když Javascript nebo C# program zavolá komponent C++), ale jsou implicitně převést na jejich odpovídající typy rozhraní. Například, Pokud implementujete veřejnou metodu, která naplní a vrátí kolekci, použijte [Platform::Collections:: Vector –](../cppcx/platform-collections-vector-class.md) implementovat kolekci interně a použít [Windows::Foundation:: Collections –: : IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) jako návratový typ. Další informace najdete v tématu [kolekce](../cppcx/collections-c-cx.md) a [vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Platform::Collections:: Vector – od lze vytvořit [std::vector](../standard-library/vector-class.md) a [Platform::Collections:: map –](../cppcx/platform-collections-map-class.md) z [std::map](../standard-library/map-class.md).

Kromě toho Platform::Collections – obor názvů poskytuje podporu pro zpětné vložení a vstupní iterátory a `Vector` a `VectorView` iterátory.

Musí obsahovat (`#include`) hlavičku collection.h použít typy v Platform::Collections – obor názvů.

## <a name="syntax"></a>Syntaxe

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>Členové

Tento obor názvů obsahuje následující členy.

|Název|Popis|
|----------|-----------------|
|[Platform::Collections::BackInsertIterator – třída](../cppcx/platform-collections-backinsertiterator-class.md)|Představuje iterátor, který se vloží prvek na konec kolekce.|
|[Platform::Collections::InputIterator – třída](../cppcx/platform-collections-inputiterator-class.md)|Představuje iterátor, který se vloží prvek na začátku kolekce.|
|[Platform::Collections::Map – třída](../cppcx/platform-collections-map-class.md)|Představuje upravitelné kolekci párů klíč hodnota, které jsou přístupné pomocí klíče. Podobně jako [std::map](../standard-library/map-class.md).|
|[Platform::Collections::MapView – třída](../cppcx/platform-collections-mapview-class.md)|Představuje kolekci párů klíč hodnota, které jsou přístupné pomocí klíče jen pro čtení.|
|[Platform::Collections::Vector – třída](../cppcx/platform-collections-vector-class.md)|Představuje upravitelné sekvence prvků. Podobně jako [std::vector](../standard-library/vector-class.md).|
|[Platform::Collections::VectorIterator – třída](../cppcx/platform-collections-vectoriterator-class.md)|Představuje iterátor, který prochází skrz `Vector` kolekce.|
|[Platform::Collections::VectorView – třída](../cppcx/platform-collections-vectorview-class.md)|Představuje posloupnost prvků jen pro čtení.|
|[Platform::Collections::VectorViewIterator – třída](../cppcx/platform-collections-vectorviewiterator-class.md)|Představuje iterátor, který prochází skrz `VectorView` kolekce.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>Požadavky

**Metadata:** platform.winmd

**Namespace:** Platform::Collections –

**– Možnost kompilátoru:** /ZW

## <a name="see-also"></a>Viz také:

[Platforma Namespace](../cppcx/platform-namespace-c-cx.md)
