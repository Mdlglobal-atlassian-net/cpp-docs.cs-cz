---
title: Chyba kompilátoru C3804
ms.date: 11/04/2016
f1_keywords:
- C3804
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
ms.openlocfilehash: e83380696aca3d6d45c235925b830bef9e3061a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544583"
---
# <a name="compiler-error-c3804"></a>Chyba kompilátoru C3804

'property_accessor': přístupové metody pro vlastnost musí být všechny statické nebo všechny statické

Při definování netriviální vlastnosti přístupové funkce může být buď statická nebo instance, ale ne obojí.

Zobrazit [vlastnost](../../windows/property-cpp-component-extensions.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3804.

```
// C3804.cpp
// compile with: /c /clr
ref struct A {

   property int i {
      static int get() {}
      void set(int i) {}
   }   // C3804 error

   // OK
   property int j {
      int get() { return 0; }
      void set(int i) {}
   }

   property int k {
      static int get() { return 0; }
      static void set(int i) {}
   }
};
```