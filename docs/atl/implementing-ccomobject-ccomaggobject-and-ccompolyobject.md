---
title: Implementace CComObject CComAggObject a CComPolyObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CComPolyObject
- CComAggObject
- CComObject
dev_langs: C++
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb74d68bb8974f820ac09a0c56930d835a3fe7f3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>Implementace CComObject CComAggObject a CComPolyObject
Třídy šablon [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), a [CComPolyObject](../atl/reference/ccompolyobject-class.md) jsou vždy maximální odvozené funkcí v řetězu dědičnosti. Je zodpovídají za zpracovávaly všechny metody v **IUnknown**: `QueryInterface`, `AddRef`, a **verze**. Kromě toho `CComAggObject` a `CComPolyObject` (při použití pro agregované objekty) zadejte počítání speciální odkazů a `QueryInterface` sémantiku požadované pro vnitřní neznámý.  
  
 Jestli `CComObject`, `CComAggObject`, nebo `CComPolyObject` slouží závisí na tom, jestli deklarovat jednu (nebo none) následující makra:  
  
|– Makro|Efekt|  
|-----------|------------|  
|`DECLARE_NOT_AGGREGATABLE`|Vždy používá `CComObject`.|  
|`DECLARE_AGGREGATABLE`|Používá `CComAggObject` Pokud je objekt agregován a `CComObject` Pokud není. `CComCoClass`obsahuje tato makro, pokud žádná z **DECLARE_\*_AGGREGATABLE** makra jsou deklarované v třídě, bude výchozí.|  
|`DECLARE_ONLY_AGGREGATABLE`|Vždy používá `CComAggObject`. Vrátí chybu, pokud objekt nejsou agregovány.|  
|`DECLARE_POLY_AGGREGATABLE`|ATL vytvoří instanci **CComPolyObject\<CYourClass >** při **IClassFactory::CreateInstance** je volána. Během vytváření se kontroluje hodnota vnější neznámý. Pokud je **NULL**, **IUnknown** je implementována pro objekt neagregovaná. Pokud vnější Neznámý není **NULL**, **IUnknown** je implementována pro agregovaný objekt.|  
  
 Výhodou použití `CComAggObject` a `CComObject` je, že implementace **IUnknown** je optimalizovaná pro druh objektu vytváří. Například objekt neagregovaná stačí počet odkazů, při musí agregovaný objekt počet odkazů pro vnitřní neznámý a ukazatel na vnější neznámý.  
  
 Výhodou použití `CComPolyObject` je vyhnout se nutnosti obě `CComAggObject` a `CComObject` v modulu pro zpracování agregované a neagregovaná případy. Jediný `CComPolyObject` objekt zpracovává obou případech. To znamená, že pouze jedna kopie tabulce vtable a jednu kopii funkce existují v modulu. Pokud vaše vtable velká, může to podstatně snížit velikost vašeho modulu. Ale pokud je vaše vtable malá, pomocí `CComPolyObject` může způsobit něco větší velikost modulu, protože není optimalizována pro agregovaná nebo neagregovaná objekt, jako jsou `CComAggObject` a `CComObject`.  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL COM – objekty](../atl/fundamentals-of-atl-com-objects.md)   
 [Agregace a makra objekt pro vytváření tříd](../atl/reference/aggregation-and-class-factory-macros.md)

