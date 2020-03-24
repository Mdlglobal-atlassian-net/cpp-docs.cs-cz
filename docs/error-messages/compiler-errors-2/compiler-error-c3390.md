---
title: Chyba kompilátoru C3390
ms.date: 11/04/2016
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: 4c0544df55fc71ace697d7e0a53ba303706e1378
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201120"
---
# <a name="compiler-error-c3390"></a>Chyba kompilátoru C3390

' type_arg ': neplatný argument typu pro obecný parametr ' param ' obecného ' generic_type ', musí se jednat o typ odkazu

Došlo k chybnému vytvoření instance obecného typu.  Ověřte definici typu.  Další informace najdete v tématu [Obecné typy](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

První ukázka používá C# k vytvoření komponenty, která obsahuje obecný typ, který má určitá omezení, která nejsou podporována při vytváření obecných typů v C++parametrem/CLR. Další informace najdete v tématu [omezení parametrů typu](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```csharp
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Když je k dispozici komponenta C3390. dll, následující ukázka vygeneruje C3390.

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK
}
```
