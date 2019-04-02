---
title: Chyba kompilátoru C3653
ms.date: 11/04/2016
f1_keywords:
- C3653
helpviewer_keywords:
- C3653
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
ms.openlocfilehash: 75e2c061190b24019491db7a625ecafb5ac82b6b
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776645"
---
# <a name="compiler-error-c3653"></a>Chyba kompilátoru C3653

'function': nelze použít jako pojmenované přepsání: přepisovaná funkce se nebyl nalezen; Nezapomněli jste funkci pojmenovat explicitně, použití:: operator?

Explicitní přepsání zadaná funkce, která nebyla nalezena v libovolném rozhraní. Další informace najdete v tématu [explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).

Následující ukázka generuje C3653:

```
// C3653.cpp
// compile with: /clr
public interface struct I {
   void h();
};

public ref struct X : public I {
   virtual void f() new sealed = J {};   // C3653 no J in scope
   virtual void g() {}   // OK
   virtual void h() new sealed = I::h {};   // OK
};
```