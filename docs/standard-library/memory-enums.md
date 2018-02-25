---
title: "&lt;paměť&gt; výčty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 78383fb0f2fa2b8456b5c9a1b6df43ad9f6c06f3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltmemorygt-enums"></a>&lt;paměť&gt; výčty
||  
|-|  
|[pointer_safety](#pointer_safety)|  
  
##  <a name="pointer_safety"></a>  pointer_safety – výčet  
 Výčet možných hodnot vrácených `get_pointer_safety`.  
  
pointer_safety – třída {volný, upřednostňované, striktní};  
  
### <a name="remarks"></a>Poznámky  
 Oboru `enum` definuje hodnoty, které mohou být vráceny `get_pointer_safety()`:  
  
 `relaxed` – odvozené neprovádí bezpečné ukazatele (samozřejmě ukazatelé na objekty deklarované nebo přidělené), se považují stejné jako ty bezpečně odvozené.  
  
 `preferred` --jako předtím, ale neměli přímo odkázat ukazatele odvozené neprovádí bezpečné.  
  
 `strict` – odvozené neprovádí bezpečné ukazatele mohou být považovány jinak než ty bezpečně odvozené.  
  
## <a name="see-also"></a>Viz také  
 [\<paměť >](../standard-library/memory.md)



