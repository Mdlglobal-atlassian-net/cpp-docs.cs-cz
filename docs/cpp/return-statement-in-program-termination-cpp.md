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
ms.openlocfilehash: cfcf65258767178c0f74f63ca6e938e1d940e3be
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061133"
---
# <a name="return-statement-in-program-termination-c"></a>Výraz return v ukončení programu (C++)

Vydání **vrátit** příkaz z `main` je funkčně ekvivalentní volání `exit` funkce. Vezměte v úvahu v následujícím příkladu:

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

`exit` a **vrátit** příkazů v předchozím příkladu funkčně totožné. Jazyk C++ však vyžaduje, aby funkce, které mají jiné návratové typy než **void** vracet hodnotu. **Vrátit** příkaz umožňuje vrátit hodnotu z `main`.

## <a name="see-also"></a>Viz také:

[Ukončení programu](../cpp/program-termination.md)