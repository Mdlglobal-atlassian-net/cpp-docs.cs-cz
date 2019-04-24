---
title: Chyba kompilátoru C3253
ms.date: 11/04/2016
f1_keywords:
- C3253
helpviewer_keywords:
- C3253
ms.assetid: da40be26-0f78-4730-8727-ad11cddf8869
ms.openlocfilehash: 5d161dfab8dff48a1ddd5a8a5036c0bb4d5549aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173246"
---
# <a name="compiler-error-c3253"></a>Chyba kompilátoru C3253

'function': Chyba s explicitním přepsáním

Explicitní přepsání byl nesprávně zadán. Například nelze zadat implementaci pro přepsání, která je také zadat jako čistě. Další informace najdete v tématu [explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).

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