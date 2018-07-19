---
title: Příkaz Return v ukončení programu (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: eb594eb10e8068d5f5b3ed124d5e77b48ced728e
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947488"
---
# <a name="return-statement-in-program-termination-c"></a>Výraz return v ukončení programu (C++)
Vydání `return` příkaz z **hlavní** je funkčně ekvivalentní volání **ukončit** funkce. Vezměte v úvahu v následujícím příkladu:  
  
```cpp 
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 **Ukončit** a **vrátit** příkazů v předchozím příkladu funkčně totožné. Jazyk C++ však vyžaduje, aby funkce, které mají jiné návratové typy než **void** vracet hodnotu. **Vrátit** příkaz umožňuje vrátit hodnotu z `main`.  
  
## <a name="see-also"></a>Viz také  
 [Ukončení programu](../cpp/program-termination.md)