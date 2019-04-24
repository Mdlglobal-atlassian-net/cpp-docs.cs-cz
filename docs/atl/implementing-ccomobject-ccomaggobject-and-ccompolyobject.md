---
title: Implementace CComObject, CComAggObject a CComPolyObject
ms.date: 11/04/2016
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
ms.openlocfilehash: e2413c8fb9f5722f0245883c947067387838e57f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261784"
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

## <a name="see-also"></a>Viz také:

[Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Agregační makra a makra objektu pro vytváření tříd](../atl/reference/aggregation-and-class-factory-macros.md)
