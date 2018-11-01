---
title: Chyba kompilátoru C2909
ms.date: 11/04/2016
f1_keywords:
- C2909
helpviewer_keywords:
- C2909
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
ms.openlocfilehash: 7a777e87d8110ac16740346a8494f9501ce93b37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668842"
---
# <a name="compiler-error-c2909"></a>Chyba kompilátoru C2909

'identifier': explicitní vytváření instancí šablony funkcí vyžaduje návratový typ.

Explicitní vytváření instancí šablony funkcí vyžaduje, aby explicitní její typ vrácené hodnoty. Implicitní návratový typ specifikace nefunguje.

Následující ukázka generuje C2909:

```
// C2909.cpp
// compile with: /c
template<class T> int f(T);
template f<int>(int);         // C2909
template int f<int>(int);   // OK
```