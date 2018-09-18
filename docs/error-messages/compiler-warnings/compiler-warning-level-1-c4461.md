---
title: Upozornění (úroveň 1) C4461 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4461
dev_langs:
- C++
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86c12208c6992b97f30bc36ea821ba26148ff751
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081392"
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