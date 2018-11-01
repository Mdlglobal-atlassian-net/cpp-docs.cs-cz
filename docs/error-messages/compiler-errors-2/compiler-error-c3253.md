---
title: Chyba kompilátoru C3253
ms.date: 11/04/2016
f1_keywords:
- C3253
helpviewer_keywords:
- C3253
ms.assetid: da40be26-0f78-4730-8727-ad11cddf8869
ms.openlocfilehash: 997d23fa5736e31b3824459f928a58eddde56e15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605076"
---
# <a name="compiler-error-c3253"></a>Chyba kompilátoru C3253

'function': Chyba s explicitním přepsáním

Explicitní přepsání byl nesprávně zadán. Například nelze zadat implementaci pro přepsání, která je také zadat jako čistě. Další informace najdete v tématu [explicitní přepsání](../../windows/explicit-overrides-cpp-component-extensions.md).

Následující ukázka generuje C3253:

```
// C3253.cpp
// compile with: /clr
public interface struct I {
   void a();
   void b();
   void c();
};

public ref struct R : I {
   virtual void a() = 0, I::a {}   // C3253
   virtual void b() = I::a {}   // OK
   virtual void c() = 0;   // OK
};
```