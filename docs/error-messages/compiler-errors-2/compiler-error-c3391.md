---
title: Chyba kompilátoru C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: cac397e4588c493fb8c47932feb97a5f12cf2583
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578214"
---
# <a name="compiler-error-c3391"></a>Chyba kompilátoru C3391

'type_arg': Neplatný argument typu pro obecný parametr 'param' z obecného "generic_type", musí být typu hodnotu Null

Byla nesprávně vytvořena instance obecného typu. Zkontrolujte definici typu. Další informace najdete v tématu <xref:System.Nullable> a [obecných typů](../../windows/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující příklad používá C# k vytvoření komponenty, která obsahuje obecný typ, který má určitá omezení, které nejsou podporovány při vytváření obecné typy v jazyce C + +/ CLI. Další informace najdete v tématu [omezení parametrů typů](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```cs
// C3391.cs
// Compile by using: csc /target:library C3391.cs
// a C# program
public class GR<N>
where N : struct {}
```

Pokud komponentu C3391.dll je k dispozici, následující ukázka generuje C3391.

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