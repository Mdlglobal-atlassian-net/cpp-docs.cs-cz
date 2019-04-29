---
title: Chyba kompilátoru C3767
ms.date: 11/04/2016
f1_keywords:
- C3767
helpviewer_keywords:
- C3767
ms.assetid: 5247cdcd-639c-4527-bd37-37e74c4e8fab
ms.openlocfilehash: 61f7479986cccfa3851d85bf8e7bc0e9da3d1cea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400198"
---
# <a name="compiler-error-c3767"></a>Chyba kompilátoru C3767

kandidátská funkce 'funkce' není k dispozici

Se spřátelenou funkcí definovanou ve třídě by nemělo být zacházeno, jako kdyby byla definována a deklarována v rozsahu globálního oboru názvů. Lze ji však vyhledat pomocí vyhledávání závislého na argumentu.

C3767 může být také způsobeno narušující změně: nativní typy jsou nyní ve výchozím nastavení v privátní **/CLR** tématu [zadejte viditelnost](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C3767:

```
// C3767a.cpp
// compile with: /clr
using namespace System;
public delegate void TestDel();

public ref class MyClass {
public:
   static event TestDel^ MyClass_Event;
};

public ref class MyClass2 : public MyClass {
public:
   void Test() {
      MyClass^ patient = gcnew MyClass;
      patient->MyClass_Event();
    }
};

int main() {
   MyClass^ x = gcnew MyClass;
   x->MyClass_Event();   // C3767

   // OK
   MyClass2^ y = gcnew MyClass2();
   y->Test();
};
```

Následující ukázka generuje C3767:

```
// C3767c.cpp
// compile with: /clr /c

ref class Base  {
protected:
   void Method() {
      System::Console::WriteLine("protected");
   }
};

ref class Der : public Base {
   void Method() {
      ((Base^)this)->Method();   // C3767
      // try the following line instead
      // Base::Method();
   }
};
```

