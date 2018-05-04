---
title: Příkaz Return v ukončení programu (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61d09c1b3aaea799c227686436486efa48fc7857
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="return-statement-in-program-termination-c"></a>Výraz return v ukončení programu (C++)
Vydání `return` příkaz z **hlavní** je funkčně odpovídá volání **ukončete** funkce. Podívejte se na následující příklad:  
  
```  
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 **Ukončete** a `return` příkazy v předchozím příkladu jsou funkčně identické. Jazyk C++ však vyžaduje, aby hodnotu vrátily funkce, které mají jiné návratové typy než `void`. `return` Příkaz umožňuje vrátit hodnotu z **hlavní**.  
  
## <a name="see-also"></a>Viz také  
 [Ukončení programu](../cpp/program-termination.md)