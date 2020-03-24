---
title: Upozornění kompilátoru (úroveň 1) C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 819c433a58c6b0c3a3958b483dc1d1a08bde58c1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186748"
---
# <a name="compiler-warning-level-1-c4461"></a>Upozornění kompilátoru (úroveň 1) C4461

' type ': Tato třída má finalizační metodu ' finalizační metodu ', ale nemá žádný destruktor ' dtor '

Přítomnost finalizační metody v typu implikuje prostředky, které se mají odstranit. Pokud není finalizační metoda explicitně volána z destruktoru typu, určí modul CLR (Common Language Runtime), kdy má být spuštěn finalizační metoda, poté, co se objekt dostane mimo rozsah.

Definujete-li v typu destruktor a explicitně voláte finalizační metodu z destruktoru, můžete provést deterministické spuštění finalizační metody.

Další informace naleznete v tématu [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Příklad

Následující ukázka generuje C4461.

```cpp
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
