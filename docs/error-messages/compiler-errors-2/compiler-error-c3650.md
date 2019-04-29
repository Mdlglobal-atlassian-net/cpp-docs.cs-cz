---
title: Chyba kompilátoru C3650
ms.date: 11/04/2016
f1_keywords:
- C3650
helpviewer_keywords:
- C3650
ms.assetid: ca4d8de4-b027-4d13-9b9f-03ca62905c33
ms.openlocfilehash: 54543225144ed0187f6c1e68e7236d886c026860
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385599"
---
# <a name="compiler-error-c3650"></a>Chyba kompilátoru C3650

'interface_method': nejde používat jako explicitní přepsání; musí být virtuální členská funkce základní třídy.

Došlo pokusu o provést explicitní přepsání člena, která není virtuální.

Další informace najdete v tématu [explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).

Následující ukázka generuje C3650:

```
// C3650.cpp
// compile with: /clr
public interface struct I {
   void a();
};

public ref class S {
public:
   static int f() { return 0; }
   static int g() { return 0; }
};

public ref struct T1 : public S, I {
   virtual int f() new sealed = S::f;   // C3650
   virtual int g() { return 0; }   // OK does not override S::g
   virtual void a() new sealed = I::a {}   // OK
};
```