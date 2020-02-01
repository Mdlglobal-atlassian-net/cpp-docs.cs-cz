---
title: Chyba kompilátoru C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: 7590ba9431892c07a32c27fdc97604c8b005fe33
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912860"
---
# <a name="compiler-error-c3391"></a>Chyba kompilátoru C3391

' type_arg ': neplatný argument typu pro obecný parametr ' param ' obecného ' generic_type ' musí být typ hodnoty, která není null.

Došlo k chybnému vytvoření instance obecného typu. Ověřte definici typu. Další informace najdete v tématu <xref:System.Nullable> a [Obecné typy](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka používá C# k vytvoření komponenty, která obsahuje obecný typ, který má určitá omezení, která nejsou podporována při vytváření obecných typů v C++/CLI. Další informace najdete v tématu [omezení parametrů typu](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```csharp
// C3391.cs
// Compile by using: csc /target:library C3391.cs
// a C# program
public class GR<N>
where N : struct {}
```

Když je k dispozici komponenta C3391. dll, následující ukázka vygeneruje C3391.

```cpp
// C3391_b.cpp
// Compile by using: cl /clr C3391_b.cpp
#using <C3391.dll>
using namespace System;
value class VClass {};

int main() {
   GR< Nullable<VClass> >^ a =
      gcnew GR< Nullable<VClass> >();   // C3391 can't be Nullable
   GR<VClass>^ aa = gcnew GR<VClass>(); // OK
}
```