---
title: Chyba kompilátoru C2535
ms.date: 11/04/2016
f1_keywords:
- C2535
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
ms.openlocfilehash: f5cecd847837214f6392bead624e5377cef4833f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758642"
---
# <a name="compiler-error-c2535"></a>Chyba kompilátoru C2535

'identifikátor': členská funkce je již definována nebo deklarována

Tato chyba může být způsobena použitím stejného seznamu formálních parametrů ve více než jedné definici nebo deklaraci přetížené funkce.

Pokud získáte C2535 z důvodu funkce Dispose, přečtěte si další informace v tématu [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) .

Následující ukázka generuje C2535:

```cpp
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```
