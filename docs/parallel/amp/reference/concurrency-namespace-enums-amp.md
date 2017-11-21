---
title: "Výčty obor názvů souběžnosti (AMP) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs: C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 809ea614924444b4f753153f821118cee6d29e6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="concurrency-namespace-enums-amp"></a>Výčty obor názvů souběžnosti (AMP)
|||  
|-|-|  
|[access_type – výčet](#access_type)|[queuing_mode – výčet](#queuing_mode)|  
  
##  <a name="access_type"></a>access_type – výčet  
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

  
##  <a name="queuing_mode"></a>queuing_mode – výčet  
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
 [Namespace souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
