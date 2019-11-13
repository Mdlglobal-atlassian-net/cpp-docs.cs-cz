---
title: Upozornění kompilátoru (úroveň 1) C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 195e5532b6555210077e43ad3086ee3106f3e757
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966015"
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