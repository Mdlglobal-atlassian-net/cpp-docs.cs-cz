---
title: Chyba kompilátoru C2535
ms.date: 11/04/2016
f1_keywords:
- C2535
helpviewer_keywords:
- C2535
ms.assetid: a958f83e-e2bf-4a59-b44b-d406ec325d7e
ms.openlocfilehash: b2b5452cfe59284d56b019674ffbabbda0dc62d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574019"
---
# <a name="compiler-error-c2535"></a>Chyba kompilátoru C2535

'identifikátor': členská funkce je již definována nebo deklarována

Tato chyba může být způsobena použitím stejného seznamu formálních parametrů ve více než jedné definici nebo deklaraci přetížené funkce.

Pokud jste c2535 zobrazí z důvodu funkce Dispose, přečtěte si téma [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) Další informace.

Následující ukázka generuje C2535:

```
// C2535.cpp
// compile with: /c
class C {
public:
   void func();   // forward declaration
   void func() {}   // C2535
};
```