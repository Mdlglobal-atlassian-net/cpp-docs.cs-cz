---
title: "&lt;paměť&gt; výčty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 52ccd226214da7ddbdca9c480bb2f8940203155e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltmemorygt-enums"></a>&lt;paměť&gt; výčty
||  
|-|  
|[pointer_safety –](#pointer_safety)|  
  
##  <a name="pointer_safety"></a>pointer_safety – výčet  
 Výčet možných hodnot vrácených `get_pointer_safety`.  
  
pointer_safety – třída {volný, upřednostňované, striktní};  
  
### <a name="remarks"></a>Poznámky  
 Oboru `enum` definuje hodnoty, které mohou být vráceny `get_pointer_safety()`:  
  
 `relaxed`– odvozené neprovádí bezpečné ukazatele (samozřejmě ukazatelé na objekty deklarované nebo přidělené), se považují stejné jako ty bezpečně odvozené.  
  
 `preferred`--jako předtím, ale neměli přímo odkázat ukazatele odvozené neprovádí bezpečné.  
  
 `strict`– odvozené neprovádí bezpečné ukazatele mohou být považovány jinak než ty bezpečně odvozené.  
  
## <a name="see-also"></a>Viz také  
 [\<paměť >](../standard-library/memory.md)


