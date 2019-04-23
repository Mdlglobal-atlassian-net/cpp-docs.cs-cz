---
title: Chyba kompilátoru C3392
ms.date: 11/04/2016
f1_keywords:
- C3392
helpviewer_keywords:
- C3392
ms.assetid: e4757596-e2aa-4314-b01e-5c4bfd2110e9
ms.openlocfilehash: 72bdef1b3344b3d69ba0d014f92a85e9381de4b3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776714"
---
# <a name="compiler-error-c3392"></a>Chyba kompilátoru C3392

'type_arg': Neplatný argument typu pro obecný parametr 'param' z obecného "generic_type", musí mít veřejný konstruktor bez parametrů

Byla nesprávně vytvořena instance obecného typu. Zkontrolujte definici typu. Další informace najdete v tématu [obecných typů](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázkový používá C# vytvořit komponentu, která obsahuje obecný typ, který má určitá omezení, které nejsou podporovány při vytváření obecné typy v C++vyhodnocovací. Další informace najdete v tématu [omezení parametrů typů](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```cs
// C3392.cs
// Compile by using: csc /target:library C3392.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Pokud komponentu C3392.dll je k dispozici, následující ukázka generuje C3392.

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