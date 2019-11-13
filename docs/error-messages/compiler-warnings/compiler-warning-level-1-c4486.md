---
title: Upozornění kompilátoru (úroveň 1) C4486
ms.date: 11/04/2016
f1_keywords:
- C4486
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
ms.openlocfilehash: 4c92c23af4aeb6a18c812517cfef9fa00d15dfcb
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965396"
---
# <a name="compiler-warning-level-1-c4486"></a>Upozornění kompilátoru (úroveň 1) C4486

' function ': soukromá virtuální metoda třídy ref class nebo value class by měla být označena jako Sealed

Vzhledem k tomu, že privátní virtuální členská funkce spravované třídy nebo struktury není dostupná nebo přepsaná, měla by být označená jako [zapečetěná](../../extensions/sealed-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4486.

```cpp
// C4486.cpp
// compile with: /clr /c /W1
ref class B {
private:
   virtual void f() {}   // C4486
   virtual void f1() sealed {}   // OK
};
```

## <a name="example"></a>Příklad

Následující příklad ukazuje jedno možné použití soukromé zapečetěné virtuální funkce.

```cpp
// C4486_b.cpp
// compile with: /clr /c
ref class B {};

ref class D : B {};

interface class I {
   B^ mf();
};

ref class E : I {
private:
   virtual B^ g() sealed = I::mf {
      return gcnew B;
   }

public:
   virtual D^ mf() {
      return gcnew D;
   }
};
```