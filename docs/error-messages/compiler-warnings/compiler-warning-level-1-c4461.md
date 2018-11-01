---
title: Kompilátor upozornění (úroveň 1) C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 5cc9b08f0f25e9c92b4185f060ab123684c5d9e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591019"
---
# <a name="compiler-warning-level-1-c4461"></a>Kompilátor upozornění (úroveň 1) C4461

'type': Tato třída má finalizační metodu 'finalizační", ale žádný destruktor"dtor.

Přítomnost finalizační metoda v typu znamená prostředky odstranit. Pokud z tohoto typu destruktor je explicitně zavolán finalizační metodu, modul common language runtime určuje, kdy se má spustit finalizační metodu, jakmile váš objekt dostane mimo rozsah.

Pokud jste definovat destruktor v typu a explicitně volat finalizační metodu z destruktoru, můžete spustit nedeterministicky vaše finalizační metodu.

Další informace najdete v tématu [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Příklad

Následující ukázka generuje C4461.

```
// C4461.cpp
// compile with: /W1 /clr /c
ref class A {
protected:
   !A() {}   // C4461
};

// OK
ref struct B {
   ~B() {
      B::!B();
   }

   !B() {}
};
```