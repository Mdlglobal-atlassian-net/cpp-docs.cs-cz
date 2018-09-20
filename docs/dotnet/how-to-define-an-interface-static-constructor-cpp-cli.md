---
title: 'Postupy: definice statického konstruktoru (C + +/ CLI) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e2da339259efd77ea7992e63e6137a15017fdc31
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402834"
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>Postupy: Definice a používání statického konstruktoru (C++/CLI)

Rozhraní může mít statický konstruktor, který slouží k inicializaci statické datové členy.  Statický konstruktor zavolá se maximálně jednou a bude volána před prvním členem statických rozhraní přistupuje.

## <a name="example"></a>Příklad

```
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

## <a name="see-also"></a>Viz také

[Třída rozhraní](../windows/interface-class-cpp-component-extensions.md)