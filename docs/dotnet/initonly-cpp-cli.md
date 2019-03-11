---
title: initonly (C++/CLI)
ms.date: 11/04/2016
f1_keywords:
- initonly_cpp
- initonly
helpviewer_keywords:
- initonly attribute [C++]
ms.assetid: f745d7fa-dc08-46f1-9b97-0977be58a008
ms.openlocfilehash: 91b1447231cbc189a701517e48890fea34c2858a
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742896"
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

[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)
