---
title: Při Statement (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- while
dev_langs:
- C++
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e6814df9d81674e37f4364330e7801399cb4c763
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="while-statement-c"></a>while – příkaz (C)
`while` Příkaz umožňuje opakujte příkaz, dokud zadaného výrazu se změní na hodnotu false.  
  
## <a name="syntax"></a>Syntaxe  
 *příkaz iterace*:  
 **Při (***výraz***)***– příkaz*   
  
 *Výraz* musí mít typ aritmetické nebo ukazatel. Provádění pokračuje následujícím způsobem:  
  
1.  *Výraz* vyhodnotí.  
  
2.  Pokud *výraz* je zpočátku false text `while` nikdy spustit příkaz, a předá řízení z `while` příkaz, který má další příkaz v programu.  
  
     Pokud *výraz* je true (nenulové hodnoty), provede se tělo příkazu a tento proces se opakuje od kroku 1.  
  
 `while` Příkaz můžete také při ukončení **zalomení**, `goto`, nebo `return` v rámci příkaz provede se tělo. Použití **pokračovat** příkaz Ukončit iterace bez ukončení `while` smyčky. **Pokračovat** příkaz předá řízení do další iterace `while` příkaz.  
  
 Zde je příklad příkazu `while`:  
  
```  
while ( i >= 0 )   
{  
    string1[i] = string2[i];  
    i--;  
}  
```  
  
 Tento příklad zkopíruje znaky z `string2` k `string1`. Pokud `i` je větší než nebo rovno 0, `string2[i]` je přiřazena k `string1[i]` a `i` se odečte. Když `i` dosáhne nebo klesne pod 0, provádění `while` ukončuje příkaz.  
  
## <a name="see-also"></a>Viz také  
 [while – příkaz (C++)](../cpp/while-statement-cpp.md)