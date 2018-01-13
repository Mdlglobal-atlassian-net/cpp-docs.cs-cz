---
title: BOOL (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
dev_langs: C++
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 564d2f4849d1725d46d92562e2ce75b2ea2e2d44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bool-c"></a>bool (C++)
Toto klíčové slovo je vestavěný typ. Proměnné tohoto typu může mít hodnoty [true](../cpp/true-cpp.md) a [false](../cpp/false-cpp.md). Podmíněné výrazy mít typ `bool` , proto se hodnoty typu `bool`. Například `i!=0` má nyní **true** nebo **false** v závislosti na hodnotě `i`.  

**Visual Studio 2017 verze 15.3 a novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): operand operátory nebo předpona přírůstek nebo snížení operátor nesmí být typu `bool`. 
  
 Hodnoty **true** a **false** mají následující relace:  
  
```  
!false == true  
!true == false  
```  
  
 V následujícím příkazu:  
  
```  
if (condexpr1) statement1;   
```  
  
 Pokud `condexpr1` je **true**, `statement1` je vždy provedeny; pokud `condexpr1` je **false**, `statement1` se nikdy spustí.  
  
 Při operátory nebo předponu `++` operátor se použije pro proměnné typu `bool`, proměnná je nastavená na **true**. 
**Visual Studio 2017 verze 15.3 a novější**: operator ++ pro bool byla odebrána z jazyka a již není podporována.

Operátory nebo předpona `--` proměnné tohoto typu nelze použít operátor.  
  
 `bool` Typ účastní zvýšení úrovně celého čísla. R-value typu `bool` lze převést na r-value typu `int`, s **false** stal nula a **true** stal jeden. Jako typu distinct `bool` účastní rozlišení přetížení.  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Základní typy](../cpp/fundamental-types-cpp.md)