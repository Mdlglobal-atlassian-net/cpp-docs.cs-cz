---
title: BOOL (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
dev_langs:
- C++
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 058979420e5bb1426879522e70ec8b1ac768d9cc
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407400"
---
# <a name="bool-c"></a>bool (C++)

Toto klíčové slovo je vestavěný typ. Proměnná tohoto typu může mít hodnoty [true](../cpp/true-cpp.md) a [false](../cpp/false-cpp.md). Podmíněné výrazy jsou typu **bool** a mají proto hodnoty typu **bool**. Například `i!=0` teď má hodnotu TRUE nebo FALSE, v závislosti na hodnotě z `i`.  

**Visual Studio 2017 verze 15.3 nebo novější** (k dispozici [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): operand uplatněna přípona nebo předpona Inkrementace nebo dekrementace operátor nesmí být typu **bool**. Jinými slovy, zadané proměnné `b` typu **bool**, už nejsou povolené tyto výrazy:

```cpp
    b++;
    ++b;
    b--;
    --b;
```
  
Hodnoty TRUE a FALSE mají následující vztah:  
  
```cpp  
!false == true  
!true == false  
```  
  
V následujícím příkazu:  
  
```cpp  
if (condexpr1) statement1;   
```  
  
Pokud `condexpr1` má hodnotu TRUE, `statement1` je vždy spuštěn; pokud `condexpr1` má hodnotu FALSE, `statement1` není nikdy proveden.  
  
Uplatněna přípona nebo předpona **++** operátor je použít pro proměnné typu **bool**, proměnná je nastavena na hodnotu TRUE. 
**Visual Studio 2017 verze 15.3 nebo novější**: operator ++ pro **bool** byl odebrán z jazyka a už není podporovaná.

Přípony nebo předpony **--** operátor nelze použít na proměnné tohoto typu.  
  
 **Bool** typ se účastní integrální propagace. R-value typu **bool** lze převést na hodnotu r-value typu **int**, se stávají FALSE nula a TRUE jedna. Jako odlišný typ se **bool** účastní řešení přetížení.  
  
## <a name="see-also"></a>Viz také:
[Klíčová slova](../cpp/keywords-cpp.md)  
[Základní typy](../cpp/fundamental-types-cpp.md)  