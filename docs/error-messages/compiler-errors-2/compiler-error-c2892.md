---
title: Chyba kompilátoru C2892
ms.date: 11/04/2016
f1_keywords:
- C2892
helpviewer_keywords:
- C2892
ms.assetid: c22a5084-2f50-42c2-a56b-6dfe5442edc9
ms.openlocfilehash: f3868a44cf04d6c87092759ea473aa78aa0ad4c4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760886"
---
# <a name="compiler-error-c2892"></a>Chyba kompilátoru C2892

lokální třída nesmí mít členské šablony.

Členské funkce šablon nejsou platné ve třídě, která je definována ve funkci.

Následující ukázka generuje C2892:

```cpp
// C2892.cpp
int main() {
   struct local {
      template<class T>   // C2892
      void f() {}
   };
}
```
