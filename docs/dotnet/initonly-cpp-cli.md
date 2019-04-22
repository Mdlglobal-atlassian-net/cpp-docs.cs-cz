---
title: initonly (C++/CLI)
ms.date: 11/04/2016
f1_keywords:
- initonly_cpp
- initonly
helpviewer_keywords:
- initonly attribute [C++]
ms.assetid: f745d7fa-dc08-46f1-9b97-0977be58a008
ms.openlocfilehash: cdfc278225ce4ab418dfaaf41fb413d088ad77df
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58766571"
---
# <a name="initonly-ccli"></a>initonly (C++/CLI)

**InitOnly** je kontextové klíčové slovo, která určuje přiřazení této proměnné může dojít pouze jako součást deklarace nebo ve statickém konstruktoru ve stejné třídě.

Následující příklad ukazuje, jak používat `initionly`:

```
// mcpp_initonly.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst1;

   initonly
   static int staticConst2 = 0;

   static Y1() {
      staticConst1 = 0;
   }
};
```

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../extensions/classes-and-structs-cpp-component-extensions.md)
