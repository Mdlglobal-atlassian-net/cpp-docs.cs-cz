---
title: Výraz return v ukončení programu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], function return types
- function return types [C++], return statement
- return keyword [C++], syntax
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
ms.openlocfilehash: 9c7b6130ee1a0b49ab75a70d84764d3a1f8c5ef0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267609"
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