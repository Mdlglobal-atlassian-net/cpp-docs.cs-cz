---
title: Implementace CComObject CComAggObject a CComPolyObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CComPolyObject
- CComAggObject
- CComObject
dev_langs:
- C++
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ac45a6edbe606ba445ed3ae58cfde348f83e4de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>Implementace CComObject CComAggObject a CComPolyObject
Třídy šablon [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), a [CComPolyObject](../atl/reference/ccompolyobject-class.md) jsou vždy maximální odvozené funkcí v řetězu dědičnosti. Je zodpovídají za zpracovávaly všechny metody v **IUnknown**: `QueryInterface`, `AddRef`, a **verze**. Kromě toho `CComAggObject` a `CComPolyObject` (při použití pro agregované objekty) zadejte počítání speciální odkazů a `QueryInterface` sémantiku požadované pro vnitřní neznámý.  
  
 Jestli `CComObject`, `CComAggObject`, nebo `CComPolyObject` slouží závisí na tom, jestli deklarovat jednu (nebo none) následující makra:  
  
|– Makro|Efekt|  
|-----------|------------|  
|`DECLARE_NOT_AGGREGATABLE`|Vždy používá `CComObject`.|  
|`DECLARE_AGGREGATABLE`|Používá `CComAggObject` Pokud je objekt agregován a `CComObject` Pokud není. `CComCoClass` obsahuje tato makro, pokud žádná z **DECLARE_\*_AGGREGATABLE** makra jsou deklarované v třídě, bude výchozí.|  
|`DECLARE_ONLY_AGGREGATABLE`|Vždy používá `CComAggObject`. Vrátí chybu, pokud objekt nejsou agregovány.|  
|`DECLARE_POLY_AGGREGATABLE`|ATL vytvoří instanci **CComPolyObject\<CYourClass >** při **IClassFactory::CreateInstance** je volána. Během vytváření se kontroluje hodnota vnější neznámý. Pokud je **NULL**, **IUnknown** je implementována pro objekt neagregovaná. Pokud vnější Neznámý není **NULL**, **IUnknown** je implementována pro agregovaný objekt.|  
  
 Výhodou použití `CComAggObject` a `CComObject` je, že implementace **IUnknown** je optimalizovaná pro druh objektu vytváří. Například objekt neagregovaná stačí počet odkazů, při musí agregovaný objekt počet odkazů pro vnitřní neznámý a ukazatel na vnější neznámý.  
  
 Výhodou použití `CComPolyObject` je vyhnout se nutnosti obě `CComAggObject` a `CComObject` v modulu pro zpracování agregované a neagregovaná případy. Jediný `CComPolyObject` objekt zpracovává obou případech. To znamená, že pouze jedna kopie tabulce vtable a jednu kopii funkce existují v modulu. Pokud vaše vtable velká, může to podstatně snížit velikost vašeho modulu. Ale pokud je vaše vtable malá, pomocí `CComPolyObject` může způsobit něco větší velikost modulu, protože není optimalizována pro agregovaná nebo neagregovaná objekt, jako jsou `CComAggObject` a `CComObject`.  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL COM – objekty](../atl/fundamentals-of-atl-com-objects.md)   
 [Agregační makra a makra objektu pro vytváření tříd](../atl/reference/aggregation-and-class-factory-macros.md)

