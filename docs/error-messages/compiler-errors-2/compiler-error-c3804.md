---
title: Chyba kompilátoru C3804
ms.date: 11/04/2016
f1_keywords:
- C3804
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
ms.openlocfilehash: c3c00d1d07306a9e8dc67d3f75a5cb25d8f03aee
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59775803"
---
# <a name="compiler-error-c3804"></a>Chyba kompilátoru C3804

'property_accessor': přístupové metody pro vlastnost musí být všechny statické nebo všechny statické

Při definování netriviální vlastnosti přístupové funkce může být buď statická nebo instance, ale ne obojí.

Zobrazit [vlastnost](../../extensions/property-cpp-component-extensions.md) Další informace.

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