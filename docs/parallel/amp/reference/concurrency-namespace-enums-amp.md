---
title: Výčty obor názvů souběžnosti (AMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs:
- C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a67b5e77b8ab8c52e55dea96e64a3f16a4d70e39
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="concurrency-namespace-enums-amp"></a>Výčty obor názvů souběžnosti (AMP)
|||  
|-|-|  
|[access_type – výčet](#access_type)|[queuing_mode – výčet](#queuing_mode)|  
  
##  <a name="access_type"></a>  access_type – výčet  
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

  
##  <a name="queuing_mode"></a>  queuing_mode – výčet  
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
