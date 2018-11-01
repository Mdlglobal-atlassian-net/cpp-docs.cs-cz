---
title: Změna výchozí objekt pro vytváření tříd a agregačního modelu
ms.date: 11/04/2016
helpviewer_keywords:
- CComClassFactory class, making the default
- aggregation [C++], using ATL
- aggregation [C++], aggregation models
- defaults [C++], aggregation model in ATL
- default class factory
- class factories, changing default
- CComCoClass class, default class factory and aggregation model
- default class factory, ATL
- defaults [C++], class factory
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
ms.openlocfilehash: 34e838eea201f96acd7dcc647c4410fb244c8424
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485540"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>Změna výchozí objekt pro vytváření tříd a agregačního modelu

ATL – používá [CComCoClass](../atl/reference/ccomcoclass-class.md) definovat výchozí třídy objektu pro vytváření a agregace model objektu. `CComCoClass` Určuje následující dvě makra:

- [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory) deklaruje objekt pro vytváření tříd bude [ccomclassfactory –](../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable) deklaruje, že objekt se dají agregovat.

Buď tato výchozí nastavení můžete přepsat zadáním jiného makra v definici třídy. Chcete-li například použít [ccomclassfactory2 –](../atl/reference/ccomclassfactory2-class.md) místo `CComClassFactory`, zadejte [DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2) – makro:

[!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]

Jsou dvě makra, které definují objekt pro vytváření tříd [DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) a [DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton).

ATL také používá **typedef** mechanismus pro implementaci výchozí chování. Například používá makro DECLARE_AGGREGATABLE **typedef** definovat typ s názvem `_CreatorClass`, který je pak odkazovat v rámci ATL. Všimněte si, že v odvozené třídě, **– typedef** pomocí stejného názvu jako základní třída **typedef** výsledkem knihovny ATL pomocí vaší definice a přepisuje výchozí chování.

## <a name="see-also"></a>Viz také

[Základy ATL – objekty COM](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Agregační makra a makra objektu pro vytváření tříd](../atl/reference/aggregation-and-class-factory-macros.md)

