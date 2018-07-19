---
title: Implementace CComObject, CComAggObject a CComPolyObject | Dokumentace Microsoftu
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
ms.openlocfilehash: c3b1f8a0cf466e5364907dd87eefe8bbdc0a003d
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848360"
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>Implementace CComObject, CComAggObject a CComPolyObject
Třídy šablon [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), a [CComPolyObject](../atl/reference/ccompolyobject-class.md) jsou vždy nejvíce odvozené třídy v řetězu dědičnosti. Zodpovídá za jejich zpracování všechny metody v `IUnknown`: `QueryInterface`, `AddRef`, a `Release`. Kromě toho `CComAggObject` a `CComPolyObject` (při použití pro agregované objekty) zadat speciální počítání a `QueryInterface` sémantiku vyžadované pro vnitřní neznámý.  
  
 Zda `CComObject`, `CComAggObject`, nebo `CComPolyObject` se použije, závisí na tom, jestli deklarace jednoho (nebo žádný) následující makra:  
  
|– Makro|Efekt|  
|-----------|------------|  
|DECLARE_NOT_AGGREGATABLE|Vždy používá `CComObject`.|  
|DECLARE_AGGREGATABLE|Používá `CComAggObject` Pokud objekt je agregován a `CComObject` nesplnění. `CComCoClass` obsahuje toto makro, pokud žádná z DECLARE_ * _AGGREGATABLE makra jsou deklarovány ve třídě, bude výchozí.|  
|DECLARE_ONLY_AGGREGATABLE|Vždy používá `CComAggObject`. Vrátí chybu, pokud není agregovaný objekt.|  
|DECLARE_POLY_AGGREGATABLE|Vytvoří instanci objektu ATL **CComPolyObject\<CYourClass >** při `IClassFactory::CreateInstance` je volána. Při vytváření se kontroluje hodnota vnější neznámá. Pokud má hodnotu NULL, `IUnknown` je implementován pro neagregovaná objektu. Pokud není NULL, vnější Neznámá `IUnknown` je implementován pro agregovaného objektu.|  
  
 Výhodou použití `CComAggObject` a `CComObject` je, že implementace `IUnknown` je optimalizovaná pro typ vytvářený objekt. Například objekt neagregovaná pouze musí počet odkazů, zatímco agregovaného objektu musí počet odkazů pro neznámé vnitřní a vnější Neznámá ukazatel.  
  
 Výhodou použití `CComPolyObject` je, že se vyhnete nutnosti obě `CComAggObject` a `CComObject` v modulu pro zpracování agregované a neagregovaná případech. Jediný `CComPolyObject` objekt zpracovává obou případech. To znamená, že existují jenom jednu kopii tabulku vtable a jedna kopie funkce v modulu. Pokud je vaše vtable velký, to může výrazně zkrátit velikost vašeho modulu. Nicméně pokud je vaše vtable malá, pomocí `CComPolyObject` může vést o něco větší velikost modulu, protože není optimalizován pro objekt agregována nebo neagregovaná jsou `CComAggObject` a `CComObject`.  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)   
 [Agregační makra a makra objektu pro vytváření tříd](../atl/reference/aggregation-and-class-factory-macros.md)

