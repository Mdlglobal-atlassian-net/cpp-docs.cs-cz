---
title: Kompilátor upozornění (úroveň 1) C4945
ms.date: 11/04/2016
f1_keywords:
- C4945
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
ms.openlocfilehash: 62dfbaed28f1afcdedb41d83158dfe4e8e0f61b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653853"
---
# <a name="compiler-warning-level-1-c4945"></a>Kompilátor upozornění (úroveň 1) C4945

'symbol': nejde naimportovat symbol z: 'assembly2': jako 'symbol' již byl importován z jiného sestavení "assembly1.

Symbol bylo importováno z odkazovaných sestavení, ale tento symbol již byl importován z jiného odkazovaných sestavení. Buď odkazovat sestavení nebo získat název symbolu změnit v jednom sestavení.

Následující ukázky generovat C4945.

```
// C4945a.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

a pak,

```
// C4945b.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

a pak,

```
// C4945c.cpp
// compile with: /clr /LD /W1
#using "C4945a.dll"
#using "C4945b.dll"   // C4945
```