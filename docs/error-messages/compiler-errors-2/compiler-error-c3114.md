---
title: Chyba kompilátoru C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: 6f548c72a0e95c533ed711fe9f2583a7abd6c500
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760758"
---
# <a name="compiler-error-c3114"></a>Chyba kompilátoru C3114

Argument: nejedná se o platný pojmenovaný argument atributu.

Aby byl datový člen třídy atributu platný pojmenovaný argument, nesmí být označen jako `static`, `const`nebo `literal`. Pokud vlastnost nesmí být `static` a musí mít přístupové objekty get a set.

Další informace najdete v tématu [vlastnosti](../../extensions/property-cpp-component-extensions.md) a [uživatelsky definované atributy](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3114.

```cpp
// C3114.cpp
// compile with: /clr /c
public ref class A : System::Attribute {
public:
   static property int StaticProp {
      int get();
   }

   property int Prop2 {
      int get();
      void set(int i);
   }
};

[A(StaticProp=123)]   // C3114
public ref class R {};

[A(Prop2=123)]   // OK
public ref class S {};
```
