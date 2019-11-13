---
title: Upozornění kompilátoru (úroveň 1) C4602
ms.date: 11/04/2016
f1_keywords:
- C4602
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
ms.openlocfilehash: 7cacadea560dc5a68d396ac607deb3a5a3c236ee
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965905"
---
# <a name="compiler-warning-level-1-c4602"></a>Upozornění kompilátoru (úroveň 1) C4602

\#direktivy pragma pop_macro: ' název makra ' neexistuje předchozí #pragma push_macro pro tento identifikátor.

Použijete-li [pop_macro](../../preprocessor/pop-macro.md) pro konkrétní makro, je třeba nejprve předat název tohoto makra [push_macro](../../preprocessor/push-macro.md). Například následující ukázka generuje C4602:

```cpp
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```