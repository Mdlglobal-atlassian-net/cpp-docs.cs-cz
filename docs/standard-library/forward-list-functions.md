---
title: "&lt;forward_list –&gt; funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 6696f42d2ba7cb6daabb8f2ff38093911838c1ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list –&gt; funkce
||  
|-|  
|[swap](#swap)|  
  
##  <a name="swap"></a>swap  
 Výměny elementy dva seznamy předat dál.  
  
```
void swap(
    forward_list <Type, Allocator>& left,
    forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`left`|Objekt typu `forward_list`.|  
|`right`|Objekt typu `forward_list`.|  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce šablony provede `left.swap(right)`.  
  
## <a name="see-also"></a>Viz také  
 [< forward_list – >](../standard-library/forward-list.md)



