---
title: "Implementace třídy IUnknown (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.Iunknown
dev_langs: C++
helpviewer_keywords: IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 34c0b46d8a7d89ca46dc4361fe85469bd64e538c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iunknown-implementation-classes"></a>Implementace třídy IUnknown
Následující třídy implementují **IUnknown** a související metody:  
  
-   [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) spravuje pro objekty agregované a neagregovaná při počítání referencí. Umožňuje zadat model vláken.  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) spravuje pro objekty agregované a neagregovaná při počítání referencí. Používá výchozí model serveru vláken.  
  
-   [CComAggObject](../atl/reference/ccomaggobject-class.md) implementuje **IUnknown** agregovaného objektu.  
  
-   [CComObject](../atl/reference/ccomobject-class.md) implementuje **IUnknown** neagregovaná objektu.  
  
-   [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementuje **IUnknown** pro agregované a neagregovaná objekty. Pomocí `CComPolyObject` tomu není nutné i `CComAggObject` a `CComObject` v modulu. Jediný `CComPolyObject` objekt zpracovává agregované a neagregovaná případů.  
  
-   [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) implementuje **IUnknown** pro objekt neagregovaná beze změny počet modulů zámku.  
  
-   [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) implementuje **IUnknown** pro rozhraní úplné vypnutí.  
  
-   [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) implementuje **IUnknown** pro rozhraní "v mezipaměti" úplné vypnutí.  
  
-   [CComContainedObject](../atl/reference/ccomcontainedobject-class.md) implementuje **IUnknown** pro vnitřní objekt agregace nebo rozhraní úplné vypnutí.  
  
-   [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) spravuje počet odkazů na modul zajistit objektu se neodstraní.  
  
-   [CComObjectStack](../atl/reference/ccomobjectstack-class.md) vytvoří dočasný objekt COM, pomocí kosterního provádění **IUnknown**.  
  
## <a name="related-articles"></a>Související články  
 [Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../atl/atl-class-overview.md)   
 [Agregace a makra objekt pro vytváření tříd](../atl/reference/aggregation-and-class-factory-macros.md)   
 [Makra COM Map](../atl/reference/com-map-macros.md)   
 [Globální funkce mapy modelu COM](../atl/reference/com-map-global-functions.md)

