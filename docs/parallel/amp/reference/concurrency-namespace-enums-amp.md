---
title: "Výčty obor názvů souběžnosti (AMP) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs:
- C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d17378a34698cc80d356983898e0023b76877140
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="concurrency-namespace-enums-amp"></a>Výčty obor názvů souběžnosti (AMP)
|||  
|-|-|  
|[access_type – výčet](#access_type)|[queuing_mode – výčet](#queuing_mode)|  
  
##  <a name="access_type">access_type – výčet</a>  
 Typ výčtu použitý k označení různé typy přístupu k datům.  
  
```  
enum access_type;  
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`access_type_auto`|Automaticky vybrat nejlepší `access_type` pro akcelerátor.|  
|`access_type_none`|Vyhrazené. Přidělení přístupný jenom na akcelerátor a ne na procesor.|  
|`access_type_read`|Sdílet. Přidělení je dostupné na akcelerátor a je čitelná na procesoru.|  
|`access_type_read_write`|Sdílet. Přidělení je dostupné na akcelerátor a zápis na procesoru.|  
|`access_type_write`|Sdílet. Přidělení je dostupné na akcelerátor a parametr readable i writable na procesoru.|  

  
##  <a name="queuing_mode">queuing_mode – výčet</a>  
 Určuje režimů služby Řízení front, které jsou podporovány na akcelerátor.  
  
```  
enum queuing_mode;  
``` 
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`queuing_mode_immediate`|Řízení front režim, který určuje, že všechny příkazy, například [parallel_for_each – funkce (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each), odešlou do odpovídající zařízení akcelerátoru co nejrychleji vracejí volajícímu.|  
|`queuing_mode_automatic`|Řízení front režim, který určuje, že příkazy zařadí do fronty ve frontě příkaz, který odpovídá [accelerator_view](accelerator-view-class.md) objektu. Příkazy se odesílají do zařízení při [accelerator_view::Flush –](accelerator-view-class.md#flush) je volána.|   
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
