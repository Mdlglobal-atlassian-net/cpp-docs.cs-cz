---
title: Chyba kompilátoru C3241
ms.date: 11/04/2016
f1_keywords:
- C3241
helpviewer_keywords:
- C3241
ms.assetid: 2ca14879-bba0-4a23-b22a-72cfff92d6a4
ms.openlocfilehash: 6eab22a8627b817b7a31e4bd34aad86d1f274615
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173496"
---
# <a name="compiler-error-c3241"></a>Chyba kompilátoru C3241

"metoda": tuto metodu nezavádí "rozhraní"

Když explicitně přepsat funkce, podpis funkce musí přesně odpovídat deklarace funkce, která jsou přepisování.

Následující ukázka generuje C3241:

```
// C3241.cpp
#pragma warning(disable:4199)

__interface IX12A {
   void mf();
};

__interface IX12B {
   void mf(int);
};

class CX12 : public IX12A, public IX12B { // C3241
   void IX12A::mf(int);
};
```