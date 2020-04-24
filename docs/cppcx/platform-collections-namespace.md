---
title: Platforma::Obor názvů kolekcí
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- collection/Platform::Collections
helpviewer_keywords:
- Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
ms.openlocfilehash: ab6b78f1b88c586a11276d36387fb42ea6ee667f
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032418"
---
# <a name="platformcollections-namespace"></a>Platforma::Obor názvů kolekcí

Obor názvů Platform::Collections `Map`obsahuje `MapView` `Vector`třídy `VectorView` , , a. Tyto třídy jsou konkrétní implementace odpovídající rozhraní, které jsou definovány v [systému Windows::Foundation::Collections](/uwp/api/windows.foundation.collections) oboru názvů. Typy kolekce betonové nejsou přenosné přes ABI (například když Javascript nebo C# program volá do komponenty C++), ale jsou implicitně převoditelné na jejich odpovídající typy rozhraní. Například pokud implementujete veřejnou metodu, která naplní a vrátí kolekci, pak použijte [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) k implementaci kolekce interně a použijte [Windows::Foundation::Collections::IVector](/uwp/api/windows.foundation.collections.ivector-1) jako návratový typ. Další informace naleznete v [tématu Kolekce](../cppcx/collections-c-cx.md) a [vytváření součástí prostředí Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Můžete vytvořit platformu::Collections::Vector z [std::vector](../standard-library/vector-class.md) a [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) from [a std::map](../standard-library/map-class.md).

Kromě toho platforma::Collections obor názvů poskytuje podporu pro zpět vložit `Vector` a `VectorView` vstupní iterátory a iterátory.

Chcete-li`#include`použít typy v oboru názvů Platform::Collections, musíte zahrnout hlavičku collection.h.

## <a name="syntax"></a>Syntaxe

```cpp
#include <collection.h>
using namespace Platform::Collections;
```

### <a name="members"></a>Členové

Tento obor názvů obsahuje následující členy.

|Název|Popis|
|----------|-----------------|
|[Platforma::Kolekce::BackInsertIterator Class](../cppcx/platform-collections-backinsertiterator-class.md)|Představuje iterátor, který vloží prvek na konci kolekce.|
|[Platform::Collections::InputIterator – třída](../cppcx/platform-collections-inputiterator-class.md)|Představuje iterátor, který vloží prvek na začátku kolekce.|
|[Platform::Collections::Map – třída](../cppcx/platform-collections-map-class.md)|Představuje upravitelné kolekce párů klíč hodnota, které jsou přístupné klíč. Podobně jako [std::map](../standard-library/map-class.md).|
|[Platform::Collections::MapView – třída](../cppcx/platform-collections-mapview-class.md)|Představuje kolekci jen pro čtení párů klíč hodnota, které jsou přístupné pomocí klíče.|
|[Platform::Collections::Vector – třída](../cppcx/platform-collections-vector-class.md)|Představuje upravitelné posloupnosti prvků. Podobné [std::vector](../standard-library/vector-class.md).|
|[Platform::Collections::VectorIterator – třída](../cppcx/platform-collections-vectoriterator-class.md)|Představuje iterátor, který prochází `Vector` kolekce.|
|[Platform::Collections::VectorView – třída](../cppcx/platform-collections-vectorview-class.md)|Představuje posloupnost prvků jen pro čtení.|
|[Platforma::Kolekce::Třída VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md)|Představuje iterátor, který prochází `VectorView` kolekce.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)

### <a name="requirements"></a>Požadavky

**Metadata:** platform.winmd

**Obor názvů:** Platforma::Kolekce

**Možnost kompilátoru:** /ZW

## <a name="see-also"></a>Viz také

[Obor názvů platformy](../cppcx/platform-namespace-c-cx.md)
