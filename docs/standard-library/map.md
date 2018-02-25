---
title: '&lt;Mapa&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <map>
dev_langs:
- C++
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c91e321573782a4173033d586b2211870dc05f33
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltmapgt"></a>&lt;map&gt;
Definuje mapování třídy šablony kontejneru a multimap a jejich podpůrné šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <map>  
  
```  
  
## <a name="members"></a>Členové  
  
### <a name="operators"></a>Operátory  
  
|Verze mapy|Multimap verze|Popis|  
|-----------------|----------------------|-----------------|  
|[Operator! = (map)](../standard-library/map-operators.md#op_neq)|[Operator! = (multimap)](../standard-library/map-operators.md#op_neq)|Testy, pokud není stejný jako mapy nebo multimap objekt na pravé straně mapy nebo multimap objekt na levé straně operátoru.|  
|[Operator < (map)](../standard-library/map-operators.md#op_eq_eq)|[Operator < (multimap)](../standard-library/map-operators.md#op_eq_eq)|Testy, pokud mapy nebo multimap objekt na levé straně operátoru je menší než mapy nebo multimap objekt na pravé straně.|  
|[Operator < = (map)](../standard-library/map-operators.md#op_lt)|[operator\<= (multimap)](../standard-library/map-operators.md#op_lt)|Testy, pokud mapy nebo multimap objekt na levé straně operátoru je menší než nebo rovna hodnotě mapy nebo multimap objekt na pravé straně.|  
|[Operator == (map)](../standard-library/map-operators.md#op_eq_eq)|[operator== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|Testy, pokud je stejný jako mapy nebo multimap objekt na pravé straně mapy nebo multimap objekt na levé straně operátoru.|  
|[Operator > (map)](../standard-library/map-operators.md#op_gt)|[operator> (multimap)](../standard-library/map-operators.md#op_gt_multimap)|Testy, pokud mapy nebo multimap objekt na levé straně operátoru je větší než mapy nebo multimap objekt na pravé straně.|  
|[operator>= (map)](../standard-library/map-operators.md#op_gt_eq)|[operator>= (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|Testy, pokud mapy nebo multimap objekt na levé straně operátoru je větší než nebo stejný jako mapy nebo multimap objekt na pravé straně.|  
  
### <a name="specialized-template-functions"></a>Specializované funkce šablon  
  
|Verze mapy|Multimap verze|Popis|  
|-----------------|----------------------|-----------------|  
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|Elementy dvě mapy nebo multimaps výměny.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[value_compare – třída](../standard-library/value-compare-class-map.md)|Poskytuje objekt funkce, který můžete porovnat elementy mapy srovnáním jejich klíčů určit jejich relativní pořadí v mapě.|  
|[map – třída](../standard-library/map-class.md)|Používá pro ukládání a načítání dat z kolekce, ve kterém do jednotlivých elementů má jedinečný klíč, pomocí kterého automaticky řazení dat.|  
|[multimap – třída](../standard-library/multimap-class.md)|Používá pro ukládání a načítání dat z kolekce, ve kterém do jednotlivých elementů má klíč, pomocí kterého je automaticky seřadí data a klíčů není nutné mít jedinečné hodnoty.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



