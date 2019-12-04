---
title: Chyba kompilátoru C2506
ms.date: 11/04/2016
f1_keywords:
- C2506
helpviewer_keywords:
- C2506
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
ms.openlocfilehash: 593fbbc6b561e6390624aa79af14dc665a552990
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746835"
---
# <a name="compiler-error-c2506"></a>Chyba kompilátoru C2506

' member ': ' __declspec (modifikátor) ' nelze použít na tento symbol

Pro statické členy spravované třídy nelze deklarovat jednotlivé procesy nebo pro jednu doménu AppDomain.

Další informace naleznete v tématu [AppDomain](../../cpp/appdomain.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C2506.

```cpp
// C2506.cpp
// compile with: /clr /c
ref struct R {
   __declspec(process) static int n;   // C2506
   int o;   // OK
};
```
