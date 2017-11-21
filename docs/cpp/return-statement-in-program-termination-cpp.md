---
title: "Příkaz Return v ukončení programu (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb3555ecb80b2f6bc8663325b500ffb2eb317ce3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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