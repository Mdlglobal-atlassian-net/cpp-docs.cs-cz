---
title: "&lt;hash_map –&gt; | Microsoft Docs"
ms.custom: 
ms.date: 09/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <hash_map>
- std::<hash_map>
dev_langs: C++
helpviewer_keywords: hash_map header
ms.assetid: 0765708a-a668-42a2-9800-654c857bdcc2
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e69496f3383233c45ba994305342c3340459a287
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="lthashmapgt"></a>&lt;hash_map –&gt;
> [!NOTE]
>  Tuto hlavičku je zastaralé. Alternativou je [ \<unordered_map >](unordered-map.md).  
  
 Definuje hash_map – kontejner šablony třídy a hash_multimap a jejich podpůrné šablony.  
 
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <hash_map>  
  
```  
  
### <a name="operators"></a>Operátory  
  
|Hash_map – verze|Hash_multimap – verze|Popis|  
|-----------------------|----------------------------|-----------------|  
|[Operator! = (hash_map)](hash-map-operators.md#op_neq)|[Operator!=(hash_multimap)](hash-map-operators.md#op_neq_mm)|Testy, pokud hash_map nebo hash_multimap objekt na levé straně operátor není rovno hash_map nebo hash_multimap objekt na pravé straně.|  
|[Operator == (hash_map)](hash-map-operators.md#op_eq_eq)|[operator == (hash_multimap)] ((hodnota hash – mapy operators.md op_eq_eq_mm #)|Testy, pokud hash_map nebo hash_multimap objekt na levé straně operátoru rovná hash_map nebo hash_multimap objekt na pravé straně.|  
  
### <a name="specialized-template-functions"></a>Specializované funkce šablon  
  
|Hash_map – verze|Hash_multimap – verze|Popis|  
|-----------------------|----------------------------|-----------------|  
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Elementy dva hash_maps nebo hash_multimaps výměny.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[hash_compare – třída](hash-compare-class.md)|Popisuje objekt, který můžete použít žádné kontejnery asociativní hash – hash_map, hash_multimap, hash_set, nebo hash_multiset – ve výchozím nastavení **vlastnosti** parametr objekt pořadí a hodnoty hash elementy obsahují.|  
|[value_compare – třída](value-compare-class.md)|Poskytuje objekt funkce, který můžete porovnat elementy hash_map srovnáním jejich klíčů určit jejich relativní pořadí v hash_map.|  
|[hash_map – třída](hash-map-class.md)|Používá pro ukládání a rychlé načítání dat z kolekce, ve kterém je každý prvek pár, který má klíč řazení, jehož hodnota je jedinečný a hodnotu přidružená data.|  
|[hash_multimap – třída](hash-multimap-class.md)|Používá pro ukládání a rychlé načítání dat z kolekce, ve kterém je každý prvek pár, který má klíč řazení, jehož hodnota nemusí být jedinečný a hodnotu přidružená data.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<hash_map >  
  
 **Namespace:** stdext –  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](thread-safety-in-the-cpp-standard-library.md)   
 [Standardní C++ – referenční dokumentace knihoven](cpp-standard-library-reference.md)



