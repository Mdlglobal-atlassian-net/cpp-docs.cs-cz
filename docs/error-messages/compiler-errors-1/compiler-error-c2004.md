---
title: Chyba kompilátoru c2004
ms.date: 11/04/2016
f1_keywords:
- C2004
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
ms.openlocfilehash: b781e9f81342f35d66eca222bd338252b739096c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737488"
---
# <a name="compiler-error-c2004"></a>Chyba kompilátoru c2004

očekávalo se: defined (ID).

Identifikátor musí být uveden v závorkách následujících po klíčovém slovu preprocesoru.

Tato chyba se může vygenerovat taky v důsledku práce s shodami s kompilátorem, která se dokončila pro Visual Studio .NET 2003: v direktivě preprocesoru chybí závorky. Pokud v direktivě preprocesoru chybí pravá závorka, vyvolá kompilátor chybu.

## <a name="example"></a>Příklad

Následující ukázka generuje c2004:

```cpp
// C2004.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG   // C2004
        printf_s("DEBUG defined\n");
    #endif
}
```

## <a name="example"></a>Příklad

Možné řešení:

```cpp
// C2004b.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG)
        printf_s("DEBUG defined\n");
    #endif
}
```
