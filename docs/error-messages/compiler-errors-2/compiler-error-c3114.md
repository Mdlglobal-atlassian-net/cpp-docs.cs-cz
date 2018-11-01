---
title: Chyba kompilátoru C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: 6ce5b9860cd75619f26a3585981af5807c33535a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50606671"
---
# <a name="compiler-error-c3114"></a>Chyba kompilátoru C3114

"argument": nejde o platný pojmenovaný argument atributu

Aby datový člen třídy atributu platný pojmenovaný argument, nesmí být označené `static`, `const`, nebo `literal`. Pokud vlastnost nesmí být vlastnost `static` a musí mít get a přístupové objekty set.

Další informace najdete v tématu [vlastnost](../../windows/property-cpp-component-extensions.md) a [uživatelem definované atributy](../../windows/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3114.

```
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