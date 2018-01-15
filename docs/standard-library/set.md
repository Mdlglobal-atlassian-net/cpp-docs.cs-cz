---
title: '&lt;nastavit&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <set>
dev_langs: C++
helpviewer_keywords: set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 16338888d64155ddeab188159030ac060ebb2b17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ltsetgt"></a>&lt;set&gt;
Definuje sadu kontejneru šablony třídy a multiset a jejich podpůrné šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <set>  
  
```  
  
## <a name="members"></a>Členové  
  
### <a name="operators"></a>Operátory  
  
|Nastavit verzi|Multiset verze|Popis|  
|-----------------|----------------------|-----------------|  
|[Operator! = (set)](../standard-library/set-operators.md#op_neq)|[Operator! = (multiset)](../standard-library/set-operators.md#op_neq)|Testy, pokud set / multiset objekt na levé straně operátor není rovno set / multiset objekt na pravé straně.|  
|[Operator < (set)](../standard-library/set-operators.md#op_lt)|[Operator < (multiset)](../standard-library/set-operators.md#op_lt_multiset)|Testy, pokud set / multiset objekt na levé straně operátor je menší než set / multiset objekt na pravé straně.|  
|[Operator < = (set)](../standard-library/set-operators.md#op_lt_eq)|[operátor\<= (multiset)](../standard-library/set-operators.md#op_lt_eq_multiset)|Testy, pokud set / multiset objekt na levé straně operátor je menší než nebo rovna hodnotě set / multiset objekt na pravé straně.|  
|[Operator == (set)](../standard-library/set-operators.md#op_eq_eq)|[Operator == (multiset)](../standard-library/set-operators.md#op_eq_eq_multiset)|Testy, pokud set / multiset objekt na levé straně operátoru rovná set / multiset objekt na pravé straně.|  
|[Operator > (set)](../standard-library/set-operators.md#op_gt)|[Operator > (multiset)](../standard-library/set-operators.md#op_gt_multiset)|Testy, pokud set / multiset objekt na levé straně operátoru je větší než set / multiset objekt na pravé straně.|  
|[Operator > = (set)](../standard-library/set-operators.md#op_gt_eq)|[Operator > = (multiset)](../standard-library/set-operators.md#op_gt_eq_multiset)|Testy, pokud je sada nebo multiset objekt na levé straně operátor větší než nebo rovna hodnotě set / multiset objekt na pravé straně.|  
  
### <a name="specialized-template-functions"></a>Specializované funkce šablon  
  
|Nastavit verzi|Multiset verze|Popis|  
|-----------------|----------------------|-----------------|  
|[swap](../standard-library/set-functions.md#swap)|[swap (multiset)](../standard-library/set-functions.md#swap_multiset)|Elementy dvě sady nebo multisets výměny.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[set – třída](../standard-library/set-class.md)|Používá pro ukládání a načítání dat z kolekce, ve kterém jsou jedinečné hodnoty elementů obsažených a sloužit jako klíčové hodnoty, podle které data automaticky řazení.|  
|[multiset – třída](../standard-library/multiset-class.md)|Používá pro ukládání a načítání dat z kolekce, v kterém hodnoty elementů obsažených nemusí být jedinečný a které budou sloužit jako klíčové hodnoty, podle které data automaticky řazení.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)



