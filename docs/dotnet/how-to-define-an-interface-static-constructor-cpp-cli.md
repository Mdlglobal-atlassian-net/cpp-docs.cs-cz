---
title: 'Postupy: Definice a používání statického konstruktoru (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
ms.openlocfilehash: 562605a579ac372e4a69953853a6e32668357565
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988238"
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>Postupy: Definice a používání statického konstruktoru (C++/CLI)

Rozhraní může mít statický konstruktor, který lze použít k inicializaci statických datových členů.  Statický konstruktor se bude volat maximálně jednou a bude volán před prvním tím, než se člen statického rozhraní přistupuje.

## <a name="example"></a>Příklad

```cpp
// mcppv2_interface_class2.cpp
// compile with: /clr
using namespace System;

interface struct MyInterface {
   static int i;
   static void Test() {
      Console::WriteLine(i);
   }

   static MyInterface() {
      Console::WriteLine("in MyInterface static constructor");
      i = 99;
   }
};

ref class MyClass : public MyInterface {};

int main() {
   MyInterface::Test();
   MyClass::MyInterface::Test();

   MyInterface ^ mi = gcnew MyClass;
   mi->Test();
}
```

```Output
in MyInterface static constructor
99
99
99
```

## <a name="see-also"></a>Viz také:

[interface class](../extensions/interface-class-cpp-component-extensions.md)
