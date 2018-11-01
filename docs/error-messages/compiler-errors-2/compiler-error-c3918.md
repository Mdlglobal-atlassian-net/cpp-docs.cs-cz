---
title: Chyba kompilátoru C3918
ms.date: 11/04/2016
f1_keywords:
- C3918
helpviewer_keywords:
- C3918
ms.assetid: a8b3a90a-3fe1-4244-a5ff-a31cdae97d98
ms.openlocfilehash: 2c2d2f2598d06ca228a96f2786fcb02888e29a1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530894"
---
# <a name="compiler-error-c3918"></a>Chyba kompilátoru C3918

použití vyžaduje 'člen' jako datový člen

C3918 může dojít z několika důvodů související s událostmi.

## <a name="example"></a>Příklad

C3918 situace může nastat, protože člen třídy je nutné v aktuálním kontextu. Následující ukázka generuje C3918.

```
// C3918.cpp
// compile with: /clr /c
public ref class C {
public:
   System::Object ^ o;
   delegate void Del();

   event Del^ MyEvent {
      void add(Del^ev) {
         if ( MyEvent != nullptr) {}   // C3918
         if ( o != nullptr) {}   // OK
   }
   void remove(Del^){}
   }
};
```

## <a name="example"></a>Příklad

C3918 také dojde, pokud se pokusíte zkontrolujte triviální událost pro null (název události nadále poskytovat žádné přímý přístup k úložišti delegáta zálohování pro událost).

Následující ukázka generuje C3918.

```
// C3918_2.cpp
// compile with: /clr /c
using namespace System;
public delegate int MyDel(int);

interface struct IEFace {
   event MyDel ^ E;
};

ref struct EventSource : public IEFace {
   virtual event MyDel ^ E;
   void Fire_E(int i) {
      if (E)   // C3918
         E(i);
   }
};
```

## <a name="example"></a>Příklad

C3918 může také dojít, pokud je nesprávně přihlášení k odběru události. Následující ukázka generuje C3918.

```
// C3918_3.cpp
// compile with: /clr /c
using namespace System;

public delegate void del();

public ref class A {
public:
   event del^ e {
      void add(del ^handler ) {
         d += handler;
      }

      void remove(del ^handler) {
         d -= handler;
      }

      void raise() {
         d();
      }
   }

   del^ d;
   void f() {}

   A() {
      e = gcnew del(this, &A::f);   // C3918
      // try the following line instead
      // e += gcnew del(this, &A::f);
      e();
   }
};

int main() {
   A a;
}
```