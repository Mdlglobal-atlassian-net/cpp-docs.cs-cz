---
title: Chyba kompilátoru C3391
ms.date: 11/04/2016
f1_keywords:
- C3391
helpviewer_keywords:
- C3391
ms.assetid: c32532b9-7db4-4ccd-84b9-479e5a1a19d1
ms.openlocfilehash: 32ba1ca63a3a6fafa3290946a976e6845385126f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328689"
---
# <a name="compiler-error-c3391"></a>Chyba kompilátoru C3391

'type_arg': Neplatný argument typu pro obecný parametr 'param' z obecného "generic_type", musí být typu hodnotu Null

Byla nesprávně vytvořena instance obecného typu. Zkontrolujte definici typu. Další informace najdete v tématu <xref:System.Nullable> a [obecných typů](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázkový používá C# vytvořit komponentu, která obsahuje obecný typ, který má určitá omezení, které nejsou podporovány při vytváření obecné typy v C++vyhodnocovací. Další informace najdete v tématu [omezení parametrů typů](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

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