---
title: "duration_values – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
dev_langs: C++
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a0f06646975d694ab76477a64642c03c20769c54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="durationvalues-structure"></a>duration_values – struktura
Poskytuje konkrétní hodnoty [doba trvání](../standard-library/duration-class.md) parametr šablony `Rep`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Rep>  
struct duration_values;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[maximální počet](#max)|Statické. Určuje horní limit pro hodnotu typu `Rep`.|  
|[min.](#min)|Statické. Určuje dolní limit pro hodnotu typu `Rep`.|  
|[nula.](#zero)|Statické. Vrátí `Rep(0)`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<typu chrono >  
  
 **Namespace:** std::chrono  
  
##  <a name="max"></a>duration_values::max –  
 Statickou metodu, která vrací horní mez pro hodnoty typu `Ref`.  
  
```  
static constexpr Rep max();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V důsledku toho vrátí `numeric_limits<Rep>::max()`.  
  
### <a name="remarks"></a>Poznámky  
 Když `Rep` je uživatelsky definovaný typ. Návratová hodnota musí být větší než [duration_values::Zero –](#zero).  
  
##  <a name="min"></a>duration_values::min –  
 Statickou metodu, která vrací dolní mez pro hodnoty typu `Ref`.  
  
```  
static constexpr Rep min();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V důsledku toho vrátí `numeric_limits<Rep>::lowest()`.  
  
### <a name="remarks"></a>Poznámky  
 Když `Rep` je uživatelsky definovaný typ. Návratová hodnota musí být menší než nebo rovno [duration_values::Zero –](#zero).  
  
##  <a name="zero"></a>duration_values::Zero –  
 Vrátí `Rep(0)`.  
  
```  
static constexpr Rep zero();
```  
  
### <a name="remarks"></a>Poznámky  
 Když `Rep` je uživatelsky definovaný typ. Návratová hodnota musí představovat sčítání nekonečna.  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<typu chrono >](../standard-library/chrono.md)

