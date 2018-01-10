---
title: "Změna výchozí objekt pro vytváření tříd a agregace Model | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bb88a4c7827fcd43c26819a6f546779e35863cc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>Změna výchozí objekt pro vytváření tříd a agregace modelu
ATL používá [CComCoClass](../atl/reference/ccomcoclass-class.md) definovat výchozí třídu objektu pro vytváření a agregaci modelu pro objekt. `CComCoClass`Určuje následující dvě makra:  
  
-   [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory) deklaruje objektu pro vytváření tříd jako [CComClassFactory](../atl/reference/ccomclassfactory-class.md).  
  
-   [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable) deklaruje, že se dají agregovat objektu.  
  
 Buď tato výchozí nastavení můžete přepsat zadáním jiného makra v definici vaší třídy. Chcete-li například použít [CComClassFactory2](../atl/reference/ccomclassfactory2-class.md) místo `CComClassFactory`, zadejte [DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2) makro:  
  
 [!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]  
  
 Jsou dvě makra, které definují objekt pro vytváření tříd [DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) a [DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton).  
  
 ATL používá také `typedef` mechanismus pro implementaci výchozí chování. Například `DECLARE_AGGREGATABLE` používá makro `typedef` k definování typu s názvem **_CreatorClass**, které se pak odkazuje v rámci ATL. Všimněte si, že v odvozené třídě, `typedef` pomocí stejný název jako základní třída `typedef` výsledkem ATL pomocí vaší definice a přepsání výchozího nastavení.  
  
## <a name="see-also"></a>Viz také  
 [Základy ATL COM – objekty](../atl/fundamentals-of-atl-com-objects.md)   
 [Agregační makra a makra objektu pro vytváření tříd](../atl/reference/aggregation-and-class-factory-macros.md)

