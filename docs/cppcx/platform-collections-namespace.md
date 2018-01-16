---
title: Platform::Collections Namespace | Microsoft Docs
ms.custom: 
ms.date: 01/25/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: collection/Platform::Collections
dev_langs: C++
helpviewer_keywords: Platform::Collections Namespace
ms.assetid: b5042864-5f22-40b7-b7a5-c0691f65cc47
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a93282a233f98d7a384d1fdad2ba6ca862e9e3f2
ms.sourcegitcommit: c2e990450ccd528d85b2783fbc63042612987cfd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2018
---
# <a name="platformcollections-namespace"></a>Platform::Collections Namespace
Obor názvů Platform::Collections obsahuje `Map`, `MapView`, `Vector`, a `VectorView` třídy. Tyto třídy jsou konkrétní implementace odpovídající rozhraní, které jsou definovány v [Windows::Foundation::Collections](http://go.microsoft.com/fwlink/p/?LinkId=262645) oboru názvů. Typy konkrétní kolekce nejsou přenosné napříč ABI (např. při Javascript nebo programu volání do komponent C++ C#), ale jsou implicitně převést na jejich odpovídající typy rozhraní. Například pokud budete implementovat veřejnou metodu, která naplní a vrátí kolekci, použijte [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) interně implementovat kolekce a použít [Windows::Foundation::Collections: : IVector](http://go.microsoft.com/fwlink/p/?LinkId=262410) jako návratový typ. Další informace najdete v tématu [kolekce](../cppcx/collections-c-cx.md) a [vytváření součásti systému Windows Runtime v jazyce C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md).  
  
 Můžete vytvořit Platform::Collections::Vector z [std::vector](../standard-library/vector-class.md) a [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) z [std::map](../standard-library/map-class.md).  
  
 Kromě toho obor názvů Platform::Collections poskytuje podporu pro zpětné vložení a vstupní iterátory a `Vector` a `VectorView` iterátory.  
  
 Musí zahrnovat (`#include`) collection.h hlavičky k použít typy v oboru názvů Platform::Collections.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
#include <collection.h>  
using namespace Platform::Collections;  
```  
  
### <a name="members"></a>Členové  
 Tento obor názvů obsahuje následující členy.  
  
|Název|Popis|  
|----------|-----------------|  
|[Platform::Collections::BackInsertIterator – třída](../cppcx/platform-collections-backinsertiterator-class.md)|Představuje iterátor, který vloží prvek na konec kolekce.|  
|[Platform::Collections::InputIterator – třída](../cppcx/platform-collections-inputiterator-class.md)|Představuje iterátor, který vloží prvek na začátek kolekce.|  
|[Platform::Collections::Map – třída](../cppcx/platform-collections-map-class.md)|Představuje kolekci upravitelnými páry klíč hodnota, které jsou přístupné pomocí klíče. Podobně jako [std::map](../standard-library/map-class.md).|  
|[Platform::Collections::MapView – třída](../cppcx/platform-collections-mapview-class.md)|Představuje kolekci páry klíč hodnota, které jsou přístupné pomocí klíče jen pro čtení.|  
|[Platform::Collections::Vector – třída](../cppcx/platform-collections-vector-class.md)|Představuje upravitelnými pořadí elementů. Podobně jako [std::vector](../standard-library/vector-class.md).|  
|[Platform::Collections::VectorIterator – třída](../cppcx/platform-collections-vectoriterator-class.md)|Představuje iterátor, který prochází `Vector` kolekce.|  
|[Platform::Collections::VectorView – třída](../cppcx/platform-collections-vectorview-class.md)|Představuje jen pro čtení pořadí elementů.|  
|[Platform::Collections::VectorViewIterator – třída](../cppcx/platform-collections-vectorviewiterator-class.md)|Představuje iterátor, který prochází `VectorView` kolekce.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Obor názvů Platform](../cppcx/platform-namespace-c-cx.md)  
  
### <a name="requirements"></a>Požadavky  
 **Metadata:** platform.winmd  
  
 **Namespace:** Platform::Collections  
  
 **– Možnost kompilátoru:** /ZW  
  
## <a name="see-also"></a>Viz také  
 [Namespace platformy](../cppcx/platform-namespace-c-cx.md)
