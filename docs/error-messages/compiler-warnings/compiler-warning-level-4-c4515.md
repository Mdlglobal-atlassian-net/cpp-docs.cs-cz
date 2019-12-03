---
title: Upozornění kompilátoru (úroveň 4) C4515
ms.date: 11/04/2016
f1_keywords:
- C4515
helpviewer_keywords:
- C4515
ms.assetid: 167b5177-3f89-418b-b6c8-7de634f6b28f
ms.openlocfilehash: c3df2b4846dfbdd8c1288ae94153ee93aafb2fd0
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682917"
---
# <a name="compiler-warning-level-4-c4515"></a>Upozornění kompilátoru (úroveň 4) C4515

' namespace ': obor názvů používá sám sebe

Obor názvů se používá rekurzivně.

Následující ukázka generuje C4515:

```cpp
// C4515.cpp
// compile with: /W4
namespace A
{
   using namespace A; // C4515
}

int main()
{
}
```