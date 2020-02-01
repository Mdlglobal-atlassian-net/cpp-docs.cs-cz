---
title: Chyba kompilátoru C3392
ms.date: 11/04/2016
f1_keywords:
- C3392
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
ms.openlocfilehash: 4109a59f093740c9e0865cef6a31f3b09127c747
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912810"
---
# <a name="compiler-error-c3392"></a>Chyba kompilátoru C3392

' type_arg ': neplatný argument typu pro obecný parametr ' param ' obecného ' generic_type ', musí mít veřejný konstruktor bez parametrů

Došlo k chybnému vytvoření instance obecného typu. Ověřte definici typu. Další informace najdete v tématu [Obecné typy](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka používá C# k vytvoření komponenty, která obsahuje obecný typ, který má určitá omezení, která nejsou podporována při vytváření obecných typů v C++/CLI. Další informace najdete v tématu [omezení parametrů typu](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```csharp
// C3392.cs
// Compile by using: csc /target:library C3392.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Když je k dispozici komponenta C3392. dll, následující ukázka vygeneruje C3392.

```cpp
// C3392_b.cpp
// Compile by using: cl /clr C3392_b.cpp
#using <C3392.dll>

ref class R { R(int) {} };
ref class N { N() {} };

value class V {};

ref class N2 { public: N2() {} };
ref class R2 { public: R2() {} };

int main () {
   GR<R^, V, N^>^ gr1;   // C3392
   GR<R^, V, N2^>^ gr1a; // OK

   GR<R^, N^, N^>^ gr3;  // C3392
   GR<R^, V, N2^>^ gr3a; // OK

   GR<R^, V, R^>^ gr4;   // C3392
   GR<R^, V, R2^>^ gr4a; // OK
}
```